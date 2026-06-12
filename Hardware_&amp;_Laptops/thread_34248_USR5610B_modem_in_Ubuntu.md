---
title: "USR5610B modem in Ubuntu"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by simoncm on 2005-05-14
Is there anyone out there using the USR5610B US Robotics modem.  A friend is trying to get this particular modem working in a system.  I am looking for any configuration tips to get modem working.  

Thanks...

---

### Post by wwwolf on 2005-05-14
[QUOTE=simoncm]Is there anyone out there using the USR5610B US Robotics modem.  A friend is trying to get this particular modem working in a system.  I am looking for any configuration tips to get modem working.  

Thanks...[/QUOTE]

Yes, I'm using it now. :) 
'sudo wvdialconf' should tell you that it defaults to ttyS14

You can create a symlink to /dev/modem by:
sudo ln -s /dev/ttyS14 /dev/modem
Then anything using or that likes to use /dev/modem will see it.

If your symlink keeps getting deleted after you reboot, the you just add the line:
KERNEL="ttyS14", SYMLINK="modem"
in the file /etc/udev/rules.d/modem.rules

You then can edit /etc/wvdial.conf to put in the phone#, username, and passwd.

You can also set it up with 'sudo pppconfig isp' after you have created your symlink and put in the rest of the needed info, then to connect:
pon isp
and to disconnect:
poff

HTH,

---

### Post by gjcamann on 2006-08-06
Your info worked great for me thanks!  :D 

A recap:

sudo wvdialconf   (tells you what # of ttyS to use, and the init string)
sudo ln -s /dev/ttyS4 /dev/modem
sudo pppconfig isp (under advanced copy the init string, output from wvdialconf)
pon isp

---

