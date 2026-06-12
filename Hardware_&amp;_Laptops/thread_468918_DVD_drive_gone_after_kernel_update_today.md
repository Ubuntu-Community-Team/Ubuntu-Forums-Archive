---
title: "DVD drive gone after kernel update today"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by apel_2804 on 2007-06-09
Hi,

I updated the kernel to 2.6.20-16.29 as adviced from updater. After that there is no dvd drive available. It is an dell latitude d630 with new gm965 chipset. I see in fstab that it schould /dev/hda but these device is not found in /dev and the Hardware Information also shows no dvd or cd device. Any ideas what to do?

---

### Post by grahams on 2007-06-12
A lot of folks ran into issues with the 2.6.20-16 kernel update. 

I believe ide drives that where previously under /dev/sd* moved back to the older /dev/hd* device file naming. If you have an ide disk you may find your disk partitions now start at /dev/hda,, and your dvd is something like /dev/hdc (which is where mine move to). 

If it isn't as simple as that try rebooting and select the old 2.6.20-15 kernel and see if you can still access your dvd drive.

---

### Post by Roadrunner777 on 2007-06-14
Same problem here.  I've been through every forum thread I can find on this, no joy.  I've been through the threads relating to fstab, and to my untrained eye, I don't see anything there like they have been getting.

I know it's the new kernel, I was using my DVD drive for backups and so I know by the day what happened.  Is there some way to find out if this is being worked on?  If it's not working soon, I'll have to buy a USB drive or something to continue my backup.

Also, I tried the previous kernel (esc during grub) but that brings up some issue where my video driver won't load.

I guess mainly I'm interested in knowing if this has been recognized as a bug and is being worked on.  If someone could give me a direction, I'd appreciate it.

- Phil

---

### Post by cnshzj007 on 2007-06-17
> **grahams said:**
> A lot of folks ran into issues with the 2.6.20-16 kernel update. 

I believe ide drives that where previously under /dev/sd* moved back to the older /dev/hd* device file naming. If you have an ide disk you may find your disk partitions now start at /dev/hda,, and your dvd is something like /dev/hdc (which is where mine move to). 

If it isn't as simple as that try rebooting and select the old 2.6.20-15 kernel and see if you can still access your dvd drive.

[B][SIZE="3"]The old kernal 2.6.20-15 has the problem that it can not start the GDM with the X3100 GPU.
So your advice is not able to access.
[/SIZE][/B]

---

### Post by Voland666 on 2007-06-20
I have this problem also. Can work it around in this way:
- Open a terminal
- write
```
sudo modprobe -v ide-generic
```

you should get /dev/hd(a-b-c-d) (primary/secondary master/slave), /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw depending on your configuration. The drive should also be visible in computer:/// and inserted discs should be automounted.

- If that worked, write in the terminal
```
sudo gedit /etc/modules
```

- add this line in it and save
```
ide-generic
```

Modifying /etc/fstab accordingly might be needed.
Please notice that ide-generic doesn't give you any DMA mode (and this is bad). This is just a temporary workaround, I think something should be fixed in the kernel...

---

### Post by cnshzj007 on 2007-06-21
OK.That's BINGO.
THANKS!
AND Looking for fixed it in kernel.

---

### Post by El_Hobo on 2007-06-21
Hello.

I seem to be just one of the many having this problem too, and so far..well.. thank you :)

anyway, modprobe works fine for almost anything here, but when i try to install "restricted extras" from add/remove programs, it unmounts my cdrom.
I can insert cd, and read from it using Konqueror, but when i start upp add/remove, select restricted, and click apply it says to insert my ubuntu cdrom in /cdrom/, and it is unmounted again. if i try to remount it, it just reunmounts it when i click retry.
I tryed to copy the cd (worked) and create symlink from /cdrom/ and /media/cdrom/ to the folder containing all cdrom files, but no luck, still just "insert cdrom"..

anyone have any ideas what this can be?

//Bjornie

---

### Post by vgiannadakis on 2007-07-04
I have an Intel GM965-based laptop and have the same problem with my cdrom: It cannot be mounted.

I had to dist-upgrade to get the latest Feisty kernel (2.6.20-16-generic) to solve my graphics problems (X3100), and discovered today that my burner wasn't there!! Gnome reported "mount: special device /dev/hda does not exist" and no cdrom...

Looking at the fstab, I saw a line that should mount /dev/hda, but indeed, no /dev/hda existed!

**Voland666**, your suggestion worked fine with me, as soon as I modproped ide-generic, the cdrom spinned-up and Gnome showed me the contents of the cd!

My concern is this however: Grub's menu.lst includes "all-generic-ide" in its defoptions line, and if I'm not wrong, this is supposed to tell the kernel to load this exact module (ide-generic), isn't it? /proc/cmdline confirms that all-generic-ide is passed to the kernel.

If all-generic-ide means ide-generic, then why the kernel doesn't load it??

---

### Post by lordxale on 2007-07-04
I just got my brand new d630 yesterday (has to be one of the first ones off the presses with the quadro 135m!), had the same problem with the DVDRW after updates.  I'm happy to report that Voland's fix worked like a charm, but the no DMA is a killer.  I eagerly await a kernel update, or whatever else could be done to fix this for real :)

For the record, I'm running Kubuntu 7.04 on kernel 2.6.20-15

---

### Post by tommoyer324 on 2007-07-04
I too had my DVD go missing, and was able to find it again by using ide-generic, however there are several problems with this.
1. After rebooting and having ide-generic loaded the drive shows up fine, but Nautilus reports that disc are either blank ( in the case of a burned disc) or it doesn't detect it at all ( disc made "professionally" i.e. one that came with a piece of hardware )
2. It doesn't automount anything anymore.

I was able to successfully mount the CD's (both kinds) using mount /dev/hda, but this doesn't show up in Nautilus (Nautilus doesn't show the disc as being mounted).

3. I can't play DVD's at all.

I tried booting to the previous kernel (2.6.??-15) and it appears that the drive is detected fine (couldn't be sure GDM wouldn't start which is because of binary drivers I think)

any ideas on when or how to fix this?

---

