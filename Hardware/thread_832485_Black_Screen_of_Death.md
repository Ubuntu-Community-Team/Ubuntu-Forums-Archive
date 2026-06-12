---
title: "Black Screen of Death?"
date: 2008-06-17
forum: Hardware
---

### Post by charliman on 2008-06-17
I just installed the latest build of Umbuntu on my dell inspiron 1100 - Install went fine and I was able to play around with it for 1 restart. After I had quit and restarted, I got nothing but a blank screen. I have tried multiple times to restart and get the same result. What can I do?

---

### Post by famous3warriors on 2008-06-17
Ok what did you do last before powering down or did it just go blank?  Cause that happen to me one time. When you start up your computer can you get into your Bios?

---

### Post by ladr0n on 2008-06-17
This happens occasionally on my desktop (Dell Dimension something or other).  I haven't found a real solution for it, but escaping into the grub menu, pressing e to edit the entry for ubuntu, and then pressing b to boot seems to work most of the time.  Sometimes it will go black on boot as soon as X starts, sometimes after I've used it for a little while (but when it goes black while I'm using it it [I]never[I] works properly on reboot) 
Can anyone think of a reason it would do this?

---

### Post by charliman on 2008-06-17
Yes I can get to my Bios - I'm testing the Umbuntu OS out for a software company to see if we need to include it in our list of OS's - Can you guess what rating I'm giving it so far ](*,)

---

### Post by charliman on 2008-06-17
Well folks, I have started it a few times now and I do like the OS and other than this problem, I really like it. I'm sure I'll run into a few other snafus but so far so good. \\:D/

---

### Post by halyihev on 2008-07-17
I'm having the same problem, but it worked fine for months until I did some recent upgrade a month or so ago.

I do like Ubuntu, but I have to admit this is quite frustrating.

---

### Post by jbrax on 2008-10-20
These are steps you have to take to get Ubuntu-8.04 running in Dell Inspiron 1100: 

1. Upgrade your laptops BIOS to A32
2. Go to BIOS Setup and change the video memory value from 1MB to 8MB
3. Install Ubuntu-8.04 
4. Edit /etc/X11/xorg.conf to get 1024x768 resolution
5. Change splash to nosplash, line 89 in /boot/grub/menu.lst 

This last one fixes the "Blank screen after every other boot" -error. Do not uncomment (=remove # from the beginning of that line). If you have already updated the kernel you have to change "splash" to "nosplash" manually in every existing kernel line too.

For more detals see comment 18 at [http://ubuntuforums.org/showthread.php?t=819541](http://ubuntuforums.org/showthread.php?t=819541)

---

### Post by hopesdevid on 2008-10-20
Hi friend,
                  I think you have to go with perticular company site of your devices.I don't know the exact problem but i have seen the question a few times. good luck.

---

### Post by ammikulka on 2008-10-20
if you are using 8.10 i think its unfair cause its still in beta, however 8.04lts its pretty solid on my HP

---

