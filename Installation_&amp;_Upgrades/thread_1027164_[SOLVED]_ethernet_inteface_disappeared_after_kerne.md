---
title: "[SOLVED] ethernet inteface disappeared after kernel update.."
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2009-01-01
Hey friends,, i have Ubuntu Hardy installed on my Vostro 1510.. Everything was working fine with 2.6.24-19 but then one day after updating to 2.6.24-21 i found that i had no option of "wired connection" in the manual configuration of network connections... 
I think somehow.. ethernet interface got disappeared.. and this is now the case with all the new kernels.. 2.6.24-22 for Hardy and when i tried to upgrade to intrepid.. i was having the same problem with its kernel..
Currently i m using 2.6.24-19 kernel.. 
Please help..

---

### Post by shredder12 on 2009-01-02
hey.. i found something new about my problem... instead of upgrading i used intrepid's live cd this time.. and to my wonder ethernet connection was working this time.. so does this mean that after intrepid's installation i won't have that ethernet problem again..??

---

### Post by stwalkerster on 2009-01-02
Hi!

I'm using Ubuntu 8.10, kernel 2.6.27-9-generic at the moment, but I've got Ubuntu 8.10, kernel 2.6.27-11-generic installed too. My ethernet interface (eth0) disappears every time I boot into '11. I can only assume there's an issue with '11, as that's the only thing that changes when the interface appears/disappears, leaving lo as the only interface in ifconfig. (My wireless card isn't working yet, so I can't comment on that - but that's a different issue)

---

### Post by shredder12 on 2009-01-02
hey.. well i really want to upgrade my system to intrepid.. but i don't want to mess up things like last time..
So, isn't there any way by which i can check if things are gonna work fine after the new installation.. does the proper working with the live cd in the previous post mean that there will be no wired connection problem after the installation??
....

---

### Post by davidself1001 on 2009-01-02
My eth0 was gone from my network manager applet when I upgraded to 8.10 and I found a fix on one of the other threads that worked for me.  I commented out the iface eth0 inet dhcp, address, netmask and gateway lines from my /etc/network/interfaces file using sudo gedit /etc/network/interfaces.  After doing so and rebooting everything works fine for me.

---

