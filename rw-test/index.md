---
title: Hello homelab
date: 2024-09-11 12:00:00
categories: [homelab,hardware]
tages: [servers,proxy]
---

# A wonderful serenity has taken possession of my entire soul
Addressing “400 Bad Request” in Home Assistant and Traefik

![img-description](https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559820489/js-code_n83m7a.jpg)
               

Home Assistant needs to be properly configured to trust Traefik that is passing traffic to it.

In your Home Assistant configuration.yaml, add the following:
````yml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.16.0.0/12   # This should cover Docker internal network range
    - 127.0.0.1       # Loopback for local requests
    - 192.168.1.0/24  # Your local network
````