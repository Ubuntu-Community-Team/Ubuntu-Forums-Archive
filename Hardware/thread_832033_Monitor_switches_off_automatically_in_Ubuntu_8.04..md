---
title: "Monitor switches off automatically in Ubuntu 8.04. Help"
date: 2008-06-17
forum: Hardware
---

### Post by arunthegr8 on 2008-06-17
I recently installed Ubuntu 8.04, n since i m no pro of linux, i m not able to solve this problem of mine. My monitor, an old Samsung Samtron 55v 15" crt, automatically switches of in Ubuntu and even after trying everything i can it remains so. if i manually restart the pc, d montor starts workin again.

i dont think it is a hardware problem since it works well in xp. plz help me out.this is causin a lot of problems.

I have already tried the following things...
[http://www.thinkdigit.com/forum/showthread.php?p=859243&posted=1#post859243](http://www.thinkdigit.com/forum/showthread.php?p=859243&posted=1#post859243)

---

### Post by overdrank on 2008-06-17
> **arunthegr8 said:**
> I recently installed Ubuntu 8.04, n since i m no pro of linux, i m not able to solve this problem of mine. My monitor, an old Samsung Samtron 55v 15" crt, automatically switches of in Ubuntu and even after trying everything i can it remains so. if i manually restart the pc, d montor starts workin again.

i dont think it is a hardware problem since it works well in xp. plz help me out.this is causin a lot of problems.

I have already tried the following things...
[http://www.thinkdigit.com/forum/showthread.php?p=859243&posted=1#post859243](http://www.thinkdigit.com/forum/showthread.php?p=859243&posted=1#post859243)

Hi and welcome, when does the monitor shut off? When the screen savers are activated? Have you check the power management settings in screen saver settings. I see you have another post for the desktop effects also, and have you tried and reconfigure you xorg after activating the restricted drivers? If have not you can try and use the keys ctrl, alt, F1 and this will bring you to the terminal and login. Then reconfigure you xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use the command startx or sudo reboot.

---

