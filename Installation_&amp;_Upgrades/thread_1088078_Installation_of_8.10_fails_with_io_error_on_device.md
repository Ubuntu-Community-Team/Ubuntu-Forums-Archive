---
title: "Installation of 8.10 fails with i/o error on device sr0,logical block"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by dverhoeven on 2009-03-05
Hi, I found many posts so far but no solutions, so here is what happened to me.
System:
Gigabyte GA-EP45-DS3R motherboard
Gigabyte GV-R485MC-1GB radeon 4850 video 
Intel core duo E8400
8 Gb Kingston
WD caviar GP 500 GB HD 16 MB 7200 RPM

Installing 8.04 64 bit succeeds after some initial issues (see [http://ubuntuforums.org/showthread.php?p=6845191#post6845191](http://ubuntuforums.org/showthread.php?p=6845191#post6845191))

8.10 64 bit remains giving me the same failure as in the title of the topic (both when I try to start as live CD as when I try to install). Even after reburning at low speed (from windows XP 64 bit that runs fine on the system)

I unhooked all devices, except my HD an I connected a IDE CD RW instead of my  sata one. I tried my HD on different sata ports, but no luck so far.

I would appreciate if someone could give me a hint on how to get this puppy dancing.

---

### Post by Dallywood on 2009-03-06
Did you burn the install cd yourself?
I found that when I did I got the same error until I used the program cdburnerxp (free to download).I was using isoburner before that and the discs it made gave me that error. 
The only thing is that under burn iso options subheading burn method I needed to select "Disc at once" and not the default selection "Session at once."

---

### Post by dverhoeven on 2009-04-18
Hi,after not doing anything with it for a while finally solved it based on a post I found on the net.

The solution is very simple : burn the image to DVD instead of CD. Go figure :-)

Some details : CD burner : Samsung SH-S223F DVD±R/RW DL
initial disk that failed : Philips CD-R80 52X 700 Mb
disk that was successfull :philips DVD+RW 1-4X

To be complete I tried a number of other things, like unhooking my HD from the cable it shared with my DVD, and tried a live cd run. This failed.
Various settings when starting up.
Various other CD's (all checked if they were burned correct)
Knoppix (alos failed)
Ubuntu 8.04 and 9.04 (also fail)

So for those suffering from the same, I suggest to try a burn to DVD.

ps: i did not try the solution above, which might very well work, as I do use cdburnerxp, but I did not use this selection. As I am out of CD's I can not try it anymore.

---

