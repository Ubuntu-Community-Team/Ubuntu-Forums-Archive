---
title: "(wireless nd wired) Networking works in Ubuntu 8 Beta but not with 8.04"
date: 2008-06-22
forum: Hardware
---

### Post by reddox on 2008-06-22
Okay this is why I left Linux.

My friend gave me a beta version of Ubuntu 8.01 i think..

I installed it and when I first logged in, everything was already ready! I was very impressed (also by the fact that ).

Later, when I downloaded Ubuntu 8.04 and installed it, my Wireless switch is not even turning on (the blue light it not coming)! Nor is my LAN able to ping the Gateway.

I have a HP nx7300 Laptop which has:

1. Intel Pro/Wireless 3945ABG card
2. Broadcom 440x 10/100 Integrated Controller

I coulnt even download the NDISwrapper. I didnt even want to try.i was just really bugged that i couldnt install the drivers from a disk or something...and i was googling for help every minute anyway...

Please..this is why most users switch back to windows (also because OpenOffice is not quite up to the mark)...

This isnt destructive criticism. This is just honest feedback.

Thank you.

---

### Post by Zorael on 2008-06-23
What is the output of both following commands, entered in a terminal?
```
$ lshw -C network
$ apt-cache policy linux-ubuntu-modules-`uname -r`
```

---

