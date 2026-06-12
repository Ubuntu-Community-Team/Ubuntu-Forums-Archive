---
title: "Dell Inspiron 1501. VGA output blank"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by nithinsujir on 2007-08-15
Hi, 
Ubuntu works great on my laptop except for this one issue. I connected it to my LCD TV using the vga out and press Function + F8 to direct the display to the LCD but nothing happens. 

Anyone got this to work?

How can I debug this?

Thanks,
Nithin.

---

### Post by xarroyo on 2007-08-27
I have the same problem.. One solution is that turn on the computer and you must have already plugged the cable on the output video... and then it seems to recognize it.. at least, it works for me!! but i want to know how to make it work by pressing FN + F8.. 
FN and the Volume setting works, also for enable and disable the Wireless.. but it seems that is not working for the output video.. is there any special setting to make enable the output video???

it is really annoying restart the computer to make it fix!! does anyone knows a better solution????

---

### Post by nithinsujir on 2007-08-27
if it works on restart of the machine, maybe it will work with restarting xserver. 

can you try this?
1. boot without vga.
2. connect the vga.
3. ctrl-alt-backspace to kill xserver. it should restart. 

see if it works. i'm going to try the restart one tonight.

---

### Post by xarroyo on 2007-08-29
when do i have to do the third step?? before i start my ubuntu session?? 
i noticed that you need to boot with the VGA plugged in order to activate it.. once, you see the ubuntu splash, it can be disconnected, and you can connect it later if you need to.. the VGA is already activate and it will be disable if you restart the computer..

---

### Post by nithinsujir on 2007-08-29
i let ubuntu boot completely into the gui. after it reached the desktop, I connected the vga cable. and then pressed ctrl-alt-backspace.

this kills the x server and it xserver restarts automatically. now the vga display was active. 

N.

---

### Post by BrianM23 on 2008-02-19
Can you give me a link to the cord you were using. I have the same laptop running ubuntu and followig these steps is not giving me any results.

---

### Post by nithinsujir on 2008-02-19
hmm, it's not anything special. it's just a 6 ft vga-vga cable i picked up at fry's.

---

