---
title: "External install for Internal Boot (Presario M2000, 9.10)"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Chi The Designer on 2009-10-22
Hello fellow ubuntu-members.
I have, once again, a question.

[I]I used to be the guy prodding around with the PXE boot on my laptop, but that's never going to work. So I decided to try something else:
[/I]
I had a laptop that worked fine with XP, until XP started acting weird. Installed ubuntu. Was happy. Then somebody installed XP over it. Killed everything. Had to clear CMOS and the laptop restarted. Now the laptop says:

**"Operatig System Not Found".**

Now the laptop does not boot from USB and the DVD drive is broken. I can't seem to order a new dvd drive, since it needs a certain type and only reacts to that one.

So I bought a 2.5'' External HD Enclosure and installed the HDD from my laptop in there. Plugged it into another PC and the drive was fine, even made backups *(hey!)*. So the drive is just working fine, I can even use it as a External HDD at this point.

[B]IDEA:

Is it possible to install Ubuntu on my 2.5'' Ext. HDD using the live CD (or boot from PC) on my 2nd PC, then unplugging the HDD when setup is done, put the 2.5'' HDD back into my laptop and run Ubuntu on my laptop which brings my laptop back to life? 

Will that work?[/B]

And if Ubuntu couldn't do that, would Windows or Mac be able to do that? I'm really running down the last stretch here, don't know what else to do and I feel like this laptop could still be used for some coding, hehe.

Hope someone can help me out!

---

### Post by Zavior on 2009-10-22
You could do a "persistent live install." This means that the install can be run (potentially) from any computer. The persistent part means that changes you make to the OS stay, or are persistent. Easiest way to do this:

1. Plug the drive into another computer 
2. Boot from the Ubuntu Live CD
3. Go to "System > Administration > USB Startup Disk Creator"
4. Follow the onscreen instructions installing Ubuntu Live to your usb HDD

This will create a live install on the Hard drive. After that you should be able to put it back into the laptop and boot up Ubuntu Live. The live option is a little messy... It probably won't run as well as a normal install (you'll especially notice a lot longer startup times). You *might* be able to do this (I'm not sure about this):

Repeat steps 1-4 but install ubuntu live to a small partition at the end of the drive. Put the drive into the laptop. Start Ubuntu live on the laptop. Use this to install a regular install to to the front of the drive. If all goes well you can then delete the Live partition at the end of the drive and your good to go... maybe... I don't know if that would work or not.

---

### Post by Chi The Designer on 2009-10-22
> **Zavior said:**
> You could do a "persistent live install." This means that the install can be run (potentially) from any computer. The persistent part means that changes you make to the OS stay, or are persistent. Easiest way to do this:

1. Plug the drive into another computer 
2. Boot from the Ubuntu Live CD
3. Go to "System > Administration > USB Startup Disk Creator"
4. Follow the onscreen instructions installing Ubuntu Live to your usb HDD

This will create a live install on the Hard drive. After that you should be able to put it back into the laptop and boot up Ubuntu Live. The live option is a little messy... It probably won't run as well as a normal install (you'll especially notice a lot longer startup times). You *might* be able to do this (I'm not sure about this):

Repeat steps 1-4 but install ubuntu live to a small partition at the end of the drive. Put the drive into the laptop. Start Ubuntu live on the laptop. Use this to install a regular install to to the front of the drive. If all goes well you can then delete the Live partition at the end of the drive and your good to go... maybe... I don't know if that would work or not.

Thanks loads for the quick reply! I was actually thinking of something like that, and the "Live Partition" -> Regular install seems like it would work. Thank you, I will try it right now. :)

Be back in a flash!

---

### Post by Chi The Designer on 2009-10-23
Zaviour, thanks. You really do your name honor.
After a lot of fiddling I have finally found a second life in my laptop.

I used the technique you told me, where I insert a Live CD in the PC and install USB Flash Startup on my Notebook HDD. I then inserted it into my Notebook and I could boot into the Live CD version on my HDD. Nice. 

However, I tried doing a full install from the disk onto the disk afterward, but it would not let me. So that leaves me to think..

**> #1 <**

I have 9.10 on a 4GB USB Key as well. I have no DVD Drive nor USB boot, so I have limited resources - but **is it possible to use an internal HDD to boot from USB?** I know there is a way out there to boot from USB using a CD, but I have never heard of an HDD doing that? 


If so, I could let my HDD boot the USB, after which I could use the USB to install the 9.10 on my HDD on the laptop! That would be great in theory, but I do not know if any such a thing can and will work, and what the proper files would be to do so.


**> #2 <**

If that can not or will not work, I have a 2nd 2.5'' IDE HDD lying around here. If I boot my current HDD into Live Mode, put my second HDD in the USB Enclosure and then install Ubuntu 9.10 on the 2nd drive.. I should be able to put that 2nd drive in the laptop and have a full install on my laptop, right?

I just wanted to know because if the USB thing doesn't work out I have an option to get to the full install. :)


So do you have an answer to those questions?
Thanks again!

---

### Post by Zavior on 2009-10-23
I would suggest going with the second option. You could probably do the first but it would be a lot more hassel than the second I'm guessing. Yeah, try the second option first. Boot from the internal drive you've got the live on, do a normal install to the second in the usb enclosure, then swap the two drives. 

Two things I'd keep in mind if you try this:
1) make sure to install the bootloader to the 2nd (ie the USB) hard drive. This will ensure that when you put it into the laptop you'll be able to boot it. I'm guessing the default for the installer would be to put the bootloader on the internal drive, so make sure you check.

2) If you would prefer to have Ubuntu installed on the 1st HDD, repeat the steps to make the second a live install, put it into the laptop and the 1st into the eclosure and go from there. Basically switch the drives. I don't know if you care which one you end up with the Ubuntu install on.

Good luck! Let me know how it goes.

---

