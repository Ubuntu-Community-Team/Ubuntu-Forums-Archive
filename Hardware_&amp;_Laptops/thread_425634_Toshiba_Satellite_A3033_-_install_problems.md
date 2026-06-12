---
title: "Toshiba Satellite A30/33 - install problems"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by gwilym on 2007-04-27
Hi there,

I downloaded the latest Ubuntu last night and installed it on a Satellite A33 laptop. It installed fine but when i boot to it it gets to login, I put in my user/pass and then it hangs on an orange screen with the cursor on (the mouse works).

I noticed that the during start up a message came up saying "8254 timer not connected" so I searched in the forums and found out about appending "noapic" at grub which I did - this didn't make any difference other than removing the message.

Hmmm...

Anybody got any ideas where to go from here? Any help much appreciated.

Many thanks,

Gwilym

PS: The Laptop is Pentium4 with ATI Radeon 9000 and 512mb RAM

---

### Post by drumkitcat on 2007-05-16
I don't know if it will be much help or not;

I've heard/read many people having problems installing Feisty in general, let alone on Toshiba laptops... personally, I'm running Edgy (ver 6.10) on my Toshiba Satellite A40 laptop.. and it's marvellous and totally stable.  

I started off installing Dapper (version 6.06) and it also ran great - then I found out about Edgy (ver 6.1) so I reformatted the drive and installed it, and have been using it for a few months now without any serious issues at all.  

I did have to dink around with getting wireless to work, but otherwise, everything else is fine.  In general, it takes up less space than Windows XP, boots much faster, and runs much better overall.

Personally, I'm going to wait a while before upgrading to Feisty from Edgy... sometimes if it ain't broke it's not worth fixin'!

Paul

---

### Post by dre2004 on 2007-05-22
I've got the very same problem as the original poster. I must admit this laptop has been very problamatic in terms of getting linux installed on.

Some of the things which have caused me issues in the past have been

- Keyboard / touchpad not working during install (Redhat, FC and I think even Slackware)
- Sound not working (This is due to the modem using the same chipset as the sound card)
- Touchpad doing strange things.

If i knew  i was going to have these issues I probably would have never bought this laptop. Things you need to do to get it working.

In /etc/modprobe.d/blacklist-modem

- Uncomment snd-atiixp-modem

Well so far I've narrowed it down to the volume application which is crashing every time I login I get sound but then it seems some gnome applet is crashing which is preventing gnome from starting.

---

### Post by dre2004 on 2007-05-22
I've managed to get it to login but now need to get the sound working.

I added the acpi=off kernel option to the default kernel in

/boot/grub/menu.lst 

This will probably need to be changed so when you upgrade the kernel that option is automagically added also

---

