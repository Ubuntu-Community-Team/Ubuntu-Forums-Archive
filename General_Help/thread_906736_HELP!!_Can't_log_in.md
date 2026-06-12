---
title: "HELP!! Can't log in"
date: 2008-08-31
forum: General Help
---

### Post by jc0811 on 2008-08-31
My installation went smoothly. I am running Hardy Heron right now. Specifically 8.04.1. After install it showed the login screen. I type my username and password at the login window. Its after I press Enter is when I have the issue. After I hit Enter. The screen goes black and then it reappears with the same login window. Asking for my username and then my password. I have tried logging in numerous times but it won't work. 

I then restart and choose recovery. The second choice for Linux and that works now. I can see the Gnome desktop. Is it because of my video card?? I have the ATI Radeon Express 200 card by the way. I hope this makes sense and hope somebody can help with this issue. Thank you.

---

### Post by falcon61102 on 2008-08-31
Yeah, that sounds like it's an issue with your video card.  What you can try doing to resolve this would be to startup in the recovery mode and install the drivers for your video card there.  Once they are installed then you should be able to boot up in the normal mode.

Also, be sure you check to see if you can enable any restricted drivers.  Go to System>Administration>Hardware Drivers
Then see if your video card is listed there.  Click the check box to enable if it is present.

---

### Post by monkeyking on 2008-08-31
If you just want your box to work without all the fancy graphics,
simply set vesa driver in your x11 config. I think the name now adays is /etc/X11/Xorg.conf.

good luck

---

