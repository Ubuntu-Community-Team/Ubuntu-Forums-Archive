---
title: "Usb issue"
date: 2011-10-19
forum: Hardware
---

### Post by lucas8880 on 2011-10-19
hey guys, i have asked this question, and seem to have not received an answer..
My usb's do not work on my dell inspiron-1546. with a mouse, i can see that power is supplied, when i type in lsusb in the terminal i get this error:

unable to initialize libusb: -99

I am using Ubuntu 11.10
and i had this problem in 10.10 (i skipped 11.04 so idk if it would have worked then)
I know that my usb ports do work (not fried or anything because i was able to use them in 10.04)
it just seems they are not working now.
so i am unable to use any usb device, and i would really appreciate some help
thanks in advance

---

### Post by hazyEgG on 2011-11-09
I am having the exact same issue Dell Inspiron 1546 ... no usb what so ever. lsusb renders a failed initization code -99. I have tried everything. Had this problem since 11.10 ... somehow it worked on 11.04 but does not now even on a clean reinstall and format. I think something radically changed in both kernels since my initial download of 11.04.
The USB ports do work on Windows 7. I am going to wipe Ubuntu entirely this weekend and try a clean debian install and I will report back to the class. This super sucks for us because all the suggestions I get on the answers ubuntu page are candy attempts to solve a problem that is at the kernel level. If the OS does not see USB hardware.... you cannot apply a stupid lil fix.. fdisk shows nothing on USB pens and lsusb proves there is nothing plugged in to the any of the USB port.... no mouse, cam, nothing!  Sys log .... nothing when plugged in.... NOTHING!

**[COLOR=DarkRed]SOLUTION:[/COLOR] ITS AT THE BOOT LOADER LEVEL GRUB2 IS OUR PROBLEM CHILD HERE**
Okay I showed my a$$.
Here is the step by step solution  to this one:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732)

And dig my stupidity... the reason that my 11.04 worked is because I _**now**_ remember performing these steps with that version of Ubuntu

---

### Post by lucas8880 on 2011-11-19
> **hazyEgG said:**
> I am having the exact same issue Dell Inspiron 1546 ... no usb what so ever. lsusb renders a failed initization code -99. I have tried everything. Had this problem since 11.10 ... somehow it worked on 11.04 but does not now even on a clean reinstall and format. I think something radically changed in both kernels since my initial download of 11.04.
The USB ports do work on Windows 7. I am going to wipe Ubuntu entirely this weekend and try a clean debian install and I will report back to the class. This super sucks for us because all the suggestions I get on the answers ubuntu page are candy attempts to solve a problem that is at the kernel level. If the OS does not see USB hardware.... you cannot apply a stupid lil fix.. fdisk shows nothing on USB pens and lsusb proves there is nothing plugged in to the any of the USB port.... no mouse, cam, nothing!  Sys log .... nothing when plugged in.... NOTHING!

**[COLOR=DarkRed]SOLUTION:[/COLOR] ITS AT THE BOOT LOADER LEVEL GRUB2 IS OUR PROBLEM CHILD HERE**
Okay I showed my a$$.
Here is the step by step solution  to this one:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732)

And dig my stupidity... the reason that my 11.04 worked is because I _**now**_ remember performing these steps with that version of Ubuntu

THANK YOU SO MUCH, you really helped me. this is outstanding.  i have been looking for the answer for a very long time.  it works perfectly! I shall help others with this problem aswell. 
   EDIT: although this does fix my issue, it arises another.. my proccessor seems to always be working at its maximum speed, and anything related to may battery disapears.the icon is no longer there as though i had no battery, and any other battery monitoring program doesnt work

---

