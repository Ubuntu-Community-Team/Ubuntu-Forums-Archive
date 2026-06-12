---
title: "kernel update, now won't boot &amp; can't remove 2nd hdd"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by I8NY on 2009-06-24
So i updated Ubuntu 9.04 through the update manager to a newer kernel.  The update failed for the kernel update to 2.6.28-13-generic from 2.6.28-11-generic.  Now the when ever i boot the pc i get a error with it saying, 
"[   0.656864] ACPI: Aborted because crc error.
[   2.940471] crc error
[   3.042072] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
So i added a 2nd hdd and install ubuntu 9.04 onto and then i was going transfer stuff from the 1st hdd that has the boot error.  But now grub wants me to select what OS to boot and it lists ubuntu on the 2nd hdd and 3 ubuntus on the 1st hdd.(there's only 1 installed ubuntu on 1st hdd)  I can select to boot ubuntu on the 1st hdd now using the older kernel listed (2.6.28-11-etc.).  I have tried booting the broken kernel (2.6.28-13-etc.) in recovery mode but that does not work.  So now want remove the 2nd hdd boot grub gets a error 25.  So my question is how do i remove my 2nd hdd and have grub boot the the older working kernel w/out having me selecting it.  And using the older kernel will i have updating problems in the future?

---

### Post by quixote on 2009-06-25
> using the older kernel will i have updating problems in the future? This is the easiest question, so I'll start here. :)  I don't think so.  It'll just prompt you to update again, if the newer one isn't there, as far as I know.
> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)" ...
3 ubuntus on the 1st hdd.(there's only 1 installed ubuntu on 1st hdd)This suggests filesystem corruption.  Boot from a LiveCD. open a terminal and make sure your messed up hard drive is NOT mounted.  You can do that by running```
sudo fdisk -l
```
Pick out your former boot drive from the list, it'll probably be something like /dev/hda1 or /dev/sda1, and then type ```
sudo umount /dev/hda1  *fill in your own drive designation*
```  It may return a message saying it's already not mounted, which is fine.
Now run: ```
sudo fsck -y /dev/hda1 *fill in your own drive designation*
```
That stands for "filesystem check, yes, fix all errors without waiting for an answer"  Never run this on a mounted drive (one where you can see the directories it contains).

Hopefully, it finds errors, fixes them, and your system will magically boot from the original hard drive. :)

Don't worry about the second hard drive for now.  To get data off the messed up drive, it's better to boot from a LiveCD with the 2nd drive plugged in.  Then mount the bad drive, and the 2nd drive, and move your data over.  

HOWEVER: if there has been filesystem corruption, every time you use the drive without fixing the problem, the worse the corruption gets.  So, ideally, you fix the corruption first.  If there's data you absolutely must have, then transfer only that, then move on to fixing the filesystem before doing a whole lot more disk accesses.

---

### Post by quixote on 2009-06-25
I should add that this won't fix the broken 28.13 kernel.  If it does allow you to boot from hda1, and if that's listed as the default choice in grub, move down to your older kernel before it continues booting.

---

### Post by I8NY on 2009-07-10
okay i did as u said unmount then run sudo fsck etc. on a live cd.  did that but it says the drive is busy or used by another program when running fsck.  It says it is unmounted in the termenal and in file browser.  And i don't know how to change the default choice in  grub boot loader.

---

### Post by quixote on 2009-07-10
> drive is busy or used by another programThat means some part of the system still thinks it's mounted.  Try```
sudo umount -f /dev/hda1 *fill in your own drive designation*
```(that tells it to force an unmount)  Then try the fsck -y command again.  

Changing the default choice in grub involves editing one text file.  (However, if this is the problem hard drive, boot from LiveCD, not the hard drive, until it is fixed!)
```
sudo cp /boot/grub/menu.lst /boot/grub/menu_lst.backup
```
(so that you have a copy of this critical file, in case anything goes wrong)

Then```
gksudo gedit /boot/grub/menu.lst
```
(I'm assuming you're using intrepid or jaunty.  Which version are you using?) Near the top of that file you'll see a line that says "default   0"

Grub numbers from 0, so that means the first of the list of choices is the default.  Toward the end of the file are all the choices.  

There are two ways to go at this point: 1) Find the entry you want (and its associated recovery mode entry) and move them up to the default (zero) position.  This method works more easily with future updates.  Or, 2) Find the entry you want.  Count carefully from the first one to figure out what number you should enter instead of "0" next to "default" at the top.  Every entry counts, including any placeholders that just create separators, for instance.

---

### Post by I8NY on 2009-08-03
Well the 1st hdd ubuntu died so i'm going to do a clean install w/ 1 hdd but grub is not working. (grub error 18  So how do i reinstall grub?

---

### Post by quixote on 2009-08-04
Sorry, I've lost track of which disk is currently which.  Will the clean install be to a partition of the disk that also contains Windows?  Or to the disk with nothing but Ubuntu?

Grub error 18 apparently happens if you have an older hard drive with relatively small cluster sizes. Look through the BIOS settings.  You can do that by hitting whichever key the computer tells you to (usually only for a second or two) right after you first turn it on, and it says e.g. "press F2 for setup" or something similar.  Somewhere in the BIOS settings, it has hard drive type, with settings like "LBA" "Auto" "Normal".  Set it to "Normal" and see if that helps.

---

### Post by I8NY on 2009-08-04
Sorry about mixing up what hdd is what.  I looked for that setting (LBA, etc) in the BIOS but it was not there.  I have seen the setting in other BIOSes but it is not in this BIOS.  The hdd is not that old, 40gb made ~2002 but i don't know how old you are talking about.  Now i'm getting a grub error 15 for some reason.:(  The hdd is only ubuntu, no windows.

---

### Post by quixote on 2009-08-05
I'm not sure how old either.  Mainly I think it's a matter of size.  Small enough so that the cluster sizes are smaller than would be expected under LBA.  How small is that?  Again, dunno. :?  I guess it's not relevant any more, since it's not even an option.

error 15 means grub can't find menu.lst.  That's actually not too hard to fix.  (But it's weird you keep getting different errors.)

Try the following (based on [this thread]("http://ubuntuforums.org/showpost.php?p=4587202&postcount=9")):

(I'm assuming you get the initial grub choices, but when you choose one, you get error 15.)  When grub is at the list of choices, hit "c"
That will bring you to a Grub prompt.
grub>
At that prompt type ```
find /boot/grub/stage1
```

It'll return something like: root (hd0,0)

Now press Esc.
Select the first boot option and press "e"

Press "e" again on the root option
Change the (hdX,X) to whatever you got above. for me it was (hd0,0).
Press Enter.
Now press "b"

Ubuntu should load up.

Once things are working, you need to change this permanently.
Open a terminal and enter ```
gksudo gedit /boot/grub/menu.lst
```

Scroll down towards the bottom of the file, and you will find the same "root (hdX,X)".  Change it as needed and save.

Look at the "root (hdX,X)" listed for the remaining boot options while you're editing the file.  They may need to be changed too.

---

### Post by quixote on 2009-08-05
By the way, searching for the exact error message is often a good way to find information on it.  For instance, in google: "grub error 15 site:ubuntuforums.org" (without quotes) would find all mentions of that error on the ubuntuforums.  "grub error 18 site:.linuxquestions.org" likewise for that site.  and so on.

---

### Post by I8NY on 2009-08-07
okay, so i found a program called, "supergubdisk" i put that on a floppy and ran it to see if it would fix the problem.  I messed around with it and deleted grub or messed it up so much grub didn't pop up the next time i boot the pc.  Reinstalled Ubuntu 9.04 and installed grub again and it works!:D  Thank you for your help.

---

### Post by quixote on 2009-08-07
Glad you got it sorted :)  More often than not, a clean install is really the easiest solution.

---

