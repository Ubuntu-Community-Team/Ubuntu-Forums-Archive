---
title: "Breezy annoyances"
date: 2005-11-13
forum: General Help
---

### Post by PereUbu on 2005-11-13
After doing a fresh Breezy-install, which went just fine, I have these problems:

My keyboard layout switches back to english every time I reboot. I have to do the 'setxkbmap' command every time I log in to my computer.

My system freezes for a few seconds and something is trying to access my cd-romdrive (my cd-rom goes klik-klik, just like when you insert a cd). This starts after about 1 hour uptime, and repeats every second minute or so. Very annoying, indeed.

My HP DJ845C printer only prints in magenta!!!! Very good for love-letters ;), but for other purposes it's useless. 

Hopefully someone out there have some good advice!

Best regards
PereUbu

---

### Post by PereUbu on 2005-11-13
Hi again

My Breezy install seems to be born under a bad star :( 

As I mentioned before my cd-burner is bugging me, but now it goes crazy. It seems like it want to burn something, but it can't because there is no cd in it. The red lamp is blinking and it makes a lot of noise. I really have no idea why it is behaving like this :confused: 

Ubuntu automagically mounted my fat32 partitions, but I can't get write access to it. My fstab-entry goes like this:
/dev/hda5       /media/hda5     vfat    defults        0       0

I changed it to:
/dev/hda5       /media/hda5     vfat    user,uid=1000        0       0

but that didn't help either. 

Mozilla Thunderbird can't read my mailboxes on my vfat partition. I get an message that says it is processing my mailbox. But nothing happens, it can go on for hours............................

With all these problems to get simple things to work, I'm longing back for  good old Hoary, which worked right away. I'm beginning to loose faith in you, Breezy. Any help out there?

---

### Post by kosmic on 2005-11-13
ok, I think you should reinstall breezy, just re-download the Breezy Install CD or DVD and install, when you get to the partition wizard format the Ubuntu partitions so there's no data there, and after you do a fresh install please tell me if the problems still occurs to you.

---

### Post by fergus on 2005-11-13
in order to get write access to your fat32 partitions you should try adding a umask option to fstab.  Not sure what the exact syntax is offhand but you should be able to find something if you search for it..  worth a shot..

---

### Post by Juzz on 2005-11-13
Did you try a:

dpkg-reconfigure locale

?

---

### Post by Wally68 on 2005-11-13
To get write access for vfat change your /etc/fstab from:
/dev/sda4       /media/sda4     vfat    defaults        0       0
to:
/dev/sda4       /media/sda4          vfat    iocharset=utf8,umask=000    0 
But given the problem with the cdrom and printer you should reinstall breezy first.

---

### Post by PereUbu on 2005-11-14
Thanx a lot for your info!

I have checked the MD5-sum for the iso-file I burned for my Breezy and it is OK.
I will give it one more shot, and see if your good advices will solve my problems, before I reinstall.

BTW: I have found out that my cd-burner is sick and dying (it behaves badly when I let it stay in the GRUB-menu, and not boot into linux). In other words it's a hardware problem and has nothing to do with linux or Ubuntu. 

Greetings from PereUbu

---

### Post by PereUbu on 2005-11-14
Made a new fresh install from a brand new cd, and now my keyboard works, Thunderbird works and I can write to my vfat partitions! :p
I also bought a brand new dvd-burner, and it is behaving nicely so far. :D
But my printer (HP DJ845C) still prefer pink letters :( 
 
My thunderbird didn't work because of my lacking write access to my vfat drive, where I kept my mailboxes. I got write acces by unmounting my vfat partitions, uncommented their lines in fstab, and making a new directory (/mnt/hda5) and adding a new line in fstab before mounting it:
/dev/hda5       /mnt/hda5       vfat    user,uid=1000 0       0

**Updated: **When it comes to my printer problem, I think it must be a combination of a bad color-ink-cartridge (only letting out the magenta), and the HPIJS-driver not using the black-cartrigde (blending "black" with yellow, magenta and cyan colors).  What do you think? (The GIMP-print driver prints in black and magenta)

Pink regards to everyone!
PereUbu

---

