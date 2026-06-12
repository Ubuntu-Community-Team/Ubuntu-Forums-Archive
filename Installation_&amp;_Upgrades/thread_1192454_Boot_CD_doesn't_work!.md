---
title: "Boot CD doesn't work!"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by pooja on 2009-06-20
Hi there!
I want to install Ubuntu 9.04 on my HP laptop DV6385ea. I haven't done any partition so far, I just wanted to have a look of the Ubuntu desktop so in my other computer (Dell Inspiron) I downloaded the .iso file through utorrent, burnt it to a CD-R with "Record Now!" and put the CD in my hp laptop (w/ no partition, just one big disk, 149 GB occupied by Vista).
I shut down and restarted the laptop hoping for it to automatically catch up with the CD inserted in the disk drive but it didn't and Vista started over again. I tried restarting some 2 or 3 times pressing F2 and F10 but nothing. Can anyone give me a hint? Do I really need to do the partition? How much space does Ubuntu need, 25GB, 30GB? I want to use Ubuntu extensively (multimedia, web surfing, office application) and limit as much as possible Vista.

---

### Post by wpshooter on 2009-06-20
Is your CD-Rom drive set as the FIRST boot device in the BIOS ?

---

### Post by pooja on 2009-06-20
I'm not sure... How do I check that? Press F..something at boot up?

---

### Post by jerrrys on 2009-06-20
just to be sure, this is the LIVE cd?  

to answer your question; during boot you should be given the option to enter system configuration (or named something similar to that).  it usually is F1 or F2, but you should get a screen that tells you.

---

### Post by Bucky Ball on 2009-06-20
Press either the 'delete' key or the F1 to get into BIOS as soon as the machine boots up. You set to boot from CD there. That sounds like your problem; machine won't automatically boot from the CD unless you tell it.

When your screen comes alive at boot, somewhere on that first screen it should tell you what to press to get into 'Setup' (BIOS). Watch carefully as it goes by quickly and might be an obscure key like 'F2' (like my machine).

---

### Post by pooja on 2009-06-20
ok, just in case I succeed in booting from the CD, is there an exit without installing the Ubuntu since I haven't done any partition?

---

### Post by jerrrys on 2009-06-20
yes, you will get a screen that will give you the option to run ubuntu without installing.

---

### Post by Bucky Ball on 2009-06-20
You should have the LIVE CD which gives you the option of running Ubuntu from the CD, NOT installing it. That will tell you whether your hardware is going to work or not also. If that all goes well, you should be good to install to the hard drive. 

Performance running from CD is naturally slower than installed on the disc but good start to see how things are going to work out.

---

### Post by pooja on 2009-06-20
Still not working. Pressed F10 as soon as I saw the HP logo at boot up. Entered Boot Setup and changed the Boot order so that the CD drive would be the first to boot instead of the USB drive. Saved everything and booted again. Nothing still. The torrent I downloaded was called **ubuntu-9.04-desktop-i386.iso**. I have a CD drive with LightScribe.

---

### Post by Therion on 2009-06-20
You need to burn the file you downloaded as an *image* in order for your PC to be able to boot from it.

See these instructions for how to do that: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also, burn your CD sloooooooooowly.  Say, 8x or 16x and no faster.  You need accuracy for this job, not raw speed.

---

### Post by jerrrys on 2009-06-20
you say still nothing. do you mean that the cd did try to boot or you booted into vista?

---

### Post by pooja on 2009-06-20
WoW! Ubuntu is amazing! It's swift and smart even though it's running from the CD! I tried out some applications (OpenOffice, Games, Sound Recording) and I set the Internet connection to my home wireless LAN - it's fantastic!
The only little problem I'm having is with the keyboard layout- I changed it to my needs from System > Preferences > Keyboard but now that I'm writing on the forum, not all the keys match the symbols drawn on them. Anyway, not a major problem!

Kudos for Ubuntu!!!

Now I need to shrink Vista and install Ubuntu 9.04 for real!
Thank you guys for your prompt answers!          ):P

---

### Post by Bucky Ball on 2009-06-20
I have something similar to your laptop (see my signature) and it is 64bit and running on the 64bit version. You should try that if you have a 64bit laptop.

I have had no problems installing the 64bit whatsoever but I have been using the long term support 8.04 since it came out last year, not 9.04.

You could try 8.04 (64bit if appropriate) and see if you get the same problems.

* Update: Ah, you posted before me! Good one, success! You will notice a little speed increase when installed on the drive and the keyboard problem should be simple to fix. Keep us notified, welcome and glad you like it so far. The good news is all your other hardware is working. Like I said, I have been using it on a HP dv6000 series laptop for 18 months and loving it. :)

---

### Post by jerrrys on 2009-06-20
enjoy

---

### Post by pooja on 2009-06-20
I forgot to mention what was the problem with the CD.
That CD didn't work because the program I used, "Record now!", just copied the iso file like any ordinary file, onto the CD. So I burnt the iso on another Re-writable DVD, this time using a different application and booted the laptop with the disk inserted in the drive. It worked! Just great!

---

### Post by wpshooter on 2009-06-20
> **pooja said:**
> WoW! Ubuntu is amazing! It's swift and smart even though it's running from the CD! I tried out some applications (OpenOffice, Games, Sound Recording) and I set the Internet connection to my home wireless LAN - it's fantastic!
The only little problem I'm having is with the keyboard layout- I changed it to my needs from System > Preferences > Keyboard but now that I'm writing on the forum, not all the keys match the symbols drawn on them. Anyway, not a major problem!

Kudos for Ubuntu!!!

Now I need to shrink Vista and install Ubuntu 9.04 for real!
Thank you guys for your prompt answers!          ):P

Make sure that you run scandisk and defrag once or twice before you try to change Windows partition size and before you install Ubuntu to the drive.

---

### Post by Bucky Ball on 2009-06-20
Excellent. When you install, there is an option to manual partition along the way so you don't need to make up the partitions in Windows. Linux uses EXT3 or EXT4, not ntfs of FAT to install (although it can read and write to both nfts and fat once installed), so you can't create a partition for Ubuntu to install to from Windows anyhow.

Good luck with it.

ps: and always a good idea to run 'Check CD for defects' before the install. It is an option on the CD menu.

:)

---

