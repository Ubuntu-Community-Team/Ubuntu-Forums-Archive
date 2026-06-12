---
title: "Changed Motherboard- Won't Boot- HELP!!"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by CheeseQueen452 on 2007-05-10
I'm attempting to upgrade my hardware from an intel P3 1 ghz to an intel P4 2.8 ghz. After changing the motherboard, I get an error that my grahical interface is not properly set up & X Server won't start. Please help ASAP!!!

---

### Post by CheeseQueen452 on 2007-05-10
Anyone?

---

### Post by CheeseQueen452 on 2007-05-10
Can someone please help?

---

### Post by vigleik on 2007-05-10
sudo dpkg-reconfigure xserver-xorg

---

### Post by CheeseQueen452 on 2007-05-10
How do I run that command if Ubuntu won't boot?

> **vigleik said:**
> sudo dpkg-reconfigure xserver-xorg

---

### Post by tajreed on 2007-05-10
Specifically, what is happening? Can u boot into safe mode

---

### Post by CheeseQueen452 on 2007-05-10
All I know is it won't boot, & I get the error I described above. I don't see any way of booting into safe mode.

> **tajreed said:**
> Specifically, what is happening? Can u boot into safe mode

---

### Post by tajreed on 2007-05-10
after the bios check, hit escape and u will get the option to boot into a mode that leads to a command line. Then u can do: "dpkg....as above"

---

### Post by tajreed on 2007-05-10
Once u get to "sudo dpkg....." You can set up the x server manually. There is probably a prob with the Ubuntu picking up the video from the new MB. I assume that u don't have a separate video card.

---

### Post by CheeseQueen452 on 2007-05-10
How do I set it up manually? I do have a seperate video card.

> **tajreed said:**
> Once u get to "sudo dpkg....." You can set up the x server manually. There is probably a prob with the Ubuntu picking up the video from the new MB. I assume that u don't have a separate video card.

---

### Post by tajreed on 2007-05-10
which card Nvidia or ?

---

### Post by CheeseQueen452 on 2007-05-10
Asus.

> **tajreed said:**
> which card Nvidia or ?

---

### Post by tajreed on 2007-05-10
asus is the mb or the video card?

---

### Post by CheeseQueen452 on 2007-05-10
Video card.

> **tajreed said:**
> asus is the mb or the video card?

---

### Post by tajreed on 2007-05-10
ASUS uses both the ATI and the Nvidia graphics chips depending on the card. You need to determine which chip is being used.

If nvidia select NV as the driver in "sudo dpkg....", If ATI select fglrx driver. If "dgkg..." asks whether or not to id the video card and monitor, say yes. All else in "dpkg" just select the defaults.  

When u get to the end of "dpkg" reboot and see what happens

---

### Post by CheeseQueen452 on 2007-05-11
Ok, I followed the instructions I was given, & I got my new system working :) A lot of hardware changes had to be made, but it works better with the 2.8ghz processor & 1gb of memory :D

---

