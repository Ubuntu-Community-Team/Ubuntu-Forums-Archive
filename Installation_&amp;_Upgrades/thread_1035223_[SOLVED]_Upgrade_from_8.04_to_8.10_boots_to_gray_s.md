---
title: "[SOLVED] Upgrade from 8.04 to 8.10 boots to gray screen"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by driven1 on 2009-01-09
I finally decided to upgrade to Intrepid on my AMD box, the upgrade went smoothly with no install issues or errors, but at reboot, when I should see the login screen, it flashes a couple of times, then goes to a grayish color where it remains. Has anyone had a similar experience or know what I need to do to troubleshoot this? I was happy with Hardy but couldn't leave well enough alone...

---

### Post by lemming465 on 2009-01-10
If you press CTRL-ALT-F1 do you get a text console login prompt?  If so, you are yet another victim of the significant and not fully debugged changes in the X server and drivers (nvidia, ATI, and intel issues exist, which covers a lot of us :-() 

If you can log in at a text console, try:```
sudo -i
apt-get update
apt-get upgrade
dpkg-reconfigure xserver-xorg
```
and see if that improves the situation.

---

### Post by driven1 on 2009-01-11
Thanks. I already reinstalled Hardy. Armed with your advice maybe I'll try to upgrade again today.

---

### Post by driven1 on 2009-01-11
Did a fresh install of Hardy, updated then upgraded and now Intrepid seems to work fine. I'm still in the process installing everything again and configuring, etc.

---

