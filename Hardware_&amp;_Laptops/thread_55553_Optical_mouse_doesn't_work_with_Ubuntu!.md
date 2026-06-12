---
title: "Optical mouse doesn't work with Ubuntu!"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by Darkscot on 2005-08-09
Whilst visiting Asda yesterday to purchase beer and BBQ material I spotted a very nice optical mouse at an apparent bargain price.  I purchased the glowing rodent under the naive assumption that it would work with Ubuntu, but it doesnt.  I tried searching for suitable drivers but no luck.  

Anyone got any suggestions or is it not worth the bother?  (It is a Trust AMI 250S Optical by the way.)

---

### Post by dave9191 on 2005-08-09
1) Don't buy anything from Trust, its not a company to be trusted. Everything I ever had from them was a bargin and fell apart real quick. 

2) I don't see any reason why the mouse wouldn't work under linux. Does it light up when you plug it in? Im guessing its a USB mouse. 

3) I use a cheapsate budget optical mouse with my comp, so they do work. 

Dave

---

### Post by Darkscot on 2005-08-09
It is a PS2 mouse.  It lights up when the PC first boots up but then it goes out.  The buttons 'work' but that is small consolation.

---

### Post by dave9191 on 2005-08-09
In that case I'm guessing that this might be some sort of driver issue with ubuntu. But I don't reall know how to proceed. Maybe someone else has an idea. 

Dave

---

### Post by woedend on 2005-08-10
im no expert but i'll try.  was your last mouse USB?  if so, it may be set for USB and not working right.  Have you tried reconfiguring your mouse in Xorg?

---

### Post by Darkscot on 2005-08-10
This is a lot more complicated than first appeared.  I switched back to my old mouse and now that is giving problems in Windows!!!!  aaaargh!  Looks like it might be a hardware issue.

---

### Post by autocrosser on 2005-08-10
If you wonder if a device will work with Linux----Look here first- 

[http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

This site has helped me more times that I can count!!!! :-)

---

### Post by Gezzer on 2005-08-10
[QUOTE=autocrosser]If you wonder if a device will work with Linux----Look here first- 

[http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

This site has helped me more times that I can count!!!! :-)[/QUOTE]
 with the new mouse installed open a konsole/terminal and write

sudo dpkg-reconfigure xserver-xorg

follow the on screen instructions and hopefully it will configure your new attachment ...

---

### Post by Darkscot on 2005-08-11
Thanks to all who offered advice.  However, I have solved the problem and it is nothing to do with Ubuntu.  The 'bargain' (HAH!!!) Trust mouse has ****** my PS2 port! I tried various PS2 mice and all gave various problems on both Ubuntu and Windows.  Then I tried a USB mouse and all is well.

As a Dave9191 said, Trust are not to be trusted.

---

