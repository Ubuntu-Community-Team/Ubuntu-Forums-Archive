---
title: "Samsung N150 netbook: no boot options in the BIOS?"
date: 2010-04-24
forum: Hardware
---

### Post by JC Cheloven on 2010-04-24
Hi, I'm really confused.

I just had a brand new specimen of that netbook at hand, and of course tried to see how does ubuntu works on it. Plugged my usual ubuntu usb stick, turned on, and stroke F2 to enter the BIOS. 

To my surprise, in the "boot" section of the bios, appeared some silly options (about what I'd like to see at startup), but no actual options to boot from external usb/cd/whatever. Thus I have been unable to even ask the computer to boot from usb. In fact, I don't figure out how to install any OS apart from the branded one (guess: W7 starter).

Anyone knows what is this about?

---

### Post by JC Cheloven on 2010-04-25
Bump. 
Really worried here. Is it a new threat to the user's freedom? 
Perhaps manufacturers gave up due to corporate pressures, and the ability to boot from external devices will disappear from bios-es? 

That would be very serious, indeed. But I don't find a mention anywhere :confused:

---

### Post by d-wizzle on 2010-04-28
Hi JC,

I'm thinking of buying one of these today. I did a bit of Googling and found this:

[http://printer1.blogspot.com/2010/03/samsung-n150-user-manual.html](http://printer1.blogspot.com/2010/03/samsung-n150-user-manual.html)

which has instructions on changing boot priority.

When I'm in the shop today I'll have a go before I buy!

Regards,

d-wizzle

---

### Post by trig on 2010-04-28
Read this, and see if it shead any light on your situation.
[http://www.linuxquestions.org/questions/linux-newbie-8/install-linux-on-netbook-that-will-only-boot-from-hard-drive-793505/](http://www.linuxquestions.org/questions/linux-newbie-8/install-linux-on-netbook-that-will-only-boot-from-hard-drive-793505/)

---

### Post by JC Cheloven on 2010-04-28
Ufff... my worries increase.
To contextualize the situation: I've made perhaps 100 installations over 50+ computers of all kinds in the last 3 years. I think I'm facing something unseen before. As I said, only a few stupid options are present in the boot section of the bios.

@ d-wizzle
Please get informed on the boot abilities of your N-150 before you buy! I saw the instructions you pointed me (btw, in a win-executable format, aggg!). My bios doesn't look like this. I have no boot-priority-order, or anything like that. The manual itself states that bios are subject to change without notice, and depend on the model... 

@ trig
Thanks for the link. Again little to do with my situation. Their bios show at least an option. 

I wonder if it's just in the spanish market. I think I'll post in the cafe to see if someone has seen this.

---

### Post by d-wizzle on 2010-04-30
Hi JC,

I did buy one, and the BIOS is as it appears in the manual.

Sorry to hear you're still having trouble. You could try updating the BIOS: I found this on the Samsung website - 

[http://www.samsung.com/sg/consumer/detail/support.do?group=pc-peripherals-printer&type=notebook-pc&subtype=n-series&model_nm=NP-N150&language=&cate_type=all&mType=FM&dType=D&cttID=2694799&prd_ia_cd=05081200&disp_nm=N150&model_cd=NP-N150-JA05SG&menu=download&menu2=detail](http://www.samsung.com/sg/consumer/detail/support.do?group=pc-peripherals-printer&type=notebook-pc&subtype=n-series&model_nm=NP-N150&language=&cate_type=all&mType=FM&dType=D&cttID=2694799&prd_ia_cd=05081200&disp_nm=N150&model_cd=NP-N150-JA05SG&menu=download&menu2=detail)

which was posted today. 

Regards,

Dom.

---

### Post by cariyawa on 2010-12-03
Since you posted this before couple of months ago, I hope you have figure out the solution..but if you haven't.. you may want to read this. 
I recently got a samsung n-150 and had the same problem that you have..No boot option setup....The answer is you have to select it and "Press Enter key".. then you will have the boot order setup dialog box. It is kind of confusing, because none of the other options/selections don't use enter key.

---

### Post by dsfitzpat on 2010-12-21
I just picked up one of these for my brother.  Have you tried hitting Esc at startup?  That brought up a screen for me where I could select to boot from USB.  Sadly however it doesn't seem to be possible to boot from an SD card, or even from an SD card connected to USB via an adapter (I have an eeePC that boots from the card reader just fine).  So although I can't use any of the live images I have on various SD cards, there was no problem booting from a USB drive once I tracked one down.

---

### Post by Mortifis on 2011-01-31
Hey, just saw this post.  Okay, you don't use the F2 key to access the Bios Setting on the Samsung N150 you use the ESC key just as it starts up (gotta be quick)  You'll be presented with Boot menu.  This is not the same Boot Manager Menu you get when you F2 at boot. If you have a bootable USB stick, USB HDD or other bootable USB device it will be in the list.  One option is ENTER SETUP.  Cursor down and select that and you'll find your familar BIOS Setup Utility.  Cursor to BOOT and the first highlighted option is Boot Device Priority.  Select that.  Use F5/F6 to put the USB HDD device as the first option.  If there is no USB stick the the port is will say N/A.  At any rate, make sure it is the 1st option.  F10 and reboot with your Ubuntu (or any other bootable OS) stick in the USB port and/or press the ESC. Select your Boot device and have at 'er.
 
Hope this helps
 
~Mortifis  :guitar:

---

### Post by regebro on 2011-03-05
I have boot order options in my N150 bios setup, with loads of USB options. You need to have a USB key inserted before boot, it seems.

Didn't try the ESC way, which seems easier.

---

