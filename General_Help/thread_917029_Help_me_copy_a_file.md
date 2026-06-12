---
title: "Help me copy a file"
date: 2008-09-11
forum: General Help
---

### Post by ManyBeers on 2008-09-11
Me again. I need to make a copy of ubuntu.bin which is part part of Ubuntu's boot process. It has a size of 512. Anyways i would like to make a copy of it and put it on a drive. Can somebody help me do this.

---

### Post by WRDN on 2008-09-11
Right click and select "Copy" :)
If, for whatever reason, this cannot be done, open the Terminal and type:

```
gksudo nautilus
```

Then copy the file. The command above allows you to use nautilus with root privileges. I can see no reason why you would have to do so though, for the task at hand.

---

### Post by ManyBeers on 2008-09-11
> **WRDN said:**
> Right click and select "Copy" :)
If, for whatever reason, this cannot be done, open the Terminal and type:

```
gksudo nautilus
```

Then copy the file. The command above allows you to use nautilus with root privileges. I can see no reason why you would have to do so though, for the task at hand.

Let me explain: I just yesterday installed Ubuntu 8.04 on my Sony laptop 
which already had WindowsXP on it. So I currently dual boot via Grub installing itself in the Master Boot Record. I would like to go back to 
using Windows bootloader to boot the systems. The way this is done is by placing a copy of Ubuntu.bin in Windows root(C:\drive) in my case and then editing Windows boot.ini file to point to the Ubuntu.bin file in
C:. I know how to do htis in Windows but not how to do stuff in Linux with the command line. I just looked in nautilus and I believe the file I need a copy of is Stage_1. It showed a file size of 512 which looks good. Is that the correct file?

---

### Post by ManyBeers on 2008-09-11
> **ManyBeers said:**
> Let me explain: I just yesterday installed Ubuntu 8.04 on my Sony laptop 
which already had WindowsXP on it. So I currently dual boot via Grub installing itself in the Master Boot Record. I would like to go back to 
using Windows bootloader to boot the systems. The way this is done is by placing a copy of Ubuntu.bin in Windows root(C:\drive) in my case and then editing Windows boot.ini file to point to the Ubuntu.bin file in
C:. I know how to do htis in Windows but not how to do stuff in Linux with the command line. I just looked in nautilus and I believe the file I need a copy of is Stage_1. It showed a file size of 512 which looks good. Is that the correct file?

Bump.I still need some help on this.

---

### Post by WRDN on 2008-09-11
Using [this]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") guide, the instructions for adding Ubuntu to the Windows MBR are as follows:

> 
#  Reboot into Windows. When you get there, you should now see a ubuntu.bin file on your FAT32 partition. Here's the steps to get the Windows boot loader to load Linux:

   1. Copy ubuntu.bin to C:\
   2. Go to C:\ and in the explore menubar, go to Tools --> Folder Options --> View and select "Show hidden files and folders" and uncheck the "Hide protected Operating System Files" box and apply these changes.
   3. You should now see a Boot or Boot.ini file in C:\. Right click on it and under properties, uncheck the "Read-Only" box.
   4. Open the C:\Boot.ini file with Notepad (or some other text editor) and make the last line:
      C:\ubuntu.bin="Ubuntu Linux"
      Note that you may have to add this line or their may already be a similar line that says something about an "Unknown Operating System" that you can modify. Also, I'd recommend changing the timeout in the Boot.ini file to be something like 5 or 10 instead of 30.
   5. Make the Boot.ini "Read-Only" again. You can also make the ubuntu.bin file "Read-Only" and "Hidden" as well. 

# Reboot the computer. This time, you should see a a screen during booting that ask you to choose between Windows and Ubuntu Linux. Choose Ubuntu Linux and let the Ubuntu install process finish (this took about half an hour on my laptop). 


Note that, if you are currently using GRUB, you will need to replace it with the Windows MBR by booting from the XP Installation Media, pressing "r" to enter the recovery console, and then typing:

```
fixmbr
```

Then follow the guide above. You may want to copy the files first, or otherwise, install the [FS- Driver]("http://www.fs-driver.org/") which will allow you to access Ext2/ Ext3 partitions.

---

### Post by ManyBeers on 2008-09-11
> **WRDN said:**
> Using [this]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") guide, the instructions for adding Ubuntu to the Windows MBR are as follows:



Note that, if you are currently using GRUB, you will need to replace it with the Windows MBR by booting from the XP Installation Media, pressing "r" to enter the recovery console, and then typing:

```
fixmbr
```

Then follow the guide above. You may want to copy the files first, or otherwise, install the [FS- Driver]("http://www.fs-driver.org/") which will allow you to access Ext2/ Ext3 partitions.

I understand all of that guide there. What I need to know is how to make the copy of Ubuntu.bin count 446 to my shared Fat32 drive which is called Fatty. The command would look sinilar to this:
dd if=/dev/hda2 of=/mnt/share/ubuntu.bin bs=446 count=1. This is just 
an example and was copied from a guide I was reading. He is using
System Rescue cd and is mountuing his shared drive in the command. I will do this from within Ubuntu

---

### Post by bodhi.zazen on 2008-09-11
You copy a file from the command line with cp.


cp file destination

mount your C drive

sudo cp /path/to/ubuntu/bin /path/to/C_drive

Or as WRDN suggested, use gksu nautilus

---

### Post by ManyBeers on 2008-09-11
Can somebody show me how to do this task with the System Rescue CD?

---

### Post by milasch on 2008-09-11
Use
```

fdisk -l

```
to list all your partitions

identify your FAT32 partition where windows is installed.

then mount your FAT32 partition (lets say it is /dev/hda1)
```

sudo mount -t auto /dev/hda1 /mnt/

```

find where's the ubuntu.bin file, and copy it to your ntfs partition:

```

sudo cp /path/to/ubuntu.bin /mnt

```

Be careful with dd, you can wipe your hd easily with it.

---

### Post by ManyBeers on 2008-09-11
Bump.I need an expert here who knows if a file in my computers MBR which is where Grub is can be copied from while Ubuntu is running.

---

### Post by bodhi.zazen on 2008-09-11
> **ManyBeers said:**
> Bump.I need an expert here who knows if a file in my computers MBR which is where Grub is can be copied from while Ubuntu is running.

LMPPO !!!!!

What we have here is a failure to communicate. I was distracted by the nature of your question.

WRDN posted the solution some 5 hours ago. You do not copy an ubuntu.bin file, you write one on windows.

See post #5 for detailed step-by-step instructions.

/me thanks WRDN

---

### Post by bodhi.zazen on 2008-09-11
> **WRDN said:**
> Everything that has a Beginning, has an End

Not a circle ...

---

### Post by ManyBeers on 2008-09-11
> **bodhi.zazen said:**
> LMPPO !!!!!

What we have here is a failure to communicate. I was distracted by the nature of your question.

WRDN posted the solution some 5 hours ago. You do not copy an ubuntu.bin file, you write one on windows.

See post #5 for detailed step-by-step instructions.

/me thanks WRDN

No need to get hot! I am trying to get some help is all. If you know what I need to do then help me do it. I need to do this with the dd command like it is done in this tutorial [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")
using SystemRescue cd and not being booted into Ubuntu.

---

### Post by bodhi.zazen on 2008-09-11
I am not hot, I am LOL

Read the post I referred to it explains how to configure your system.

---

### Post by ManyBeers on 2008-09-11
> **bodhi.zazen said:**
> I am not hot, I am LOL

Read the post I referred to it explains how to configure your system.
That only explains what to do once Ubuntu.bin is on my Windows Fat32 shsred drive. My problem is getting Ubuntu.bin to that shared drive. Will you help me with that using the dd command? I believe it is actually the first 446 bytes of Grub's stage1

---

### Post by ManyBeers on 2008-09-12
Hey guys. Me again.

---

### Post by bodhi.zazen on 2008-09-12
I would if I could, but I know next to nothing about windows. You seem quite determined to follow a guide that does not seem to be working for you.

I would be more then happy to help you use tools I am familiar with , such as GRUB.

Grub is the default boot loader for Ubuntu, and in fact many Linux distros. Grub will boot almost any operating system, including windows. I know grub and grub works out of the box in the vast majority of installations.

So why not pop in the Ubuntu CD and install it the Ubuntu way ? IMO you are going about this the hard way.

You might have better luck with the windows boot loader on Windows forums or Microsoft. Perhaps if you contacted Microsoft support they will walk you through configuring their boot loader to boot Ubuntu.

---

### Post by ManyBeers on 2008-09-12
> **bodhi.zazen said:**
> I would if I could, but I know next to nothing about windows. You seem quite determined to follow a guide that does not seem to be working for you.

I would be more then happy to help you use tools I am familiar with , such as GRUB.

Grub is the default boot loader for Ubuntu, and in fact many Linux distros. Grub will boot almost any operating system, including windows. I know grub and grub works out of the box in the vast majority of installations.

So why not pop in the Ubuntu CD and install it the Ubuntu way ? IMO you are going about this the hard way.

You might have better luck with the windows boot loader on Windows forums or Microsoft. Perhaps if you contacted Microsoft support they will walk you through configuring their boot loader to boot Ubuntu.

Ubuntu has been on my computer for several days with Grub as 
the bootloader and everything works quite well. I don't have any problems with Grub. I just want to have the option to make Windows ntldr the boot manager. To do so i need run the dd
command on the drives boot sector to get the first 446 bytes
from stage 1. That file once it is placed in WindowsC:\drive
is what boots Linux.

---

