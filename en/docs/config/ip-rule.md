---
hide:
  - toc
---

# IP Rules

smartdns provides IP address whitelist, blacklist and ignore rules for filtering results.

| Parameter | Function | Usage |
| --- | --- | --- |
| whitelist-ip | Whitelist IP address | Accept IP addresses within a specified range |
| blacklist-ip | Blacklist IP address | Accept IP addresses outside a specified range |
| ignore-ip | Ignore IP address | Do not use a specific IP address, or range of IP addresses |
| bogus-nxdomain | Spoof IP address filtering | Return SOA when the requested result contains a specified IP address |
| ip-alias |IP Alias|IP Address Mapping，Can be used for CDN acceleration with Anycast IP, such as Cloudflare's CDN. refer to [IP Alias](../config/ip-alias.md)。

## Whitelist IP addresses

If you want to restrict the IP addresses returned by an upstream server within a whitelist range, and disregard non-whitelisted addresses, you can set the following:

```shell
server -whitelist-ip
whitelist-ip 192.168.1.1/24
```

## Blacklist IP addresses

To restrict the return of IP addresses from a certain upstream and discard IP within a specified range, a blacklist can be set up as follows:

```shell
server -blacklist-ip
blacklist-ip 192.168.1.1/24
```

## Ignore IP addresses

If you want to use a specific IP address returned by an upstream server, you can configure it to be ignored.

```shell
ignore-ip 1.2.3.4
```

## Spoof IP addresses

If the ISP returns a 404 page containing a specific IP address range when the website does not exist, such as China Telecom's custom 404 page, you can use this parameter to return an SOA to the client instead of the ISP's redirect 404 page.

```shell
bogus-nxdomain 1.2.3.4
```