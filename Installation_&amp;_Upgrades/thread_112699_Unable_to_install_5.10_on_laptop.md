---
title: "Unable to install 5.10 on laptop"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Dr. Blues on 2006-01-04
i am trying to install 5.10 onto a dell CPx with a 500mhz pentium ii. i changed the boot drive to the cdrom; powered up and i get zip...i mean nothing happens. cd is spinning but nothing on the screen but the cursor. am i missing something here?

tia

cioa...dr. blues

---

### Post by noeluylee on 2006-01-04
Have you tried using other 5.10 installation disk? the disk might be damaged.  I had many workstation/ laptops installed with 5.10 including twinhead and clone laptops and I didn't encounter such issue. changing your installation disk might solve your problem...  :)

---

### Post by bikeboy on 2006-01-05
Have you successfully burnt an iso onto CD before? It's not as simple as just burning the file onto the disk, you have to write it as an image.

---

### Post by xsnslaine on 2006-01-05
i have had the same issue, there are many reports that this is an issue with 5.10, i have the same problem, apparently 5.04 will work ok

---

### Post by Dr. Blues on 2006-01-05
[QUOTE=bikeboy]Have you successfully burnt an iso onto CD before? It's not as simple as just burning the file onto the disk, you have to write it as an image.[/QUOTE]


bikeboy i think you've nailed it! a search revealed this:

Q:I downloaded the Warty .iso file and burnt it to a CD, but can not get it to boot. When I reboot, the system says "Booting from CD..." then "failure" and proceeds to boot from harddrive.

A:You probably have recorded the .iso file to CD as a file, not as a CD image. The .iso file is a CD image and needs to be recorded as such. If you burn it as a regular file, the resulting CD will not work. Try opening the CD in any computer. You should see a few files and directories. If you see "ubuntu-warty-xxxxx.iso" as the only file in the CD instead, you haven't correctly created the CD. Look for the 'Write CD image' or similar option of your favourite CD creation program and use it to record the .iso file to CD. Reboot and enjoy :)

the cd i burnt has only the one iso file. will re-burn it as a cd image and report back.

obviously i shoulda done the search first. thanx!

ciao...dr. blues

---

### Post by Dr. Blues on 2006-01-05
cheers!
ubuntu is up and running! had a little glitch partitioning the hd, but otherwise it went straight away...wiped an xp pro installation and made the whole thing ubuntu. now i need to learn how to set up the pcmcia modem so i can get online with it.

ciao...dr. blues

---

### Post by bikeboy on 2006-01-06
[QUOTE=Dr. Blues]cheers!
ubuntu is up and running![/QUOTE]

Good to hear Dr. Blues. I haven't got any experience with pcmcia modems so I can't help you there. Have had no problems with my pcmcia wireless card though...apart from the lack of a linux driver for it.

---

### Post by xsnslaine on 2006-01-06
[QUOTE=Dr. Blues]cheers!
ubuntu is up and running! had a little glitch partitioning the hd, but otherwise it went straight away...wiped an xp pro installation and made the whole thing ubuntu. now i need to learn how to set up the pcmcia modem so i can get online with it.

ciao...dr. blues[/QUOTE]

how you get past the partitioning problem? my installed just hangs, im clearing the whole drive for just ubuntu.

any ideas?

---

### Post by Dr. Blues on 2006-01-06
i think my problem with partitioning the hd was i didn't understand all the options and terminology. initially i tried the some various LVM, VG options; that's where i got hung up. fortunately(?), i had to go to work, so i aborted the installation. when i picked later on, i chose "erase entire disk leaving x GB of free space". then i let installation suggest a partitioning. i accepted the suggested partitions and the installation when smoothly after that. ymmv.

important to note, i intended to wipe the (hated) xp pro; i didn't wipe it to get the installation to run. if you want to preserve a wind*ws installation, then you need to ask someone else.

get me...on this forum 2 days and already i'm giving advice!
anyway hth.

ciao...dr. blues

---

### Post by Dr. Blues on 2006-01-06
ooorah!
i'm on a roll. sorted the installation yesterday and today i got the modem functional: this is my first online foray using my linux laptop.

ubuntu is the bomb!

ciao...dr. blues

---

### Post by xsnslaine on 2006-01-17
i dont know if this is related, what i was trying to do was install over a windows XP partition and ubuntu was failing .. 

i installed linspire and that went though ok, i then tried the ubuntu install again and it worked no problems ....

could it have a problem removing XP partitions?

---

