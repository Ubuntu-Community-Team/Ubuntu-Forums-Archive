---
title: "Setting the boot sequence"
date: 2008-11-26
forum: Hardware
---

### Post by cairnsww on 2008-11-26
This is not really an Ubuntu question but the problem came up when I tried to use a live Ubuntu CD.

I have a brand new Mecer PC with a Johannesburger motherboard - no PS2 ports. It runs like a dream and even manages to make Vista look quite speedy. The trouble is that it will not boot off the CD or a flash drive for that matter. Obviously the boot sequecnce has the hard drive first. So I need to get into BIOS to change the boot sequence. Except I can't change get into BIOS because I have a USB keyboard and my frantic pushing of F2 yields no result. Perhaps "Legacy USB Support" is not enables. Well, if I could get into BIOS, I could enable it ...

Helpful howtos such as [http://www.intel.com/support/peripherals/sb/cs-011939.htm](http://www.intel.com/support/peripherals/sb/cs-011939.htm) from Intel themselves suggest that the best thing is to use a PS2 keyboard to get into BIOS and enable Legacy USB support. Good suggestion - except I don't have a PS2 port ...

I found the comment on another site: "I am using a USB keyboard, so I had to go into the guts of the PC and change the jumpers. I'd never have thought that was the problem."
[http://au.answers.yahoo.com/question/index?qid=20070528083816AAVFs4K](http://au.answers.yahoo.com/question/index?qid=20070528083816AAVFs4K)

Any ideas?

Bill

---

### Post by amac777 on 2008-11-26
Just an idea, is there a way to add a boot menu in Vista so that you could select "boot from cd" when the computer boots? I think this is possible with grub, but I guess that won't help you since you don't yet have linux installed on your system.

---

### Post by TFX360 on 2008-11-26
Deadlock. No way you are getting in the BIOS. A reset prolly doesn't work either as USB Legacy support is defacto disabled.


Sorry mate.

---

### Post by glotz on 2008-11-26
Flash the BIOS? :)

---

### Post by amac777 on 2008-11-26
I still think you can make your computer boot from a CD by setting up a boot menu in Vista to do it. I don't have Vista though so I can't figure it out. But I did find this link:

[http://technet.microsoft.com/en-us/library/cc721886.aspx](http://technet.microsoft.com/en-us/library/cc721886.aspx)

It seems to be similar to a grub menu and you can make changes by running the program: Bcdedit.exe  (It's part of vista)

---

### Post by TFX360 on 2008-11-26
> **glotz said:**
> Flash the BIOS? :)

Hack it to set USB Legacy Support to **1** or **on** or **True** :)

---

### Post by TFX360 on 2008-11-26
> **amac777 said:**
> I still think you can make your computer boot from a CD by setting up a boot menu in Vista to do it. I don't have Vista though so I can't figure it out. But I did find this link:

[http://technet.microsoft.com/en-us/library/cc721886.aspx](http://technet.microsoft.com/en-us/library/cc721886.aspx)

It seems to be similar to a grub menu and you can make changes by running the program: Bcdedit.exe  (It's part of vista)

Possible, but he still isn't going to get in the BIOS...

---

### Post by amac777 on 2008-11-26
Well, you said the computer is brand new, so call the company that sold it to you and ask them how to get in the bios. Maybe there is a way.

Also, are you sure it's F2 on that computer? 

Try pressing and holding down several of the keys while it boots up and see if you a "Keystuck error" or something.

---

### Post by TFX360 on 2008-11-26
> **amac777 said:**
> Well, you said the computer is brand new, so call the company that sold it to you and ask them how to get in the bios. Maybe there is a way.

Also, are you sure it's F2 on that computer? 

Try pressing and holding down several of the keys while it boots up and see if you a "Keystuck error" or something.

Most of the time F10/F12/DEL.

---

### Post by terryeden on 2008-11-26
Unplug the power (and only the power) of the HDD.  The BIOS will then skip that and try and boot off the CD.  Once it has started booting from the CD, you can plug in the power to the HDD.

That's assuming that the BIOS is set to boot from other devices if it can't find the HDD.

Be careful when playing in the guts of your PC - keep your clothing and hair free of the fans and components.  

That's all I can think of - sorry.

T

---

### Post by cairnsww on 2008-11-26
Thanks for the suggestions guys.

I did speak to the expert at the computer manufacturers and yes it is F2.

Apparently, the "Enable Legacy USB" is a red herring. It has nothing to do with sensing F2 at start up.

He did suggest that it might be the keyboard I am using - it is made by Yodata (never heard of them!) and might be sending different codes. I am trying to borrow a more standard keyboard.

Otherwise, he made the suggestion is that I could just change one of the jumpers on the motherboard that would force the computer to boot into the BIOS menu. It would seem to be the last resort though.

---

### Post by TFX360 on 2008-11-26
Good luck!

---

