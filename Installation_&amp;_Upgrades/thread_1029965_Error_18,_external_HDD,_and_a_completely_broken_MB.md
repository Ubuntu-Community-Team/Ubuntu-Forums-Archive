---
title: "Error 18, external HDD, and a completely broken MBR"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Asday on 2009-01-03
My problem seems similar to many others', but mine hasn't been solved by any of the other solutions posted, so forgive the repetition.

I attempted to install Ubuntu to an external IDE drive (connected via USB) and overwrote the MBR on my internal hard drive, due to the option being mildly hidden.  This has annoyed me, and left me with an unbootable computer.  I'll be attempting to fix this with the supergrub disc later, so that's not the point of this post.

I reinstalled Ubuntu, and made the bootloader reside on the correct hard drive this time, and after numerous re-partitions, and google searches, I'm stuck with an Error 18.

I've got a 4GiB /boot partition at the beginning of the drive, so it shouldn't be a problem, as far as I can tell, but apparently it is.

Also, it's insistent on including the internal hard drive on the device.map, even though the external HDD will be moving between PCs, I'm guessing.  If this isn't trivial to fix, however, I don't mind that much.

Here's a screenshot of the partitioning job I hashed together.  (Oh yeah, I've been playing around with flags, aswell, but they don't seem to change anything.)

[IMG]http://sara.and.zuka.googlepages.com/screenie.png[/IMG]

---

### Post by logos34 on 2009-01-04
> **Asday said:**
> overwrote the MBR on my internal hard drive, due to the option being mildly hidden.  This has annoyed me, and left me with an unbootable computer.  I'll be attempting to fix this with the supergrub disc later, so that's not the point of this post.

I reinstalled Ubuntu, and made the bootloader reside on the correct hard drive this time, and after numerous re-partitions, and google searches, I'm stuck with an Error 18.

I've got a 4GiB /boot partition at the beginning of the drive, so it shouldn't be a problem, as far as I can tell, but apparently it is.

Also, it's insistent on including the internal hard drive on the device.map...

don't worry about device.map, just a record of discs detected at installation time, doesn't affect boot

Check this out:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

i.e.:
> BIOS settings
If you don't think the BIOS date could be your problem, or there is no more modern BIOS flash available for your BIOS, then at least check and make sure your hard disk is being correctly detected and set up in the BIOS.
Quote:
" I had the same problem. Error 18 and After GRUB. The solution is in the bios.
Put the hard disk detection on auto and not on user. It did the trick for me."

 * Make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.
Remember, the old 8.0 GB limit was overcome when the old CHS (Cylinder, Heads, Sectors) method for dealing with hard disk addressing (disk geometry) was replaced by LBA (Logical Block Addressing). (Numbering each sector of the hard disk starting with the MBR and counting upwards).  

just curious: what do you have in /boot (sdb8) that's taking up 2.2 gb?

---

### Post by Asday on 2009-01-04
Aye, in my BIOS settings, the only thing like that is something likea choice between "Bit-Shift" which is the default, or "LBA assisted".

The HDD is being properly recognised and switching that option around makes no difference.

Also, I have no idea what's taking up that much space.  It installed like that.

---

### Post by logos34 on 2009-01-04
Did you install 8.10?  (if not, i'm thinking it could be  the 'root' line in menu.lst--maybe it's set for 'hd1,?; instead of 'hd0,?')

---

### Post by Asday on 2009-01-04
Yes, I installed 8.10, should I post my menu.lst here?

---

### Post by caljohnsmith on 2009-01-04
This is just an idea, but there was another case in the forums just a few weeks ago where someone was getting a Grub error 18 even though all their Grub and boot files should have been within reach of BIOS, and surprisingly the issue was resolved by converting the Grub/Ubuntu partition from a logical partition into a primary partition. Have you tried making your boot partition a primary partition rather than a logical one, Asday? Maybe that will work for you too.

---

### Post by logos34 on 2009-01-04
> **Asday said:**
> Yes, I installed 8.10, should I post my menu.lst here?

no, because in that case it's using UUIDs (partition ID), so that can't be source of problem.  Wonder what it could be...

---

### Post by Asday on 2009-01-04
> **caljohnsmith said:**
> This is just an idea, but there was another case in the forums just a few weeks ago where someone was getting a Grub error 18 even though all their Grub and boot files should have been within reach of BIOS, and surprisingly the issue was resolved by converting the Grub/Ubuntu partition from a logical partition into a primary partition. Have you tried making your boot partition a primary partition rather than a logical one, Asday? Maybe that will work for you too.

I'm all for ideas, I'll try that, and post back.  What's the difference, by the way?

EDIT:  The option to make it a primary partition is grayed out.  Help?

---

### Post by caljohnsmith on 2009-01-04
> **Asday said:**
> I'm all for ideas, I'll try that, and post back.  What's the difference, by the way?

EDIT:  The option to make it a primary partition is grayed out.  Help?
You'll need to delete your current sdb8 boot partition, and then shrink your sdb2 extended partition from the beginning in order to free up space at the beginning of the drive for a primary partition. Also, be sure to right-click the swap partition and select "swapoff" so that doesn't prevent you from resizing sdb2. Let us know how that goes.

---

### Post by Asday on 2009-01-04
Ach, that means unmounting everything, dain't it?  That's annoying, I'm listening to music on sdb5, right, gimme ten minutes, and I'll partition everything up again.

Also, where did the extended partition come from?

---

### Post by caljohnsmith on 2009-01-04
> **Asday said:**
> Ach, that means unmounting everything, dain't it?  That's annoying, I'm listening to music on sdb5, right, gimme ten minutes, and I'll partition everything up again.

Also, where did the extended partition come from?
I assume you are going to reinstall Ubuntu, is that true? If not, then please don't delete your boot partition.

---

### Post by Asday on 2009-01-04
Hehe, yeah, don't worry, I'm going to reinstall.  I still havn't managed to boot into my original installation, so nothing to lose.

Also, it appears this session's having a problem with unmounting one of the partitions, and it keeps automounting the others, so it looks like I'm going to have to restart the computer, and set up the session again.  Aah, livediscs...  :(

EDIT:  Ok, it's half fixed itself somehow, but apport and command-not-found are still crashing, so I'll reboot after the install.  The repartitioning went well, and extremely fast.

EDIT2:  Yeah, the launcher for the installer's died, and "ubiquity" has crashed.  I'll restart now.

EDIT3:  Right, everything's installing now, all going smoothly.  As always.

EDIT4:  The good news:  It boots!

The bad news, and there's alot of it:

When trying to boot into Ubuntu, I get this message:

```
Boot from (hd0,0) ext3 d6b47d15-3eea-4fab-92b5-9e03eefdf96b
Starting up ...
[    0.744111] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Which I'm *guessing* can be solved by moving the / partition out of the extended one, but I'm a newbie, so I'm not planning on doing that without it being suggested.

When attempting to boot longhorn vista, which is fairly essential at this moment in time, I get a message along the lines of:  "Unsupported executable!" and it goes no further.

When attempting to boot Ubuntu recovery mode, I get a huge amount of text, ending with some lines I believe are relevant, so I've copied them down:

```
[    0.756098] VFS: Cannot open device "UUID=25700532-3057-479f-aa0a-d054be68dbd7" or unknown-block(0,0)
[    0.756179] Please append a correct "root=" boot option; here are the available partitions:
[    0.756261] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

So yeah.  Thanks for helping so far, by the way, peoples.

---

### Post by Asday on 2009-01-04
[SIZE="1"]And a cheeky post here, because I'm not sure that editing bumps the thread and/or sends out subscription notification emails.[/SIZE]

---

### Post by caljohnsmith on 2009-01-04
It sounds like maybe your Ubuntu didn't fully install; did the installer finish and say it was successful, or did it give some error messages?

---

### Post by fgjhgkj on 2009-01-04
Online Shops for you Low price!  high-quality!!  good prestige!!!
	
Hello! welcome to our website; [www.shoes-trader.com](www.shoes-trader.com)

we can supply low price with high quality products.You can view our website for the details. 
Thanks for your reading , pls email us if u have any questions about business . 

We hope that will make a long&great business with you in future.
Your satisfactions,Our pursuit!	
Please Email me to get discount!!
:popcorn::popcorn::popcorn:

---

### Post by Asday on 2009-01-04
Yeah, it said it finished, it popped up with the little "Restart and use Ubuntu, or continue using the live disc?" message.

It said in the final stages of the installation that it was moving, or copying the installation logs or something, should I post those, and if so, where would I find them?

---

### Post by caljohnsmith on 2009-01-04
When you boot the Live CD, did you try the option at the first main menu to check the CD for defects? I would give that a try. If that doesn't turn anything up, maybe you could use the Alternate Install CD to install Ubuntu instead.

---

### Post by Asday on 2009-01-04
CD's got no defects, I checked that one before.

As for the alternate CD install:  No go.  My one and only drive is being taken up with the live disc.  My next access to a CD burner is quite a way away.

You're sure it's nothing to do with / being on the extended partition?

---

### Post by caljohnsmith on 2009-01-04
> **Asday said:**
> CD's got no defects, I checked that one before.

As for the alternate CD install:  No go.  My one and only drive is being taken up with the live disc.  My next access to a CD burner is quite a way away.

You're sure it's nothing to do with / being on the extended partition?
Putting the main Ubuntu partition (i.e. the root / partition) in the extended partition should not make any difference, but you could try making it a primary partition instead. You could either wipe the drive clean and set up your partitions, or you could delete the present Ubuntu partition, shrink the extended partition, and then create a new primary partition with the unallocated space.

---

### Post by Asday on 2009-01-04
Wiping the disc is also a no, so I'll attempt the second option.

EDIT:  Ok, I mucked around with the partitions, and reinstalled again, and now I can boot into Ubuntu.  Joy!

Thing is, it still won't let me boot into longhorn vista...

---

### Post by Asday on 2009-01-04
[SIZE="1"]Another cheekypost.[/SIZE]

---

### Post by caljohnsmith on 2009-01-04
OK, how about first posting the output of the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Vista.

---

### Post by Asday on 2009-01-04
I think I've attached the results.

Also, it appears Ubuntu's duplicated it's boot entry, only it's swapped a 7 for a 9.  Should I be worried?  (I saw what I'm referring to in the results.txt)

---

### Post by caljohnsmith on 2009-01-04
OK, how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And then delete your Vista entries, and replace them with:
```
title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try Vista from your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by Asday on 2009-01-04
Forgive me, I'm fairly new to this, and I know that menu.lst is a fairly vital file, could you let me know what that does, please?

> ```
title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

---

### Post by caljohnsmith on 2009-01-04
> **Asday said:**
> Forgive me, I'm fairly new to this, and I know that menu.lst is a fairly vital file, could you let me know what that does, please?
No problem; the menu.lst is the Grub file that contains all the information about which OSes are displayed in your Grub menu on start up, and how Grub should go about booting those various OSes. If it makes you feel better, you can first backup your current menu.lst by doing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
But modifying the menu.lst is usually not a big deal. :)

---

### Post by Asday on 2009-01-04
I don't know what kind of unholy magic you just worked, but you are now my god, in a convenient human-shaped package.  Allow me to explain.

The screen went black, then longhorn vista booted.

Also, what you said about device.map is confusing me.  If it has no effect, then why, when I attempt to boot from the internal HDD, with the external HDD unplugged, do I get an error 21, whereas when I do the same, only with the external HDD plugged in, do I get an error 18?

Also, if that can be fixed without mucking around with the partitions, that would be supreme, as it would completely fix my computer.

---

### Post by caljohnsmith on 2009-01-04
> **Asday said:**
> I don't know what kind of unholy magic you just worked, but you are now my god, in a convenient human-shaped package.  Allow me to explain.

The screen went black, then longhorn vista booted.

Also, what you said about device.map is confusing me.  If it has no effect, then why, when I attempt to boot from the internal HDD, with the external HDD unplugged, do I get an error 21, whereas when I do the same, only with the external HDD plugged in, do I get an error 18?

Also, if that can be fixed without mucking around with the partitions, that would be supreme, as it would completely fix my computer.
That's great news Vista booted OK from Grub. The reason why you are getting a Grub error 21 when you disconnect your Ubuntu drive is because you have Grub installed to the MBR of your Vista drive too. To correct that problem, you can do the following:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That installs a Windows equivalent MBR to your sda Vista drive, so if you disconnect your Ubuntu drive, you should be able to boot straight into Vista again. How about giving that a shot and let me know how it goes. :)

---

### Post by Asday on 2009-01-04
I already plan to use the supergrub disc to restore the MBR, will installing lilo scupper my plans in any way?

---

### Post by caljohnsmith on 2009-01-05
> **Asday said:**
> I already plan to use the supergrub disc to restore the MBR, will installing lilo scupper my plans in any way?
It should not be a problem at all, you can do either to restore a Windows equivalent MBR. The Super Grub Disk uses "syslinux" rather than lilo, but they both do the same thing: they "chainload" or boot the boot sector of whichever partition is marked active (i.e. has the boot flag set) in the MBR partition table, just like a Windows MBR. So either way should work just fine. :)

---

### Post by Asday on 2009-01-05
Worked like a charm, thanks!

---

