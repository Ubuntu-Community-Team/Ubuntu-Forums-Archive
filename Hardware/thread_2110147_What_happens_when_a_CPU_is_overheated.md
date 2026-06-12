---
title: "What happens when a CPU is overheated?"
date: 2013-01-29
forum: Hardware
---

### Post by jhilp on 2013-01-29
I'm working on an older HP Pavilion laptop with an Intel Celeron processor. The guy who owns the laptop says it's been getting hot on the bottom below the processor for a long time, but he didn't do anything about it because he figured it was just a bad fan design or something. Anyway, I was using it steadily for about 3 hours last night, trying out, uninstalling, and reinstalling 2 different Ubuntu versions. Finally, I was just about to install some updates when the mouse cursor quit moving. I finally had to remove the battery to shut it down, and noticed that the processor was very, very hot. I took the cover off where the heatsink is and found that every hole where the air should blow through was packed with dust. I cleaned it up and left it shut off all night. Since then, I can't get it to boot up either from the hard drive or a disk. The HP startup screen comes up, and I can get into the BIOS with no issues, but it won't boot to the operating system. The screen just goes black and stays there. Is it likely that the CPU overheated and fried so bad that it's no good? Would the BIOS still work if that was the case? I'm just an ameteur.  Thanks!

---

### Post by Bucky Ball on 2013-01-29
Welcome to the forums.

Is it overheating when you switch it on still? Even just at the BIOS screen? 
Is the fan still working?
Can you hear the hard drives spinning?
Can you boot from a Ubuntu LiveCD, the one you install from? Will that get you to a desktop?
Lastly, and it may sound dumb; are you totally positive it was around the CPU that was getting hot?

---

### Post by ahallubuntu on 2013-01-29
An overheating CPU can damage the motherboard and/or nearby components over time.  Excessive heat is very bad for computers.

The CPU hasn't failed if you can enter BIOS Setup.  If the CPU had failed, you would not see anything on the screen or be able to do anything.

Can you boot a live CD or live USB?  A failed hard drive seems more likely to me.  Can you test the drive's S.M.A.R.T. status?  You can do that from Ubuntu by installing GSmartControl (even on a live CD) and then checking the Attributes.  Any Attributes highlighted in pink?

Try removing the hard drive entirely and see if you can boot a live CD/USB.  A completely dead hard drive can cause the motherboard to freeze trying to access it when trying to boot anything.  Or, remove ALL discs and USB from the computer and see what happens.  Of course, it's also possible the motherboard itself is failing.

---

### Post by furything on 2013-01-29
I have been told but never able to do it myself that you can get the BIOS to boot without a cpu installed (don't believe it personally).

Did you try booting from live cd as recommended???

If you cannot boot from cdrom you might be able to clear the cmos and reset things. Google for motherboard manual and find if it has a cmos jumper. Then close the jumper (you will probably have to open case up again to get to jumper).

If it BIOS boots you will probably have to enter BIOS and tell it to set to defaults.

If you still cannot boot then I would suspect the chip is cooked. Normally resetting the BIOS works for me in this sort of situation

---

### Post by Bucky Ball on 2013-01-29
Yep, CPU can kill other components when overheating regularly even if it doesn't suicide itself. The high temperatures inside the case could have done this anyway.

---

### Post by Thee on 2013-01-29
If you can enter the BIOS, then you can see exactly what is working and what is not. There you will find if it detected the processor right, RAM, hard drive, etc... from there you will know more whats going on.

BTW, when processor overheats, the system should shutdown automatically, but when the hard drive overheats it wont shutdown, it will freeze like it did, and probably die if it was too much. So my best guess is that your HDD is dead.

---

### Post by tgalati4 on 2013-01-29
It's possible that your graphics chip got fried.  It will work in low-graphics, text mode, but when trying to paint 2D or 3D graphics it will just freeze up.  Can you boot into a Live DVD rescue shell (text only)?  That would be a good indication.  When the graphics chips get too hot, they warp and delaminate from the motherboard.  Repair is difficult and usually not successful.

---

### Post by jhilp on 2013-01-29
> **Bucky Ball said:**
> Welcome to the forums.

Is it overheating when you switch it on still? Even just at the BIOS screen? 
Is the fan still working?
Can you hear the hard drives spinning?
Can you boot from a Ubuntu LiveCD, the one you install from? Will that get you to a desktop?
Lastly, and it may sound dumb; are you totally positive it was around the CPU that was getting hot?
It's not overheating now. The fan is still working. I think I can hear the hard drive spinning. I did a quick test and a comprehensive test on the hard drive from the BIOS, and it checked out fine. Nothing happens even when I try to boot from a live CD. It is definitely the CPU that got hot. Thanks!!

---

### Post by jhilp on 2013-01-29
> **ahallubuntu said:**
> An overheating CPU can damage the motherboard and/or nearby components over time.  Excessive heat is very bad for computers.

The CPU hasn't failed if you can enter BIOS Setup.  If the CPU had failed, you would not see anything on the screen or be able to do anything.

Can you boot a live CD or live USB?  A failed hard drive seems more likely to me.  Can you test the drive's S.M.A.R.T. status?  You can do that from Ubuntu by installing GSmartControl (even on a live CD) and then checking the Attributes.  Any Attributes highlighted in pink?

Try removing the hard drive entirely and see if you can boot a live CD/USB.  A completely dead hard drive can cause the motherboard to freeze trying to access it when trying to boot anything.  Or, remove ALL discs and USB from the computer and see what happens.  Of course, it's also possible the motherboard itself is failing.
I tried booting from a live CD, and nothing happened. I ran a quick test and comprehensive hard drive test from the BIOS, and it checked out fine. Would you still suspect the hard drive if it tests OK?

---

### Post by jhilp on 2013-01-29
> **Thee said:**
> If you can enter the BIOS, then you can see exactly what is working and what is not. There you will find if it detected the processor right, RAM, hard drive, etc... from there you will know more whats going on.

BTW, when processor overheats, the system should shutdown automatically, but when the hard drive overheats it wont shutdown, it will freeze like it did, and probably die if it was too much. So my best guess is that your HDD is dead.
I ran a full check on the hard drive. Would you agree that the hard drive is OK if it checked out good on a test from the BIOS?

---

### Post by ahallubuntu on 2013-01-29
> **jhilp said:**
> I ran a full check on the hard drive. Would you agree that the hard drive is OK if it checked out good on a test from the BIOS?

Not necessarily.  Still, it sounds like the hard drive isn't completely dead.

Can you remove the drive and see what happens?  Can you then boot from USB or CD?  Or does anything change?

---

### Post by jhilp on 2013-01-29
> **ahallubuntu said:**
> Not necessarily.  Still, it sounds like the hard drive isn't completely dead.

Can you remove the drive and see what happens?  Can you then boot from USB or CD?  Or does anything change?
I'll try it when I get home from work this evening. Thanks for the help!

---

### Post by jhilp on 2013-01-29
> **ahallubuntu said:**
> Not necessarily.  Still, it sounds like the hard drive isn't completely dead.

Can you remove the drive and see what happens?  Can you then boot from USB or CD?  Or does anything change?
But I did try booting from a live CD with the hard drive still hooked up, and nothing changed.

---

### Post by Thee on 2013-01-29
Sometimes a faulty hard drive can cause a computer to not boot at all, as long as its connected to the motherboard. So remove it like suggested, and then try to boot a live CD.

---

### Post by tgalati4 on 2013-01-29
It's time to take the machine apart, clean it, and reseat all of the cables.  Note the different screw lengths.  Look for signs of overheating--brown spots on the motherboard, and bulging or leaking capacitors.  If it still won't boot after cleaning/reseating, then it's time to take the parts you want, put the drive in an external USB enclosure (to recover any data) and put the rest up on craigslist for sale.

---

### Post by Yellow Pasque on 2013-01-30
memtest...

---

### Post by jhilp on 2013-01-30
It turns out the CPU wasn't bad after all.  It was a bad Lubuntu install.  The disk was also bad, which is why it wouldn't boot from the disk.  Thanks for all the help!

---

### Post by Bucky Ball on 2013-01-30
Please mark as Solved from Thread tools to help others if you feel your issue is. Thanks.

---

