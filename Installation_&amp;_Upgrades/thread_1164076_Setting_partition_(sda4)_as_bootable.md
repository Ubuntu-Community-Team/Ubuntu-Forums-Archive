---
title: "Setting partition (sda4) as bootable"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by Intrepid Ibex on 2009-05-19
Hi,

I have this windows setup in a partition (/dev/sda4) and I need to set it so that I can launch the setup partition (fat32) from grub (installation from CD is way too slow!).

So how do I do it?

---

### Post by Mark Phelps on 2009-05-19
You trying to install MS Windows from inside Ubuntu?  

If you're trying to run a setup.exe file from inside Ubuntu, you can't do that.  Ubuntu does not understand MS Windows .exe files.

You could try installing Wine and running it from there -- but Wine is intended to run Applications, not for installing OSs.  So, I doubt that it will work.

---

### Post by Intrepid Ibex on 2009-05-19
No, I have it on a different partition ;) (fat32).

I just want to launch the setup partition from grub (which means there is no connection to ubuntu in any way).

ps. well I kinda know what wine is, did you read my sig?

---

### Post by dandnsmith on 2009-05-19
I get the vaguest impression that OP wants to boot Windows in sda4 using grub.

```

rootnoverify (hd0,3)
chainloader +1

```

would be the vital elements.

Try it from the grub command line (escape during boot),
and, if it works, edit the menu.lst or grub.conf accordingly.

---

### Post by Mark Phelps on 2009-05-19
> **Intrepid Ibex said:**
> ps. well I kinda know what wine is, did you read my sig?

Sorry ... didn't intend to be insulting.  You might be surprised how many posts we get here from folks wanting to use Ubuntu to install MS Windows.

As to launching the partition -- what little I know about GRUB is that it only hands over control to boot loaders. If your FAT 32 partition doesn't have a boot loader in it (i.e., NTLDR for Windows XP, BootManager for Vista), it's not going to do anything.

---

### Post by Intrepid Ibex on 2009-05-19
```
This is not a bootable disk. Please insert a bootable floppy and try again ...
```

Umm.. I hate vista? Yes?

I thought this setup had a boot manager ;e

---

### Post by sgosnell on 2009-05-19
It's not Vista's fault.  You have to have an OS on a drive to boot from it.  You cannot boot from a .exe file.  Just copying files to a drive won't make it bootable, even if it is the files from a Windows setup disk.  

You can either boot from the actual Windows setup disk, or you can use something like dd to put the system on a drive.

---

### Post by Intrepid Ibex on 2009-05-19
Yah, I'm installing it from the DVD right now .. ;/

**E:** Nobody suggested dd by this time?

---

