---
title: "Ubuntu on Asus A8Jc - Work log"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by brsseb on 2006-07-08
After looking for a new laptop to use Ubuntu on, i finally placed an order for the Asus A8Jc. Its similar to the Asus A8Jm, but with a slower nvidiacard (and thus longer batterylife and less heat & fan noise, I hope..) 

While certainly no ultraportable, it sure seems like a small and light notebook. Even though its a Core Duo, battery life should be around 3-4 hours, like the old centrinos. I expect one gets around 2.5-3 hours with Wifi on. 

[IMG]http://www.asus.com/999/images/products/1066/1066_m.jpg[/IMG]

Product info (Norwegian site)
[http://www.komplett.no/k/ki.asp?sku=322901]("http://www.komplett.no/k/ki.asp?sku=322901")

Edit: Here is the official Asus product site:
[http://www.asus.com/products4.aspx?modelmenu=2&model=1066&l1=5&l2=26&l3=270](http://www.asus.com/products4.aspx?modelmenu=2&model=1066&l1=5&l2=26&l3=270)


[LIST]
[*]33.5 cm x 24.5 cm x 3.7 cm
[*]2.4kg
[*]Intel Core Duo T2300E 1.66 GHz ( Dual-Core )
[*]1GB 667Mhz (Gonna put in an extra 1GB chip later)
[*]4-1 Card reader
[*]80 GB 5400-disk
[*]DVD-burner
[*]14.1" TFT WXGA (1280x800) 
[*]NVIDIA GeForce Go 7300 TurboCache
[*]WiFi and Bluetooth
[*]Integrated Webcam (.3MP)
[*]DVI-I out, which I need for my external LCD
[/LIST]

Ill get it next week, and ill report my experience with it, and any problems I need help with, in this thread. Aint much info about this fairly new computer, but most of the stuff should work out of the box with Ubuntu. 

If anyone got any tips, thoughts, comments or anything they wanna share, please post it here.

---

### Post by rollps on 2006-07-11
hey,

I have the Asus A6JC, which differs from yours only by the screen (15.4" on A6)
I installed Xubuntu 6.06 and everything is working out of the box, except card reader and webcam and some hotkeys.

It's really easier to install ubuntu than win xp now (thanks to Automatix too)

have fun with yours !! :)

---

### Post by brsseb on 2006-07-11
I have gotten the machine now, and installed both WinXP and Ubuntu on it in dualboot. In ubuntu everything works after you get the latest upgrades and run automatix (to get the nvidia driver working, among other things). I have not tested hibernate/suspend yet, though. 

Since its a nvidia card, you dont need to fiddle with 915resolution, one just install the driver and edit the xorg.conf-file to any resolution you want, and it will set it to that (in this case, 1280x800). Sound, wireless, card readers, etc works like a charm. No problem with the latest Core Duos either, frequency scaling works great (but you might wanna make sure you get the 686 version and not the regular 386 one).

However, I seem to be having a bit of a problem with mine. Basically the fan starts just after bootup and STAYS ON, both in WinXP and in Ubuntu. It seems to never stop, even if I dont use it and it sits idle on the desktop. Only way to shut it up is to close the lid and let it sleep for a second. But the fan comes on again and stays there. ](*,) ](*,). 

Everyone says its supposed to be a quiet machine. Having owned a fanless ultraportable for a year, im not sure if its me or the laptops thats messed up, but I know i need to fix this somehow, or I have to return it..

---

