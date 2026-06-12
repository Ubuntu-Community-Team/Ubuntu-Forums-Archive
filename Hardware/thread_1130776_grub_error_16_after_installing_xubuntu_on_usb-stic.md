---
title: "grub error 16 after installing xubuntu on usb-stick"
date: 2009-04-20
forum: Hardware
---

### Post by micro133 on 2009-04-20
Hello !

That's my first post so at the beginning I want say hello to everybody, so:

HELLO EVERYBODY ! :-)

I have a question not directly related to xubuntu (I believe) but boot mechanism in general.
I've tried install xubuntu on pendrive. My goal is to create Linux installation which I can connect to the any PC which I see nearly and run it by boot from USB.
I don't need graphical UI, I need only working network, Webmin, apt-get and some other stuff.

The problem is that this after installation I get the grub error 16. Error 16 means inconsistent file system.
But i'm little but confused what that really means.
If Grub said that because it cannot read /boot/grub/menu.lst ? I'm not sure how grub is working in details, but it doesn't requeire reinstallation after any change in config file (like it was in lilo). That means (for me) that Grub is able to read filesystem directly and probably that the problem is here.

After few trials, I connect my pendrive to another computer with working linux and perform fsck.ext3 (because it's formatted using ext3), console said that there were some problems which are now recovered (i don't remember what problems) but it actually doesn't change anything in booting.

After that I've tried to change root= parameters (again using another linux) beacause I was thinking that maybe it's wrong and maybe grub is looking this information when looking for his config file, and maybe device names has changed. but actually it also doesn't change anything. 

This is actually another problem how-to get this pendrive always working in any HDD configuration on computer I want to use. I don't know root=UUID= mechanism, If it can help in this issue ?

So, I'm writing here beacause actually I have no idea what direction I should get to get my linux working. I have feeling that there is something else I should know. 

Thank you for all replies.

Cheers 
Greg

---

### Post by randcoop on 2009-04-20
I have successfully used these instructions:

[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive]("http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive")

Give them a try.

---

### Post by micro133 on 2009-04-20
Thank you so much, I will check when I will have some time and tell you the results.

---

