---
title: "Another b43 internet problem"
date: 2010-09-19
forum: Hardware
---

### Post by pilgrimninja17 on 2010-09-19
So heres how it started. 

I'm running 10.04 on my Dell Inspiron 600m, had my external hd hooked in one night, fell asleep watching a movie, woke up and touch the pad, it wouldn't wake up, i pressed the on button which usually wakes my laptop and nothing happened. so i turned it off, then back on, and then poof, suddenly i dont have a wireless connection, it's not even recognized anymore. i have tried to reinstall the os with no luck. i have tried dl fwcutter, and tried to dl ndiswrapper. but i guess i'm doing something wrong. i've got a broadcom b4306, and it's supported by linux but suddenly it's not recognized. wtf! under system>administration>hardware drivers my card isn't seen or listed.

i can maneuver around unbuntu pretty well, but i guess i dont know how to read what terminal is spitting out correctly. please help my friends!

[http://i56.tinypic.com/211nv2u.jpg](http://i56.tinypic.com/211nv2u.jpg)

---

### Post by apfejes on 2010-09-19
oddly enough, I'm experiencing a very similar problem with my laptop (Vostro 1000) as well.  Left it on, ran out of batteries... and poof, no more wireless networking.

I've now completely reloaded the OS, and still can't get it working again, which has me thinking something else may be the issue.

However, there are some strange symptoms to this problem. 
First, I'm using wl, not b43.
Second, nm-tool shows that the card is working, can scan, and does everything EXCEPT "connect"

Third, when running NetworkManager in the --no-daemon mode, I can see everything working fine, except for the NetworkManager taking over and activating the dhcp process on the wireless card (which is exactly what happens on the b44xx wired card when the carrier signal is detected.)

I think it's simply a matter of NetwortManager not knowing what to do - some thing is set incorrectly.

Unfortunately, I'm still working to fix this.... no idea what to try next.

---

### Post by jcolyn on 2010-09-19
At the terminal type

```
lspci
``` and look for your wireless card. If it's a Broadcom BCM4309 you're out of luck. This is the most common card installed on this model and is not supported. You will get random connects but when it drops the connection it is usually down for days at a time..

---

