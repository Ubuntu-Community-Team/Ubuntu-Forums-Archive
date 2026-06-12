---
title: "Where's my C: drive (Vista, other drive is Ubuntu new install)"
date: 2008-11-12
forum: General Help
---

### Post by inmytaxi on 2008-11-12
I have a IDE drive and a (sata) C:\Vista 64 bit.

I installed the new sata C: drive after the IDE had XP (32 bit) on it, installed Vista, and after POST I would get two choices:

Older Windows Version [IDE]
Vista [sata]

with the second highighted, I could cursor up to highlight XP and hit enter to boot, or leave it (or just hit enter) and Vista would do it's thing.

note: When up and running, XP (IDE drive) couldn't see the Vista (sata) drive, and thought it was still the C: drive.  Conversely, up and running Vista **could** see the XP (IDE) drive, and thought XP was the D: drive and Vista (sata) was the C: drive.  

I installed Linux on the IDE drive hoping Linux is going to do more to allow me to control my computer than Windows.  No such luck.

Grub gobbles up control of my desktop after POST and doesn't give me a choice to boot from the sata C:\Vista drive.  

I do get three choices: Ubuntu, Ubuntu safe mode, and memtest.

I tried changing boot priority order to begin from the sata C: hard drive but Grub still grabs.

Is there a way to get Grub to give me an option to boot from the Sata disk?  Is Grub not seeing the sata drive (I had to do an ACHI driver install when I installed the sata drive and Vista, and BIOS asked for a achi-raid driver)?

If I uninstall Ubuntu, will Grub still reside in the BIOS?  If it's there to begin with?

Should I flash the bios?

Try to reinstall XP from CD to IDE? 

Reinstall Vista from CD to Sata?

I know...delete Vista ... HELP Please!

ps all puns intentional!

---

### Post by fjgaude on 2008-11-13
So many things to know to get this right. What does this show:

```
sudo fdisk -l
```

What you need then is to show us what your menu.lst file looks like, but only the tail end of the file, from **## ## End Default Options ##** to the end.

You can get to this file using the gedit text editor:

```
gksudo gedit /boot/grub/menu.lst
```

Go down the file and get to the ## End Default Section and copy and paste into your reply to us.

After you show us these things we will suggest what to add to the menu.lst so that Windows is in the grub menu at bootup.

---

### Post by Coreigh on 2008-11-13
A little more information for you.

You indicated that before you tried Ubuntu you could boot to XP but could not see the SATA drive with Vista. The reason for this is that XP does not natively know how to read SATA drive channels, you need the SATA drivers for XP.

Wether you keep Ubuntu or go back to XP Grub can be configured to see all drives and allow you to boot from which ever you choose.

---

### Post by cariboo on 2008-11-13
The reason you can't boot Vista, is that by installing Ubuntu on the first hard drive you wiped out the boot files that Vista needs to boot. Grub didn't see those files so there is no menu entry. You could try changing the disk order in the bios, but I don't think that will be to successful. The vista boot files don't take up a lot of room, so you could create a small 5-10Mb partition at the start of the IDE drive, then use your Vista installation CD to repair the installation, then you should be able to install Unbuntu, with out affecting your Vista installatiion.

Jim

---

