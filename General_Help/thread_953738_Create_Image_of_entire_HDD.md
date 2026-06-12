---
title: "Create Image of entire HDD"
date: 2008-10-20
forum: General Help
---

### Post by GabrielWolff on 2008-10-20
I have a **dual boot XP and Ubuntu**. I want to replace my 80 GB hard drive with a larger one.

In order to not reinstall everything, I want to create an image of the entire harddisk, place it on an external drive, replace the internal drive, and then copy the whole thing on the new drive.

Any clue how I do that?

---

### Post by Titan8990 on 2008-10-20
You could try using the dd command, although I doubt that it will keep grub in the MBR. This means that there is a good chance that you will have to reinstall grub.

I'm not an expert on dd and it can be a dangerous command so I will not be giving any examples. See:

man dd

---

### Post by logos34 on 2008-10-20
The easiest way is probably to boot the ubuntu live cd and use Gparted.
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

(the example is ntfs, but the procedure is the same for ext3)

remember to reinstall Grub to the mbr of the new drive. (see link my sig)

---

### Post by GabrielWolff on 2008-10-20
> **logos34 said:**
> The easiest way is probably to boot the ubuntu live cd and use Gparted.
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

(the example is ntfs, but the procedure is the same for ext3)

OK, this is what I thought as well

But gparted does NOT give me the option to actually copy the whole HDD as one piece.

Copying the different partitions one by one seems like a process with a lot of place for errors in the end, isn't it?

Is there a possibility of just creating a copy/image of **the whole HDD** as it is?

---

### Post by cariboo on 2008-10-20
You can use partimage to make a complete duplicate of your hard drive. Partimage makes a byte by byte copy of the hard drive ignoring the empty space. DD will do the same thing but it also includes the empty space. To use dd in a terminal type:

```
sudo dd if=<olddrive> of=<newdrive>
```

Where <olddrive> = your current drive (typically /dev/sda) and <newdrive> = your new drive (typically /dev/sdb). Optimally you would want to do this with both drives unmounted so using the LivedCD will allow you to do this.

Partimage is available in the repositories, use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it. Partimage has a text based interface where you set the configuration.

Jim

---

### Post by logos34 on 2008-10-20
> **GabrielWolff said:**
> Is there a possibility of just creating a copy/image of **the whole HDD** as it is?

In that case then you want to use dd command like titan suggested.  If you copy the entire disk it will include the mbr as well.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

good luck

---

### Post by GabrielWolff on 2008-10-20
> **logos34 said:**
> In that case then you want to use dd command like titan suggested.  If you copy the entire disk it will include the mbr as well.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

good luck

So let's say I got that image on my external drive.

I would then need a Ubuntu (or whatever) live CD to actually access it, right? Or how could I boot after actually replacing the old drive with the new one?

---

### Post by GabrielWolff on 2008-10-20
> **cariboo907 said:**
> You can use partimage to make a complete duplicate of your hard drive. Partimage makes a byte by byte copy of the hard drive ignoring the empty space. 
Jim

This, again, lets me, as far as I can see, copy only partition by partition. I would have to copy sda1, 2, 3, 4, 5 and 6.

Any chance I can copy the whole drive in one piece?

---

### Post by logos34 on 2008-10-20
> **GabrielWolff said:**
> So let's say I got that image on my external drive.

I would then need a Ubuntu (or whatever) live CD to actually access it, right? Or how could I boot after actually replacing the old drive with the new one?

yes, simply boot from the live cd again after installing the new drive and dd copy the external drive to the internal

As an alternative to dd command, G4L or clonezilla might be allow you to copy the the whole disk.  Not sure, though, you'll need to check.

---

### Post by GabrielWolff on 2008-10-21
> **logos34 said:**
> yes, simply boot from the live cd again after installing the new drive and dd copy the external drive to the internal

As an alternative to dd command, G4L or clonezilla might be allow you to copy the the whole disk.  Not sure, though, you'll need to check.

Great. I'll try it and will either report happily or from a WIN machine :)

---

### Post by indytim on 2008-10-21
One other thing that comes to mind,  you might want to check with your h/d mfgr.  For example, you might find what you're looking for within say, Seagate Tools.  

IndyTim

---

### Post by GabrielWolff on 2008-10-27
Well, it took me several days, but today I actually booted with the gparted live CD and wanted to copy the Ubuntu partition

The partition is called sda3 and is divided into two (screen shot attached). Gparted will not let me copy them as one. Can I copy them in two parts and still restore the system correctly later on?

---

