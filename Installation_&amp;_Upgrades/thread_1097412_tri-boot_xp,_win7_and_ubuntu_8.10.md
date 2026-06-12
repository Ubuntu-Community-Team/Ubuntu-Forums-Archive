---
title: "tri-boot xp, win7 and ubuntu 8.10"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by xsaulx on 2009-03-15
i've had a dual boot xp/ubuntu for a while but xp was messing up so i wanted to install windows 7 and check it out. 
installed it on a new partitions, reinstalled grub from a live usb. and now i can boot into ubuntu fine. but when i wanna boot windows i go to xp and it takes me to the windows booter with options for xp and 7.
but going through 2 boot screens is annoying!

i tried adding windows7 to the menu.lst but i get the "bootmgr not found..." and my xp option now takes me to the windows boot menu...

so i was wondering if i can boot in to all 3 systems directly from grub?

---

### Post by meierfra. on 2009-03-15
I assume that your main goal is to have only one boot menu.
This can by achieved fairly easily by adding Ubuntu to the Windows Boot Menu with EasyBCD:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

You should also edit menu.lst via "gksudo gedit /boot/grub/menu.lst"
and change "timemout 10" to "timeout 2" and "#hiddenmenu" to "hiddenmenu"


If you want I can also show you how to add XP to the Grub Menu, but that is more involved since one needs to separate the Win 7 and XP boot loaders.

---

### Post by xsaulx on 2009-03-17
thanx but yea i was thinkin more like adding both to the grub menu and skipping windows booter if i can. or atleast change that delay so it doesn't show.

---

### Post by meierfra. on 2009-03-17
> or atleast change that delay so it doesn't show. 

That's what editing "menu.lst" as described in my previous post will do.

So just let  me know whether  you want to go the easier route with EasyBCD or whether  you want me to write up instruction how to add XP to the Grub menu.

Keep in mind that adding XP to the Grub menu will not actually skip the Windows Boot Loader (but  you can edit Windows Boot Loader so that it does not show)

---

### Post by xsaulx on 2009-03-17
well i meant to make the windows boot screen not show.

so i guess i want the harder way, by adding xp and 7 to grub so i can boot all 3 from grub.

---

### Post by Mark Phelps on 2009-03-17
> **xsaulx said:**
> well i meant to make the windows boot screen not show.


The boot screen shows automatically when there is more than one Windows OS on the machine -- at least, at the time of the installation of the additional OSs.

To "fix" this, you have to do the following:
1) Move the boot loader files from their original partition to the host partition. Example, if you have XP and then install Vista as a second OS, Vista writes the boot loader files to the XP partition. If you install Seven instead of Vista, it will do the same thing.  You have to find the bootloader files and move them OUT of the XP partition.
2) Boot into the additional OS(s), and usine EasyBCD (or BCDEdit if you like the command line version), edit the boot manager file to remove the other OS entries.
3) Reboot when done

If all the boot manager files now have only one entry, I believe that the boot menus will no longer be displayed (but I could be wrong -- haven't actually tried this).

---

### Post by meierfra. on 2009-03-17
There are at least two more steps:

4)  Fix the boot sector of the XP partition.

5)  Use EasyBCD (or bcdedit) to edit the path for "bootmgr"

(and of course you have to edit menu.lst)

I don't have time right now, but I will write down  detailed instructions  this evening.

---

### Post by meierfra. on 2009-03-17
Here are the instruction how to add XP and Win7 to the Grub boot loader.

Boot to Win 7.


**Step 1 Edit the Win 7 boot loader**

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter".  This will open a Win 7 commandline as an administrator. Type

```
 
bcdedit /set {bootmgr} device boot
bcdedit /set {bootmgr} timeout 0
bcdedit /delete {ntldr} /f

```

(don't close the commandline)

[B]Step 2 Copy the Win 7 boot files to the Win 7 partition.
[/B]
Open the "XP" partition from  "My Computer". Go to "Organize->Folder Options" and then click on the "View" tab.
Check "Show hidden files and folders"
Uncheck "Hide Protected operating System Files"

Open the "Win 7" partition from "My Computer"

Drag the file "bootmgr" and the folder "Boot" from the XP partition to the "Win 7" partition.

**Step 3 Fix the XP bootsector.**

There are various ways to accomplish this. I will give you two options:

[COLOR="Red"]Option 1:[/COLOR]

Insert your Win 7 CD in the CDRom drive and wait for a few second. At the command line:

```
E:\boot\bootsect  /nt52 D: /force
```

Here "E" needs to be replaced by the drive letter of your CDrom drive and "D" by the drive letter of your XP partition. (Just look in "My Computer" to determine the drive letters. Even if you know the drive letters, I suggest  to double check.  Win 7 and XP probably use different drive letters assigns. You need to use the drive letters used by Win 7)

[COLOR="Red"]Option 2:  [/COLOR]

Boot from your XP CD.
Press "r" to enter the repair console.
Use

```
map
```

to determine the drive letter of your XP partition. Type

```
fixboot C:
```

Here "C" needs to be replaced by the drive letter of your XP partition.

If neither Options 1 nor Option2 works for you, let me know  and I can show you how to fix the boot sector from Ubuntu.


**Step 4 Add Win 7 to  "menu.lst"**

Since you already seem to have carried out this step, I'll skip this part of the instruction.


That should be it.  Let me know if you need additional help, or run into problems.

---

### Post by xsaulx on 2009-03-18
wow! thanx alot!
its all working now! booting from grub!! just like i wanted! =D

i did get a few permission errors when copying the files in step 2. but i was able to copy them in ubuntu no problem! 

thanx for all the  help!!

---

### Post by meierfra. on 2009-03-18
> wow! thanx alot!
its all working now! booting from grub!

Great.   Have fun with all your 0Ss


> i did get a few permission errors when copying the files in step 2. 

Thanks for letting me know. Seems my tutorial still needs some fine tuning.

---

### Post by Mark Phelps on 2009-03-18
meierfra:

Thanks for the tutorial -- it's great!

---

### Post by meierfra. on 2009-03-18
> Thanks for the tutorial -- it's great!

Thanks  for the compliment. I'm still trying to sort out the best way to copy the boot files. Using Vista it seems   one has to change the attributes of the files. And in Ubuntu one needs to mount both  Windows partitions.  So  there doesn't seem to be a really easy way to do it.

---

