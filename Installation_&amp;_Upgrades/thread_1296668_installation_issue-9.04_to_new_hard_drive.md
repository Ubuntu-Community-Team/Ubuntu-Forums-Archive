---
title: "installation issue-9.04 to new hard drive"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by McCracker on 2009-10-20
hello all, i'm new to this site, and linux in general. sorry if this ends up a bit long, but i thought it prudent to give the full background. i've never been a &quot;computer person&quot;, but i bought a new laptop(gateway t-6345u-running vista premium) a few months ago and started learning stuff. i was intending to try linux on a separate older laptop, just for fun. then my new laptop crapped it's hard drive. gateway's customer support is ATROCIOUS, so i decided to deal with it myself. bought a new hard drive-wd scorpio blue 250gb 5400 sata. installed it and decided to just run ubuntu by itself. burned a disc on a friend's computer, turned out perfect. ran it as a livecd, everything works PERFECTLY, including wifi, i love it so far. choose full installation. everything went smoothly, until....it finishes. i get the full desktop, everything works, but i never get any reboot prompt. i messed with it for a bit, shut it down, and rebooted without the cd. i get the standard gateway splash with bios/boot menu options, then it goes to the Dreaded Blank Screen With Upper Left Blinking Cursor. i can do nothing from this point, except power off. i've reinstalled several times trying different options, i.e. acpi-off, safe graphics mode, etc., but i get the same result every single time. it's like it's not fully installing. after install(with the cd still in the drive) it shows the os on my hard disk and it's related partition(s), but when i reboot and chose to reinstall it shows &quot;there are no operating systems on this computer&quot;. also, i get random error alerts that always say &quot;the report belongs to a package that is not installed&quot;. any help? i loathe the thought of returning to windoze. tia!

---

### Post by KhanTG on 2009-10-20
Did you use the CD test (one of the options on the live CD when it boots), you might have a bad disc. Also, are you going straight to Install or are you running the CD live first? sometimes that has made a difference when I installed on various machines (don't know why, sometimes OEM install works... other times normal install works ... same CD)

---

### Post by McCracker on 2009-10-20
wow, quick reply! i did check the cd for defects, i had made two cd's on my friend's desktop pc(just in case, as my laptop is my only computer), one turned out to have two defects, the other was fine-tested it several times. i have not tried installing it while running the cd, i'm assuming you mean using the install shortcut that lives on my desktop? i'll try that right now, see what happens and report back. i'm running off the livecd as i type this, but it would be nice to get it properly installed. thanks!

> **KhanTG said:**
> Did you use the CD test (one of the options on the live CD when it boots), you might have a bad disc. Also, are you going straight to Install or are you running the CD live first? sometimes that has made a difference when I installed on various machines (don't know why, sometimes OEM install works... other times normal install works ... same CD)

---

### Post by McCracker on 2009-10-21
hmmm, so i tried installing from the desktop icon-both regular install and "oem install". it goes ok at first but freezes at the 5% install mark where it is setting up the ext3 partition for several minutes then bounces back to the livecd desktop and kicks up the same error message about the package that is not installed. i'm not sure what to do about this...

---

### Post by KhanTG on 2009-10-21
Are you manually setting the partitions or letting the computer "Use Entire Disk"?  I'm just 'spit-balling' here, btw. You might have a bad HDD, can you access it OK when you are using the live CD? if you can then try using gparted to delete all partitions on your target HDD and start from a RAW disk.  If your CD is good the the only thing that I can think of being the issue is the HDD.  Anyone else out here have an opinion?

---

### Post by McCracker on 2009-10-25
figured i'd throw this out there to save someone a headache. after a bunch of messing around, i decided to just burn another copy(for the third time). cruised back over to my buddy's place, burned yet another iso dvd and VOILA! the self check kept showing that the 2nd disc i made was fine, but it would not fully install. 3 was the magic number, i guess. went perfectly and everything works great. i'll be sticking with linux, thankyouverymuch....

---

### Post by chkneater on 2009-10-25
I would chalk this up to MMD5 hash. Did you check the hash of the ISO after you DL'd it?

---

### Post by KhanTG on 2009-10-25
> **McCracker said:**
> figured i'd throw this out there to save someone a headache. after a bunch of messing around, i decided to just burn another copy(for the third time). cruised back over to my buddy's place, burned yet another iso dvd and VOILA! the self check kept showing that the 2nd disc i made was fine, but it would not fully install. 3 was the magic number, i guess. went perfectly and everything works great. i'll be sticking with linux, thankyouverymuch....

GREAT News!  Welcome to the family ;)

---

