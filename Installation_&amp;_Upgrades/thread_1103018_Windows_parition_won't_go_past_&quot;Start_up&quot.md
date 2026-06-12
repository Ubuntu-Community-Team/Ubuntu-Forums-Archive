---
title: "Windows parition won't go past &quot;Start up&quot; screen"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by nbotticelli on 2009-03-22
I recently set up someone's machine to run Ubuntu almost exclusively. So far the one catch though is that she needs to be able to use this one greeting cards program to open up a bunch of her files that have all sort of important information in them.

Her original Windows XP home installation was frakked but there was a recovery partition to restore completely fresh from.

First I pulled all her files/docs/pics off her original installation and then made an image of her original install using O&O as a last resort just-in-case.

Then I used the restore partition and totally nuked her original install and put in a fresh install as if it were straight from the factory again.

Then I booted up using Gparted and this is what I think I went wrong.

I deleted the restore partition and set GParted to expand the windows partition to fill the whole disk because I thought if/when I went to install Ubuntu that it might run into problems if the original Windows install didn't take the full disk in the first place.

I realize that wasn't necessary now but at the time I was just kind of rushing through things.

So after a very long time GParted resized the windows install to fit the entire drive and then I rebooted and went through the Ubuntu install process and installed Ubuntu 8.10 32-bit as a dual boot system


Ubuntu is installed and configured perfectly how I like it but the Windows partition will not boot.

If I select XP from the GRUB menu it just goes to a black screen saying "Start up" and stays there forever.

So I looked around and decided to go into recovery console for XP and did the FIXBOOT and FIXMBR thing and Windows still wouldn't boot.

Tried again and then did the reinstallation of GRUB so that I could get back into the Ubuntu install but still nothing with the XP partition.

I am thinking this has more to do with my having tried to expand the XP partition in the first place to take up the whole disk and not necessarily with GRUB or the Windows boot files. 

Does anyone have any ideas of what I should try next?

---

### Post by nbotticelli on 2009-03-22
Bump*

---

### Post by meierfra. on 2009-03-22
Does  the screen say "Starting up" ? Or "Start Up". 

Anyway, try this:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by nbotticelli on 2009-03-22
Sorry, it probably actually says "Starting up", I don't remember right now without it sitting in front of me.

I will try this later on this week and see what happens then post back.

Thank you!

---

### Post by crusaderbond on 2009-03-23
I would recommend ripping the files from the windows partition with something like knoppix, then reinstalling, and putting the files back. But that is just me. You might have better luck with something else.

---

### Post by nbotticelli on 2009-03-23
I actually already have a complete file back up of all her profiles/docs etc along with a complete image of her harddrive pre-Ubuntu made using O&O.

The reason she needs to still get into the Windows side is to have access to this horrid program called Greeting Cards or something along those lines.

She has been using it as a basic word processor for everything for many years and so all of her "documents" are in this completely crazy proprietary format that nothing seems to be able to open except this program.

So the goal is to get back into the Windows side, use this greeting cards program, copy the text and paste it into an actual word processor and then save as odf/doc files to bring back into Ubuntu.

---

