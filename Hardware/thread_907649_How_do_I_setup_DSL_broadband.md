---
title: "How do I setup DSL broadband?"
date: 2008-09-01
forum: Hardware
---

### Post by jacatone on 2008-09-01
I'm running Ubuntu 7.10. Haven't a clue how to configure DSL, once the modem is plugged into my computer. It comes with a software CD, but it's for Windows and the provider (Verizon) won't support Linux. Any advice would be appreciated. Thanks.

---

### Post by caljohnsmith on 2008-09-01
All DSL modems that I know of default to using DHCP so that you can just connect your computer to the modem via ethernet, and your computer should be able to obtain a LAN IP address from the modem and communicate with it just fine. That assumes of course that your ethernet card works fine in Ubuntu, which most likely it does. 

So bottom line: hook up your computer to the modem with your ethernet cable, and then if you do the command:
```
ifconfig
```
You should see that your ethernet card's interface, most likely called "eth0", has an "inet addr" which is your local or LAN IP. It will most likely be something like 192.168.0.100 or similar. If you get that far you are most likely successfully connected.

Now If you look on the bottom of your DSL modem, it often tells you what the IP address of the modem is so you can configure it via your web browser. Most modems use 192.168.0.1, but it could be maybe 192.168.1.1 or 192.168.0.254, etc. Once you know that address, just plug it into your web browser:
[http://192.168.0.1](http://192.168.0.1)
And you should be able to see your modem settings. And unless your ISP gives you directions otherwise, you should be able to set your modem to use "PPP on modem", and then type in your ISP's username and password, and you should be good to go. Let me know how it goes or if you need more details/info.

---

