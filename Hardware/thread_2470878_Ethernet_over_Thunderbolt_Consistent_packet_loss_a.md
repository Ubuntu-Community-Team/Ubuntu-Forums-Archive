---
title: "Ethernet over Thunderbolt: Consistent packet loss after reboot"
date: 2022-01-14
forum: Hardware
---

### Post by cryptochrome242 on 2022-01-14
Hello there,

I am running 20.04 with the HWE kernel on a Tiger Lake Intel NUC 11th gen. I am using Thunderbolt to connect to a NAS - both are doing Ethernet over Thunderbolt. While this generally works very well, I have one annoying little problem: Every time I reboot the machine, that Ethernet connection experiences 10-20% packet loss and high round trip times. This results in all sorts of other issues, like network shares not getting mounted over that network connection. The workaround is to unplug the Thunderbolt cable for a second or two and plug it back in. And low and behold, a couple of seconds later the connection is back up - and stable (no packet loss, everything normal). 

This only happens after a reboot - after every reboot. 

This is what's noteworthy in dmesg:

```

TCP: thunderbolt0: Driver has suspect GRO implementation, TCP performance may be compromised.
```

Since I am fairly inexperienced with Linux and Ubuntu, I wouldn't know what to look for or how to troubleshoot this. Hoping to get some help with this here :)

Thank you

---

