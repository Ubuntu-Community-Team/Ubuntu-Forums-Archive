---
title: "Compaq CQ61-125EQ suspend/resume freeze"
date: 2009-10-24
forum: Hardware
---

### Post by calin_ionut on 2009-10-24
I have a problem with the resume on this laptop:[Compaq CQ61-125EQ]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01715101&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

I install the Ubuntu 9.10 RC and i have a lot of problem with this laptop, but this is the most important with the resume. I can`t "close" the laptop to resume because it freeze. :mad:

When it suspends works, the cooler is stoping and the power led blinking. The problem is when a want to resume....the system freeze, the display is black and only the mouse cursor i can see. 

If i want to go in the tty1 (ctrl+alt+f1) to kill the X and to log back to the system i get this message:

```

ata1: irq_stat 0x00000040, connection status changed
ata2: SError : {DevExch}
ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen

```

and the message keep going with the same error and can`t write anything in the console :confused: 

I have to force it to turn it off from the power button 

Anyone have any idea how to fix this?

---

### Post by calin_ionut on 2009-10-24
Anyone????? I have tried this 2 tips:

[Tip 1]("http://www.linux.com/news/hardware/laptops/8253-how-to-suspend-and-hibernate-a-laptop-under-linux")

[Tip2]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

And the same thing :(

---

### Post by calin_ionut on 2009-10-24
I just fixed. I made an update to BIOS to F.03 to F.13A and now works! 

Cheers!:guitar:

---

### Post by amireldor on 2012-02-19
Can you tell how did you update the BIOS? Can this be done through Ubuntu?

---

### Post by calin_ionut on 2012-02-20
Nope, I did this update on Win 7. You should have Windows Install when doing this.  You can download a trial version of windows and make the update then go back to ubuntu. 

Cheers!;-)

---

