---
title: "Wireless keyboard disabled during booth sequence"
date: 2010-07-12
forum: Hardware
---

### Post by garygdoucet on 2010-07-12
I am new to ubuntu or linux
 
         A few weeks ago , I installed ubuntu 10.04 on my PC keeping Windows XP operational until I can get all my needed multimedia software installed . So far so good except for a small problem.
 
During the first part of the booth sequence ( e.i. hit the F2 key to access the bios setup ) my wireless keyboard is operational.
 
during the next part where I have to choose between ubuntu or windows, my wireless keyboard is not operational so I have to connect a PS2 keyboard to make my choice .
 
After entering ubuntu or windows welcome page , My Wireless keyboard is again operational .
 
My wireless keyboard is a Logitech EX 100 with a USB connected receiver.
 
Help would be greatly appreciated .

---

### Post by PatrickW on 2010-09-03
I have the exact same problem, except with a Logitech Wave 2.4.

The keyboard functions properly both before and after the GRUB boot loader.  I'm able to access my BIOS and make changes there (USB keyboard is enabled - I've seen many threads about that one, but it's not the same problem), and I'm able to type in my login and password after GRUB times out and chooses the first option on the list, which happens to be one of my Ubuntu drives.

I should note that if I fiddle with my arrow keys while the GRUB screen is up, when it times out, some curious characters display at the top of the screen briefly before it continues with the boot process, as though my keystrokes had been sent to a buffer of some kind and not allowed to interact with the GRUB menu.  They look like [^^C, [^^D, or something close to that.

I'm using GRUB 1.97~beta4

---

