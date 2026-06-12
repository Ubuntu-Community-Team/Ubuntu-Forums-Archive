---
title: "Ubuntu won't install"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Mephisto16 on 2009-05-31
First time trying Linux and not having much luck.
I boot from the cd and choose language then choose install then it just does something for a minute showing the ubuntu logo, then reboots and then nothing. No signal to monitor to cd or hard drive activity. I tried waiting but nothing happens. 
Anyone else had this problem?

---

### Post by presence1960 on 2009-05-31
Boot from the Ubuntu Live CD again, but this time choose check CD for defects. See what it says. Did you burn your disc on a CD-R at the slowest possible speed? You may just have a bad burn.

---

### Post by Mephisto16 on 2009-05-31
> **presence1960 said:**
> Boot from the Ubuntu Live CD again, but this time choose check CD for defects. See what it says. Did you burn your disc on a CD-R at the slowest possible speed? You may just have a bad burn.

i burned it on a DVD i then tried it on a CD. Both had exact same results, i also checked an option in imgburn that verifies the data so i think this should find any errors.

I forgot to add i did get an error message something about a timer connected to ACPI or something. So i tried again with options selected relating to ACPI, then i got a different error something about not finding local ACPI and using dummy emulated one.
But both ways had same result other than error message.

I wonder if Ubuntu just doesn't work with my BIOS?

---

### Post by presence1960 on 2009-05-31
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Check out the options for F6- you mentioned ACPI. This may be what you are looking for.

---

### Post by Mephisto16 on 2009-05-31
> **presence1960 said:**
> [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Check out the options for F6- you mentioned ACPI. This may be what you are looking for.

Yea i tried the options. same result. Thanks for the help. Just have to stick with windows.

BTW i noticed it actually is not rebooting, it is just stopping completly.

---

### Post by Fried04 on 2009-05-31
Hi. this is also my first time trying linux because my I am sick of windows crashing on me every couple of months.
I am having the same problem as the first post.
I used a cd because I dont have a dvd reader in my computer. I burned several times at 4x because that is what was recomended. I set up the bios to load from cd (and tried usb stick once) and it loads fine, i choose english and then i get the options.
I checked for errors, and it was something in the millions (wtf?), so i assumed it was a little messed up. 
 
I try to check disk for errors, installs both without changing current settings of pc and just plain installing linux, and my pc restarts.
 
 
I am using my roomates computer right now, and help would be _greatly_ appreciated! 
 
Thanks!
 
Edit: i know people will ask pc specs, they are more then ample enough for linux :P
3/4 gig of ram
7800gt nvidia vidcard
2933 chip
 
basically a new computer as of 2003

---

### Post by presence1960 on 2009-05-31
you said you checked disk for errors and it was in the millions. I think it is safe to say your disk is corrupted. I would download the iso and burn it as an image to disk again. Try to dowload from a torrent instead of a mirror.

---

### Post by Fried04 on 2009-05-31
Thanks for the response
 
It didn't even cross my mind that the mirror I downloaded from was corrupt. Ill try to download a torrent as you suggested.
 
I checked the disk for errors, and a bunch of text comes up, I dont think any of them were errors though ( though as I said am completely new to linux, and dont know coding at all)
 
The millions of errors that came up were from when i checked memory of my hardrive( I think)
 
I just tried to check memory again and it is restarting still( it worked a couple times before i tried to reformat to get my pc working, but does not now)
 
If it helps, my windows isnt loading because the ntldr is missing. I tried a few times to fix the files that I read  online that needed fixing, but just said screw it, Im going linux

---

### Post by Fried04 on 2009-05-31
would it help at all if I posted my mp5sum?
( I read in one of the threads around here that it has information, but I dont have any clue what kind)

---

### Post by presence1960 on 2009-05-31
> **Fried04 said:**
> would it help at all if I posted my mp5sum?
( I read in one of the threads around here that it has information, but I dont have any clue what kind)

you can do that. Here is a guide to md5sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Make sure the md5sum matches exactly.

Here is a link to what the hash should be: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

