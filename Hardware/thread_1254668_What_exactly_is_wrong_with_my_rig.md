---
title: "What exactly is wrong with my rig?"
date: 2009-08-31
forum: Hardware
---

### Post by Mister LinOx on 2009-08-31
Okay, I ordered some parts off of Newegg last week and about a day after I got them, I started building, finishing up on Saturday. Everything was easy, going along just fine. Then when fixing the BIOS and getting ready to put an Ubuntu LIVE CD in, my knee hits the open tray. I thought nothing of it and went on.

Then I couldn't boot from disc to install, getting the error message "DISC BOOT FAILED, INSERT SYSTEM DISC AND PRESS ENTER" Getting frustrated, I automaticly assumed the Serial ATA HDD. Took it out, requestem RMA, and was going to ship it back today.

Yesterday I suddenly remembered the drive and opened the case back up. Took the drive out and replaced with an IDE drive in my previous PC. Works. Boot up the CD and after taking the steps (Language, Time Zone, Dvorak keyboard), I get to partitioning. 

Usually, partitioning is easy. . . When the HDD is detected! Nothing. Absolutely nothing is detected.

So now, I'm wondering, should I still send the HDD back for replacement? Did I do something while packing it in a box? Is there anything I can do to get it to work?

Side Notes: I know I have every thing plugged up correctly. The only doubt would be the PSU Serial ATA cable. It looks plugged in very good, but gave no click of assurance as the other did. I would like to settle this pretty quickly, but can still wait patiently as needed. :)  


Thank you in advance.

---

### Post by Yellow Pasque on 2009-08-31
Boot into the BIOS and reset to 'optimal defaults'. Then reboot into the BIOS and see if the hard disk is recognized. If you have it connected correctly and the BIOS can't see it, then you might have a bad drive, or maybe the mobo is having SATA issues (since it didn't like your CD drive either).

If the BIOS can see the drive, try the LiveCD again (maybe try different LiveCD's).

Also, what motherboard and hard disk did you get?

> The only doubt would be the PSU Serial ATA cable. It looks plugged in very good, but gave no click of assurance as the other did.
They don't click. If you can hear the drive running, then it has power. If you can't, then there's a problem.

---

### Post by LowSky on 2009-08-31
Go to BIOS and check the Sata cnnection, change it to IDE mode or legacy mode (depend on the manufacuter for naming convention, mine is legacy ide...especaially if the DVD-Rom is SATA powered.

---

### Post by Mister LinOx on 2009-08-31
@Temujin: I'm using a Gigabyte MA-770 UD3. The CD drive might have worked, but I kneed the tray really hard and it went lose. Also, I have normal/average defaults or something similar. EDIT: There are Failsafe and Optimized Defaults.

I can hear it when putting my head to the case. If it helps, it is a WD Caviar Blue 250GB.

@LowSky: Not sure how to check the Serial ATA connection. I know after connecting my old IDE drive, it says it's master under IDE settings. I do see, however, under Standard CMOS features or something it saying something about a drive A: with options. Like 1.44M 3.5" along with others. Underneath the IDE drives.

---

### Post by Yellow Pasque on 2009-08-31
Does the BIOS identify the hard disk?

---

### Post by Mister LinOx on 2009-08-31
> **Temüjin said:**
> Does the BIOS identify the hard disk?

Well, it doesn't identify it as a Western Digital 250GB. Under Normal CMOS Features, it has this:

'A: 1.44M 3.5" '  If I put the cursor on it and press ENTER, it gives me quite a few other choices. So I'm not really sure if it IS detected or not.

EDIT: Even after loading Failsafe Defaults, still not recognizing the HDD. Should I go ahead and RMA it? I have the RMA request accepted and set up. Only thing left in the process is to ship it.

---

### Post by Mister LinOx on 2009-09-01
So I think I'm just going to RMA it. Thanks you guys for trying though! :D

---

### Post by paulisdead on 2009-09-01
> **Mister LinOx said:**
> 'A: 1.44M 3.5" '  If I put the cursor on it and press ENTER, it gives me quite a few other choices. So I'm not really sure if it IS detected or not.
Haha, this made my day.  That's for if you have an old school floppy drive installed, so you can select what kind.

If you haven't done RMA's yet, you should try to determine the point of failure.  Try another sata drive and see if you can at least get it to detect.  It sounds like maybe it's the motherboard that's the problem, since it doesn't seem to be detecting either your hard drive or optical drive.

---

### Post by Whiffle on 2009-09-01
> **paulisdead said:**
> Haha, this made my day.  That's for if you have an old school floppy drive installed, so you can select what kind.

If you haven't done RMA's yet, you should try to determine the point of failure.  Try another sata drive and see if you can at least get it to detect.  It sounds like maybe it's the motherboard that's the problem, since it doesn't seem to be detecting either your hard drive or optical drive.

Ditto.  It should show your hard drive in your BIOS.  I would check and make sure all the SATA stuff is turned on, and that you have the SATA cable plugged into the right port on the motherboard (i have another motherboard that is picky about that).

---

### Post by Mister LinOx on 2009-09-02
> **Whiffle said:**
> Ditto.  It should show your hard drive in your BIOS.  I would check and make sure all the SATA stuff is turned on, and that you have the SATA cable plugged into the right port on the motherboard (i have another motherboard that is picky about that).

I mean, the CD drive would open up, but not read. Light would flash though, but no boot. So, how do I know which Serial ATA port to plug into? This is my Mobo, by the way: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128376](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128376)  with this being a shot of it: [Click.]("http://www.newegg.com/Product/ShowImage.aspx?CurImage=13-128-376-S03&ISList=13-128-376-S01%2c13-128-376-S02%2c13-128-376-S03%2c13-128-376-S04%2c13-128-376-S05&S7ImageFlag=1&Item=N82E16813128376&Depa=0&WaterMark=1&Description=GIGABYTE%20GA-MA770-UD3%20ATX%20AMD%20Motherboard%20-%20Retail")
[/URL]

The orange-like yellow ports are the Serial ATA ports. In the BIOS though, how would I check the Serial ATA connections or not? In the area with the IDE options and Floppy drive, I saw nothing about Serial ATA.

EDIT: Also, I don't have any other SATA drives. I have a drive in the temporary PC that I'm using, but it would be a pain to get out and it is IDE, which I know works.

---

### Post by Whiffle on 2009-09-02
There should be a section in your BIOS called "Integrated Peripherals", and in that there should be a couple of options for the Onboard SATA controller.  Make sure it isn't set to RAID, and that its enabled.  Also, your drives should show up under the "Standard CMOS Features" section.  It appears that SATA and IDE are both listed there.

---

### Post by linux_tech on 2009-09-02
> **Mister LinOx said:**
> Well, it doesn't identify it as a Western Digital 250GB. Under Normal CMOS Features, it has this:

'A: 1.44M 3.5" '  If I put the cursor on it and press ENTER, it gives me quite a few other choices. So I'm not really sure if it IS detected or not.

EDIT: Even after loading Failsafe Defaults, still not recognizing the HDD. Should I go ahead and RMA it? I have the RMA request accepted and set up. Only thing left in the process is to ship it.

You can download the seatools iso and create a boot cd to boot to and test the hdrive.  seatools will test pretty much any ide drive for errors.  Western digital also has some good tools and since the drive is wd, using the wd tools, you could also try a repair on the drive as well.

---

### Post by Mister LinOx on 2009-09-02
> **Whiffle said:**
> There should be a section in your BIOS called "Integrated Peripherals", and in that there should be a couple of options for the Onboard SATA controller.  Make sure it isn't set to RAID, and that its enabled.  Also, your drives should show up under the "Standard CMOS Features" section.  It appears that SATA and IDE are both listed there.

Okay. For the Onboard SATA controller, it was Enabled. For the type(?) it had Native IDE. Just trying different things, I set it to AHCI. When going back to Standard CMOS Features, the number of possible IDE drives did shorten to four, but nothing else. Then when booting up, not going into the BIOS, it says something about an AHCI controller or something.

---

### Post by Whiffle on 2009-09-03
> **Mister LinOx said:**
> Okay. For the Onboard SATA controller, it was Enabled. For the type(?) it had Native IDE. Just trying different things, I set it to AHCI. When going back to Standard CMOS Features, the number of possible IDE drives did shorten to four, but nothing else. Then when booting up, not going into the BIOS, it says something about an AHCI controller or something.

I'm looking at this:
[http://america.giga-byte.com/FileList/Manual/mb_manual_ga-_ma770-v.2.0_e.pdf](http://america.giga-byte.com/FileList/Manual/mb_manual_ga-_ma770-v.2.0_e.pdf)

and from pg 48 it looks like you might want to make sure the hard drive isn't plugged into either SATA2_4 or SATA2_5 connector, just to simplify things.  If it were me, I'd plug it into 0 or 1, whichever one is the first one.  It also looks like AHCI or Native IDE should be just fine.  I'd double check those connections and make sure that you've got power to the drive.  If all that checks out, I'd start looking into the drive itself as the culprit, or the motherboard.

---

### Post by Mister LinOx on 2009-09-05
> **Whiffle said:**
> I'm looking at this:
[http://america.giga-byte.com/FileList/Manual/mb_manual_ga-_ma770-v.2.0_e.pdf](http://america.giga-byte.com/FileList/Manual/mb_manual_ga-_ma770-v.2.0_e.pdf)

and from pg 48 it looks like you might want to make sure the hard drive isn't plugged into either SATA2_4 or SATA2_5 connector, just to simplify things.  If it were me, I'd plug it into 0 or 1, whichever one is the first one.  It also looks like AHCI or Native IDE should be just fine.  I'd double check those connections and make sure that you've got power to the drive.  If all that checks out, I'd start looking into the drive itself as the culprit, or the motherboard.

Good news. I looked up "SATA drives not working on GAMA770 UD3" and I found a guy with my problem.

What it was is a standoff in the wrong place actually grounding my Serial ATA ports. A simple re-build and replaced standoffs fixed it. I'm now using the PC. CD drive works too.

Thank you guys for helping. I would've RMAed it by now. 

Now my only problem is a 50KB or less download speed for some reason.

---

### Post by Whiffle on 2009-09-05
> **Mister LinOx said:**
> Good news. I looked up "SATA drives not working on GAMA770 UD3" and I found a guy with my problem.

What it was is a standoff in the wrong place actually grounding my Serial ATA ports. A simple re-build and replaced standoffs fixed it. I'm now using the PC. CD drive works too.

Thank you guys for helping. I would've RMAed it by now. 

Now my only problem is a 50KB or less download speed for some reason.

Ah yes those pesky standoffs.  Lucky it didn't do any damage.

---

