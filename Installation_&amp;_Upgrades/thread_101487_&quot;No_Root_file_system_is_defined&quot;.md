---
title: "&quot;No Root file system is defined&quot;"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by JoshHendo on 2005-12-09
I get this problem when tryint ot install ubuntu. I had just finished partitioning the SECOND HDD, which is what I am putting ubuntu on. Windows is on the first. All the partitioning went well. I have a partition for windows (on the first HDD), a partition for ubuntu (on the second HDD), a swap partition (double the size of my ram, second HDD) and a place where I can put files to share between ubuntu and windows (Second HDD). Ok, right, now I go to contine then that is where I get the error. I believe the error is becuase in the config for the partition I am planning to put ubuntu on it has:
"Use as:  do not use"
I go into that and find a whole lot of things that it can be used as, though I don't know what one to select.
Just for your information, the version of windows I am trying to dual boot it with is: ME, and I am using ubuntu version 10.04 (I live in Australia, and it is hard for me to download it. The new versions should come soon from shipit :)). It would be great if someone could help me :)
-edit-
Dojn't worry. I got it :). Will post here Iif I have any more problems
-Josh

---

### Post by dsjas297 on 2005-12-09
For where it say "do not use", select a file system to use. I would recommend ext3. After that, select the mountpoint as "/". That will define the root file system. Also to set your swap partition to use as swap. Now your done!

Continue with the installation.

---

### Post by JoshHendo on 2005-12-09
Ok. Another problem :|
I just got it all working, restarted the computer, It started to load grub. It said this:

> 
GRUB Loading stage1.5

GRUB loading, please wait...
Error 25


That can't be good :P. I have all my files backed up on a few CD's, so if I have to re install windows, I haven't lost anything, it is just a pain doing it if I end up have to. Does anyone know how I can fix this :) (without reinstalling windows)? If not, I will just reinstall windows. Thanks :)

-Josh

---

### Post by codejunkie on 2005-12-09
[quote=JoshHendo]Ok. Another problem :|
I just got it all working, restarted the computer, It started to load grub. It said this:



That can't be good :P. I have all my files backed up on a few CD's, so if I have to re install windows, I haven't lost anything, it is just a pain doing it if I end up have to. Does anyone know how I can fix this :) (without reinstalling windows)? If not, I will just reinstall windows. Thanks :)

-Josh[/quote] i don't know how to fix the grub error,  just post another thread about that problem, and someone with more expertise will help you with that one.
but i can help you with not having to reinstall windows, insert the windows xp cd if that's what your using boot to the cd like your going to do a fresh install but choose the recovery console option instead and when you get to the command prompt type ```
fixmbr
``` when it finishes type exit to reboot this will restore the windowsxp bootloader.
if your using windows 95,98,me instert a boot floppy and use this command ```
fdisk /mbr
```remove the floppy and press ctrl+alt+del to reboot hope this helps.
edit:fixed wrong command.

---

### Post by JoshHendo on 2005-12-10
[QUOTE=codejunkie]i don't know how to fix the grub error,  just post another thread about that problem, and someone with more expertise will help you with that one.
but i can help you with not having to reinstall windows, insert the windows xp cd if that's what your using boot to the cd like your going to do a fresh install but choose the recovery console option instead and when you get to the command prompt type ```
fixmbr
``` when it finishes type exit to reboot this will restore the windowsxp bootloader.
if your using windows 95,98,me instert a boot floppy and use this command ```
fdisk /fixmbr
```remove the floppy and press ctrl+alt+del to reboot hope this helps.[/QUOTE]
THANKYOU! :D

Just 1 error with that, and I am posting this for other peoples benifit. For windows 95\98\me the line is
fdisk /mbr
not
fdisk /fixmbr

(Even though that line you posted was wrong, it was becuase of it that I found the answer via google :D). Thanks again :)

---

### Post by codejunkie on 2005-12-10
[quote=JoshHendo]THANKYOU! :D

Just 1 error with that, and I am posting this for other peoples benifit. For windows 95\98\me the line is
fdisk /mbr
not
fdisk /fixmbr

(Even though that line you posted was wrong, it was becuase of it that I found the answer via google :D). Thanks again :)[/quote]
i thought it was one of those, but i guess things like that happen when you haven't used windows in quite a while :rolleyes: sorry about that... but glad you got it fixed and repost that grub error and im sure someone on here will know how to fix it.

---

### Post by JoshHendo on 2005-12-10
[QUOTE=codejunkie]i thought it was one of those, but i guess things like that happen when you haven't used windows in quite a while :rolleyes: sorry about that... but glad you got it fixed and repost that grub error and im sure someone on here will know how to fix it.[/QUOTE]
Well, I tried again (knowing that I could fix it if the same error came up), and the same error did come up. Does anyone know of another way that I could do it with windows ME :)?

---

