---
title: "64-bit Installation Hangs"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by izrafeel on 2009-06-11
Hi,

I have a 64-bit Compaq Presario CQ60Z running Vista Home Premium.  I'm trying to convert it to Ubuntu 8.04 using an install disc I created with the corresponding 64-bit desktop version of Hardy Heron.

After booting from the CD, selecting either the "Install Ubuntu" or "Test Drive" option causes the installation to hang at precisely the same point.  This happens early on; the screen is black and the status bar is loading below the Ubuntu logo.  When the bar loads so that about 2.75 of the black units (that make up the bar) are orange, the installation stops and the computer goes silent (i.e., I no longer hear the CD spinning or any other sound from the computer).

I've run the "Check CD for Defects" option and it came back clean.  I've also tried the same CD on another computer, a 32-bit variety running Windows XP, and it loads Ubuntu just fine.

Any ideas on why a 64-bit installation CD would hang on a 64-bit system but not a 32-bit one?  I've also double checked the ISO file I downloaded to make sure it was the correct one (ubuntu-8.04.2-desktop-amd64, 696MB).

---

### Post by merlinus on 2009-06-11
When at the menu, press the key for booting options, and try adding noapic and nolapic to that line.

Otherwise, you might try the text-based alternate install cd.

---

### Post by PreviousN on 2009-06-11
You may try adding the noapic options to the grub menu. That might work for you. It didn't for me when I upgraded to Jaunty. Instead, I used the alternate install cd, which you can download here(x86_64): [http://mirrors.easynews.com/linux/ubuntu-releases/jaunty/ubuntu-9.04-alternate-amd64.iso](http://mirrors.easynews.com/linux/ubuntu-releases/jaunty/ubuntu-9.04-alternate-amd64.iso)

Also, here's a list of all the available install cds: [http://mirrors.easynews.com/linux/ubuntu-releases/jaunty/](http://mirrors.easynews.com/linux/ubuntu-releases/jaunty/)

After installing via the text only (alternate) installer, I was able to boot modifying the noapic option. But, for some reason, that didn't work on the regular live cd. 

Try the above option, first. You may have it work better for you.

---

### Post by izrafeel on 2009-06-11
Thank you both for your suggestions.  Using the Alternate CD sounds like a good way to go but I'm concerned about the noapic/nolapic parameters.

merlinus, are there any problematic issues I should be concerned about if I employ the noapic and nolapic options?  (By the way, how exactly would I do this?  I'm still new to Ubuntu.)  For example, would these options affect my graphics card?

PreviousN, you mentioned that you needed to set the noapic option even after installing your system.  Was this necessary for your system to function?  How did you go about it?

Seeing that the 64-bit edition loaded fine on a 32-bit CPU (i.e., the live CD), what would happen if a 32-bit edition were loaded on a 64-bit CPU?  In the *Absolute Beginner Talk* forum, there is a link to Keir Thomas' "Ubuntu Pocket Guide and Reference" ([here]("http://ubuntuforums.org/showthread.php?t=1052065")).  On page 8, he says the following: 

> 
**NOTE**    You  might  notice  that  a  64&#8208;bit  version  of  Ubuntu  is  
also available for download. In my opinion, there’s no need to use 
this,  even  if  you  have  a  64&#8208;bit&#8208;capable  CPU  in  your  computer, 
unless  your  computer  has  more  than  4GB  of  RAM.  The  64&#8208;bit  
version  of  Ubuntu  has  been  known  to  present  a  handful  of  
annoying  compatibility  issues  that,  while  not  show&#8208;stoppers,  can 
make life more difficult than it needs to be.  


Thoughts?

---

### Post by merlinus on 2009-06-11
At the opening menu there is an option for booting parameters, I believe F6.  Simply add noapic nolapic to the end of the line that appears.

If this works, then the change can be made permanent by modifying the /boot/grub/menu.lst file.

It will not do any harm to your system.

---

### Post by izrafeel on 2009-06-11
Seems like I got myself into some trouble here.  I used the Alternate CD to install 8.04.  I was able to proceed without changing anything related to apic.  Now, my system hangs when it's trying to boot.  

Would editing the boot options to specify noapic and nolapic help?  If so, how should I go about it?

---

### Post by merlinus on 2009-06-11
Can you see grub?  If so, press e, and then e again at the boot line and add those parameters, and then press b.   If it works, you can make it permanent.

---

### Post by izrafeel on 2009-06-11
Yes, I can access grub. When I do, I see three options:

```
Ubuntu 8.04.2, kernel 2.6.24-23-generic
Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.2, memtest86+
```

Pressing 'e,' takes me into the first option where I see the following four options:

```
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID= [...]
initrd /boot/initrd.img-2.6.24-23-generic
quiet

```

From here, pressing 'e' allows me edit this first option. I changed it to the following and tried to boot but no luck: 

```
root (hd0,0) noapic nolapic
```

---

### Post by merlinus on 2009-06-11
No, add them after quiet.

---

### Post by izrafeel on 2009-06-11
Still no luck.  I've tried making a new line after "quite" and booting with "noapic nolapic," "noapic" and "nolapic."  None of those work and the boot hangs in the exact same place for all three.

I appreciate your help.  If you have anymore ideas, please let me know.

---

### Post by merlinus on 2009-06-12
Try deleting quiet.  That should give messages about each step in the boot process, and you may be able to tell where it is hanging.

---

### Post by PreviousN on 2009-06-12
> 
PreviousN, you mentioned that you needed to set the noapic option even after installing your system. Was this necessary for your system to function? How did you go about it?

Seeing that the 64-bit edition loaded fine on a 32-bit CPU (i.e., the live CD), what would happen if a 32-bit edition were loaded on a 64-bit CPU? In the Absolute Beginner Talk forum, there is a link to Keir Thomas' "Ubuntu Pocket Guide and Reference" (here). On page 8, he says the following:

Quote:
NOTE You might notice that a 64&#8208;bit version of Ubuntu is
also available for download. In my opinion, there&#8217;s no need to use
this, even if you have a 64&#8208;bit&#8208;capable CPU in your computer,
unless your computer has more than 4GB of RAM. The 64&#8208;bit
version of Ubuntu has been known to present a handful of
annoying compatibility issues that, while not show&#8208;stoppers, can
make life more difficult than it needs to be.
Thoughts?

Let me elaborate: the noapic option for me, I don't remember how I did it. I've been traveling, and I'll get home in about a week and a half. If you still need the answer by then I'll check out my menu.lst and just post a copy to this forum. But, it can't hurt to try! When you edit your grub menu.lst before booting, you need to save before booting. You may be making the change, then not saving, then booting, giving you the same error. 

Also, it is my impression that some of these bugs have been fixed recently. So, I'm kind of surprised you are getting them. If this is your first go at linux, I'm sorry to hear you're having trouble getting it off the ground.

Anyways, about using the 64bit version of ubuntu: I choose x86_64 for my desktop because I *am* planning on adding more than 4GB of RAM. It does have its share of compatibility issues that I had to jump through that I didn't have to jump through on x86 (namely, in previous versions such as intrepid ibex 8.10: flash). Nowadays I don't have as much trouble, but sometimes I encounter a little challenge to overcome that I didn't have on x86. For example, running a popular (free as in TV, not as in beer) game called Urban Terror, requires some settings changed for 64bit. All around I would just say using 64bit is good, but finicky. If that makes sense.

The benefits of using x86_64, however, are useful to me as it helps speed up different services (mysql and apache come to mind). And I don't have to worry if I choose to double my RAM to 8GB in the future. I hear that now they have a way to install more than 4GB of RAM to x86 (through nasty kernel hacks), so that's not really even a benefit much more. I'm just going on what I've "heard" though, it may not be the real situation. I choose to go with x86_64 because I wanted to upgrade. Sooner or later we all have to move onto the "next big thing." And I like being an early adopter.  

So, let me get this straight. You used the alternate install cd, and it installed fine? Then you rebooted and got the same error? You may try the "recovery" mode. That boots showing the errors and output. Which would be nice to know, since we may be troubleshooting the wrong component. You may have a problem with you hard disk drivers/uuid settings.

Since I'm away from home right now I can't really look at my 64bit computer to copy the menu.lst for you. So I pulled this one off a "solved" ubuntu forums thread. This is how it should look like, as a matter of where the noapic should go:
```
title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash noapic
initrd /boot/initrd.img-2.6.20-16-generic
quiet
```

---

### Post by izrafeel on 2009-06-12
Thank you both again for your suggestions. I actually *did* make the mistake of not saving my boot edits early on but then I realized I needed to press "enter" instead of "esc" to commit the changes for the boot.  Everything I've posted so have has been with this in mind.

PreviousN, your description of the issues you've come across with the 64-bit edition sounds very much in line with Thomas' remarks.  My initial confusion though was whether my boot hang-up fell under the "show-stoppers" he mentioned.

Attached is a picture of the screen at the point the boot hangs when I selected the "recovery mode" boot option.  In comparing the two options in grub - regular vs recovery mode - the major difference appears to be that "quiet" is removed from the latter.

As for the error in the picture, it seems very clear that there's a hardware issue at fault.  I'm recommended to, "run through the mcelog --ascii to decode and contact my hardware vendor."  The laptop I'm using is new and came shipped with Vista, which worked fine if a bit slow.

The final line is somewhat humorous: "Kernel panic - not syncing: Machine check."

---

### Post by PreviousN on 2009-06-13
Hmmm. You know, I think I would be worried if it tells you there is a hardware problem. It does say "THIS IS NOT A SOFTWARE PROBLEM." But... before panicking, give the x86 version a try. 

The whole "menu.lst" editing and etc... is exactly the example of the finickyness of x86_64. Regular x86 usually "just works." 

At least for me.

---

### Post by izrafeel on 2009-06-16
Just to give an update on this case, I was able to get the 32-bit live CD for 9.04 up and running (I was previously trying to install the 64-bit version of 8.04).  However, when I tried to install the OS, it failed around 57% of the way through.  The cause was a write error to the hard drive.

Everything seemed to point to a problem with the hard drive.  The confusing thing though was the the laptop originally came with Vista which worked fine, if slow, on 2GB of RAM.  Further, the diagnostic tests available from the BIOS didn't reveal any problems with the hard drive.

I've since returned the computer to HP for an exchange.  Hopefully, I'll have better luck with the new one.

---

### Post by PreviousN on 2009-06-20
Here's a copy of my menu.lst

It seems I no longer have the noapic option on it. Sorry I couldn't be of much help...

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		de30c7f2-2b5b-4d3a-9087-e5d28f3cb0d6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


You may try using a different bootloader, such as extlinux or grub2. If that is something you'd like to try out, say so and I/someone else can detail instructions...

---

### Post by PreviousN on 2009-06-20
> **izrafeel said:**
> 
I've since returned the computer to HP for an exchange.  Hopefully, I'll have better luck with the new one.

I hope so too. Good luck!

---

