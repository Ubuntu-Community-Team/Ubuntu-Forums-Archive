---
title: "Acer TravelMate 340T Video Issues"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2006-04-27
I have an Acer TravelMate 340T with dual boot to Windows 2000.  In Win 2000 the colors look normal as they should.  The resolution of the notebook goes up to 800X600 but if you connect an external monitor you can up the resolution up to 1024X768 on the external monitor only.  This works fine and dandy in Windows 2000.

Come on the Ubuntu side things are different.

1) The colors are off.  It seems like it's using 16bit even though in the xorg.config file it's set up for 24bit.  When I connect an external monitor I notice that the colors are "normal" but yet on the LCD they are not i.e. the brown on the Ubuntu site looks darker with a hint of orange (whatever that color is) on the LCD.  In Windows 2000 both LCD and External monitor match.

2) I can't set the resolution to 1024X768.  The only options I have is 800X600 and 640X480.  I ran the xorg configuration utility and specified 1024X768 and 800X600 as the possible resolutions but I don't get them.

---

### Post by dangermouse28 on 2006-04-28
Start with the basics - have you got the right video driver installed? Do lspci and look for details of the video chipset. Then search in the forum for the relevent how-to. Both ATI and NVIDIA are well covered.

---

### Post by GoodPanos on 2006-04-29
Thank you for that command.

Ok, I ran it and this is the following I got:

0000:01:00.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49)

Now what?

---

### Post by dangermouse28 on 2006-05-03
Go to [www.linux-on-laptops.com/forum/archive/index.php/t-135.html](www.linux-on-laptops.com/forum/archive/index.php/t-135.html). Looks like someone else has solved this one already:-D

---

