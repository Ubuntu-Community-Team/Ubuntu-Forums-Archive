---
title: "ubuntu 7.04 on IBM thinkpad T40"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by vr76413 on 2007-08-15
I installed ubunti 7.04 on IBM thinkpad T40 laptop and everything is fine except the screen resolution where the max is 1024x768. 
Not sure how to increase that. but iam just curious to know what is the video card in this machine. 

1.Any ubuntu command  i can go to find out the video card make and model ?
2.how to increase screen resolution to higher one like 1200 x 800


thanks
Ram K

---

### Post by randcoop on 2007-08-16
To determine the video card, you can run
```
lspci
``` in the terminal.  That will give a list of many of your components; look for the VGA or whatever and it will give you the brand name.

To get a higher resolution, you'll need to edit your /etc/X11/xorg.conf file to add the higher resolution numbers.  This can often be done using a program in the command line:```
sudo dpkg-reconfigure xserver-xorg
```

That's the simplest method.  If it fails, you'll need to edit the xorg.conf file manually.

Do a search for xorg.conf here in the forums and you'll find hundreds of messages that explain how to do that.

---

### Post by Roger Mudd on 2007-08-16
Check the serial number on the bottom of the laptop and then run that up against[ IBM's website]("http://www-307.ibm.com/pc/support/site.wss/homeLenovo.do"). It should be able to give you the full system specs.

---

