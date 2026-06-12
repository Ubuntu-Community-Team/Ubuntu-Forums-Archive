---
title: "Nvivia driver not working and not detected"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by CaptBill on 2007-10-14
I've got an Hp 9010us with nvidia GoForce 6150 and I can't get it to function. I have to boot from the cd and use vga mode to see the screen, otherwise my screen just look like a space invaders backround. It starts out all black and bleads to white fuzz. I have install the driver using restricted drivers option and although it said success, alas it was NOT! It also has a broadcom wireless that is not working, although the lan port is woirking. Shiver me thimbers maties what's a bloke to do?

---

### Post by zergling on 2007-10-14
Hi, 
I fix all my issues about my nvidia card by using a porgram called Envy.
The website is [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
If you have Ubuntu or Debian you do not have to compile it!


For the wireless just go to [http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/18/2/](http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/18/2/)
download ndiswrapper and compile it.
After the instalaltion just type:

ndiswrapper -i driver_win.inf
and to check if everything went right type
ndiswrapper -l
if you get driver and hardware present it meas that everything is ok!

Bye and let me know!

---

