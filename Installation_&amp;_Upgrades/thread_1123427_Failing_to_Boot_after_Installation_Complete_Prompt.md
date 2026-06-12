---
title: "Failing to Boot after Installation Complete Prompt"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by poorbarry on 2009-04-12
I've run through the installation procedure at least a half dozen times...but I cannot successfully boot from my hard drive after the prompt to remove the CD and restart the system.

Running from the "Live CD" works great.  I just can't get the thing to install.

I am not trying to dual boot anything.  I want only Ubuntu on this PC (AMD Processor, ASUS motherboard, 512MB RAM, 120GB SATA hard drive).

When it comes to disk partitioning, I have selected "Guided -- Use entire disk" option.

After each attempt to run thru the installation process and rebooting, I have seen one of the following errors:

grub loading stage1.5 read error
or
grub loading stage2 read error

Since millions have successfully installed this, I'm sure I am doing something stupid.  I would GREATLY appreciate it if somebody can help me get this working!

Thanks in advance for any help!!!

---

### Post by coffeecat on 2009-04-12
> **poorbarry said:**
> Since millions have successfully installed this, I'm sure I am doing something stupid.

I don't think you are. I think you've uncovered a very obscure bug. Installing from the 'guided - use entire disk' option should be entirely pain-free so long as the live CD ran OK - which it did.

Two thoughts. There may be a problem with your specific motherboard. Post details and search the forum for the particular model to see if others have had successes or failures with it. Asus is quite popular with Linux people.

By the way, which version of Ubuntu is this? 8.04, 8.10, 9.04Beta, or an earlier one? It might be worth trying a different release.

Second thought - focussing on the grub issue. It sounds as though grub hasn't installed properly. Boot up from the live CD, go to Applications > Accessories > Terminal, and then issue this command and post the output:

```
sudo fdisk -l
```With this information we can try repairing grub, but I don't hold out much hope. If you can get internet connection while in the live CD, you can copy and paste from the terminal output. Check the terminal Edit menu - keyboard shortcuts are slightly different: Shift-Ctrl-C for copy.

---

### Post by coffeecat on 2009-04-12
Another thought. Grub (the boot manager) is divided into stages 1, 1.5 and 2, each stage calling the successive one.

Grub stage 1 is only a little more than 400bytes in size so errors are of necessity somewhat taciturn. From the grub manual:

> 
**14.1 Errors reported by the Stage 1**

  The general way that the Stage 1 handles errors is to print an error string and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot.     
The following is a comprehensive list of error messages for the Stage 1:       

Hard Disk Error
The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.       

Floppy Error
The stage2 or stage1.5 is being read from a floppy disk, and the attempt to determine the size and geometry of the floppy disk failed. It's listed as a separate error since the probe sequence is different than for hard disks.       

[B]Read Error
A disk read error happened while trying to read the stage2 or stage1.5.       [/B]

Geom Error
The location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls.  This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install).I wonder if you've got a dodgy hard drive there, with bad sectors where grub stages 1.5 and 2 have been written. Have you got another SATA drive you could try out, even as temporary experiment?

---

### Post by poorbarry on 2009-04-12
> **coffeecat said:**
> There may be a problem with your specific motherboard. Post details and search the forum for the particular model to see if others have had successes or failures with it. Asus is quite popular with Linux people.

By the way, which version of Ubuntu is this? 8.04, 8.10, 9.04Beta, or an earlier one? It might be worth trying a different release

Thanks for the quick reply...and help.  Its greatly appreciated.

As for more specifics:
- ASUS A7S8X-MX (Socket A)
- Ubuntu Desktop version 8.10 (I burned the CD, checked the MD5 on the downloaded ISO, and checked the copy integrity of my CD from the "menu" when I booted from the CD.  Everything passed.)

Being a Ubuntu newbie, I haven't yet searched the forums for any known problems with this motherboard...but as per your suggestion, I will.

I will boot again from the live CD, and run your suggested commands, to see what fdisk, to see what it says.

And...thanks for you help!

---

### Post by coffeecat on 2009-04-12
> **poorbarry said:**
> As for more specifics:
- ASUS A7S8X-MX (Socket A)

I've been doing some digging. [From the Asus website]("http://uk.asus.com/products.aspx?l1=3&l2=13&l3=150&l4=0&model=378&modelmenu=2").

That's a fairly old(ish) motherboard so I'm slightly surprised it has a SATA controller. Whatever, the important thing is that it has a SiS chipset, which can be bad news. Obviously not completely bad news because the Ubuntu CD ran live. But if you were choosing a motherboard to run Linux, your last choice of chipset would be SiS. I've seen posts on some forums where with some SiS chipsets the live CD of every distro tried wouldn't even boot up.

Now this may not be the problem, but it's also worth searching for variations of: 

> SiS 741GX
SiS 964 (without RAID) Did you see my second post, where I suggest the possibility of a faulty drive? Or, considering the possibilty that this might be an obscure bug in the driver for the SiS SATA controller, have you a spare ide/ATA (parallel) drive rather than a SATA one you could try?

And a search tip. The search facility on the forum is not as good as doing a google search with:

site:ubuntuforums.org *your search string*.

---

### Post by poorbarry on 2009-04-12
coffeecat,
Thanks...you've given me quite a bit of insight and guidance.  I will do some digging, with the pointers you have provided...and quite possibly buy an IDE drive to try.  They are pretty cheap these days...and easier to install than the motherboard.  Hopefully I can make that work.

Thanks for taking the time to help me out.  And...Happy Easter!

---

### Post by coffeecat on 2009-04-12
Good luck.

> **poorbarry said:**
> and quite possibly buy an IDE drive to try.  They are pretty cheap these days...

Obviously, I can't be sure that's the answer, but if you don't mind the expense.

---

