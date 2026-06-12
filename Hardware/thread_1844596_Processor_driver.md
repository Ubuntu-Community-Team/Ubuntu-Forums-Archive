---
title: "Processor driver"
date: 2011-09-15
forum: Hardware
---

### Post by AoFhEkOl on 2011-09-15
Hi, 

I have a khlb2 compal laptop, i'm interested in trying our ubuntu.  With windows i have a problem with the processor driver, and i had to change it to "intel processor driver" which is the sencond option in device manager.  Last time i tried ubuntu it black screened which is what used to happen with windows.

My question is how can i change the processor driver in ubuntu? i have a intel core duo 2 cpu p8700 2.53mhz.

---

### Post by 2F4U on 2011-09-15
There is no processor driver in Ubuntu. Either your processor architecture is supported by  the kernel or not. However, Intel Core Duo are certainly supported. A black screen may have many different reasons and it is more likely a graphics  problem.

---

### Post by AoFhEkOl on 2011-09-16
That was the problem with windows, the processor driver not the graphics.  I know it sounds hard to believe but it took me a long time to sort out and the help of many forums. 
 
So i don't have an option when it comes to changing the driver? any ideas?

---

### Post by AoFhEkOl on 2011-09-17
I'll try changing the grapics driver but i don't think it will work.  When i say it's a black screen what i mean is only the power is on, hard drive, screen etc are dead, sometimes it restarts.  All i can think of is that it's a power saving cpu and the graphics card is doing something to interfere with the cpu.

---

### Post by grahammechanical on 2011-09-17
You may have already done this but may I suggest it for completeness?

You try the Ubuntu Live CD with the latest version 11.04 64bit. The P8700 is a 64bit CPU after all and things may have improved with Linux since this CPU was released in 2008.

Then make a note exactly of what happens or what messages you get as you try run Ubuntu off the Live CD. It is important for us to know exactly at what point you get the black screen.

Also there boot settings that can be changed to get the CD to load. Others on this forum might be able to suggest what adjustments to make. Such as nomodeset, which I think allows the CD to run without setting a video mode.

This link might help.

[http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation")

Regards.

---

### Post by AoFhEkOl on 2011-10-03
thanks, i'll give it a try and report back :)

---

### Post by AoFhEkOl on 2012-09-04
processor.nocst=1 solved the problem :p

---

