---
title: "wireless not detecting in Ubuntu 9.04"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-13
Hi,

I installed Ubuntu 9.04 in my HP laptop. The lan card is detecting but the wireless card is not detecting the wireless signals of access points.

Please help...........:(

---

### Post by kiridude on 2009-10-13
On a new installation, it sticks sometimes. right click the connections icon and uncheck "enable wireless." then re-check it. Also, make sure wireless is turned on. If you are dual booting with windows and have turned off wireless in Windows, many times it will not work right in Ubuntu, so you have to go back into Windows and turn it on, then reboot

If it is neither of these, post the output of:

```
sudo lshw -C network
```

to open a terminal: Applications > accessories > terminal

---

