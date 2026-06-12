---
title: "Now Windows Wont Start"
date: 2008-08-05
forum: General Help
---

### Post by Ninjames on 2008-08-05
I installed Ubuntu last night and all was well. It got 16 GB out of my computers 177. After installing I was able to boot up WIndows XP Media Center no problem, I checked this a few times to make sure.

Now when I shut down my computer, and turn it back on again and I select my installation of Windows to boot it doesn't work. I get a "Windows could not start up normally" or something along those lines and the options to:

Start from Safe Mode
Safe mode with networking
Safe mode with command prompt

Last known good configuration

Start Windows normally

The safe modes greet me with a blue screen telling me to CHKDSK.

Last known good configuration and start Windows normally just restart my PC again. I get the loading HP screen, with the option for system recovery with F10, which does nothing because it skips that and goes to the grub loader.

Also, after selecting my Windows OS I get the option for "Windows Media Center Recovery Console" which doesn't load correctly, I get a blue screen.

I had a backup partition (D:) that came preinstalled on this PC that I've used to reinstall windows before, but I cant seem to access it.

I don't have a Windows disc, save for a OEM Home Edition install and yeah... Anything I can do right now to fix my Windows XP? None of my data seems to be affected as I can access it from within Ubuntu.

---

### Post by Qchan on 2008-08-05
> **Ninjames said:**
> I installed Ubuntu last night and all was well. It got 16 GB out of my computers 177. After installing I was able to boot up WIndows XP Media Center no problem, I checked this a few times to make sure.

Now when I shut down my computer, and turn it back on again and I select my installation of Windows to boot it doesn't work. I get a "Windows could not start up normally" or something along those lines and the options to:

Start from Safe Mode
Safe mode with networking
Safe mode with command prompt

Last known good configuration

Start Windows normally

The safe modes greet me with a blue screen telling me to CHKDSK.

Last known good configuration and start Windows normally just restart my PC again. I get the loading HP screen, with the option for system recovery with F10, which does nothing because it skips that and goes to the grub loader.

Also, after selecting my Windows OS I get the option for "Windows Media Center Recovery Console" which doesn't load correctly, I get a blue screen.

I had a backup partition (D:) that came preinstalled on this PC that I've used to reinstall windows before, but I cant seem to access it.

I don't have a Windows disc, save for a OEM Home Edition install and yeah... Anything I can do right now to fix my Windows XP? None of my data seems to be affected as I can access it from within Ubuntu.

[b][color=darkred]
This is definitely a Windows problem and not a Ubuntu problem. You simply need to run a chkdsk on your PC to clean it up.

You'll need the Windows XP CD to boot into Recovery mode. Once you're there, you have to type chkdsk /r

If you don't have a Windows XP CD, then you can download Bart's PE... 9 times out of 10, you'll need the Windows XP CD to do it... Unless you can find other means....
[/b][/color]

---

### Post by Ninjames on 2008-08-05
Well, I know its a Windows problem.. But the problem obviously was derived from installing Ubuntu, so I figured this was where I'd get help--from people who know how to use Ubuntu. The installation (and possibly update, since it occurred after updating) of Ubuntu destabilized my Windows. I'd really appreciate some help and thanks for your response thusfar.

I loaded up my Windows XP Home CD I have and loaded up the Recovery Console. It was accessing my D: drive which id good, considering that's where I know my backup is. I ran chkdsk /r and it said one or more errors were found. But it didn't say anything about fixing or cleaning these errors? Then I restarted and tried Windows and got all the same error messages.

Any help would be appreciated. I really enjoy using Ubuntu, I prefer it vastly to Windows, but unfortunately I NEED Windows on this PC.

---

### Post by ktrnka on 2008-08-05
You could run 
```
sudo ntfsfix /dev/sda2
```
where /dev/sda2 would be your ntfs windows partition.

If it can't find the command, you will need to install ntfsprogs

```
sudo apt-get install ntfsprogs
```

---

### Post by Ninjames on 2008-08-05
Um.. see that's the thing, I'm a complete novice, I don't know how to run those commands right there, or what my windows partition would be called within that command. Could you tell me how to run those and how to find exactly what I need to put?

I know I followed the installation instructions exactly as I was supposed to, though. Jus' saying.

---

### Post by ktrnka on 2008-08-05
One more thing. If you don't know what partition is Windows, run ```
sudo fdisk -l
```

to list the partitions.

Look for NTFS.

To run the commands open a terminal at

Applications>Accessories>Terminal

---

### Post by ownaginatious on 2008-08-05
That's what happens when you dual boot an OS. Ubuntu probably overwrote the boot sector. I think it's a result of installing GRUB... not sure. To fix this problem, you have to get a hold of a Windows XP install CD; any should be fine. Boot the install CD and run the repair thing. It will correct the problem in about two seconds.

At least, that's how it works with Vista. I have never tried dual booting with XP, so I don't know if the install CD can repair problems easily like that.

---

### Post by FTBPrimeEvil on 2008-08-05
If you windows won't start, what's the problem? if you can log into Ubuntu then you are ok.:)

---

### Post by lisati on 2008-08-05
Hmmmm.. thinks for a moment.....

When I've installed Ubuntu for dual-boot, resized a Windows partition or something of that nature, XP has complained to me that CHKDSK needs to run. Usually it is happy to run CHKDSK for me and then restart. Note: it's a good idea to defrag your Windows partition before resizing it. 

Yesterday, I had the blue screen on my desktop on booting two or three times (I hadn't used the machine for a few days, it had been working before), solved for the moment by logging into safe mode and removing some software, rebooting, and reinstalling the ones I wanted to keep.

---

### Post by rfdeshon on 2008-08-05
> **ownaginatious said:**
> That's what happens when you dual boot an OS. Ubuntu probably overwrote the boot sector. I think it's a result of installing GRUB... not sure. To fix this problem, you have to get a hold of a Windows XP install CD; any should be fine. Boot the install CD and run the repair thing. It will correct the problem in about two seconds.

At least, that's how it works with Vista. I have never tried dual booting with XP, so I don't know if the install CD can repair problems easily like that.

I've set up dual boot XP/Linux PCs with GRUB dozens of time and grub has NEVER caused any problems with the windows partition. Most likely, the fact that he had to shrink his windows partition caused windows to freak out (I HAVE seen this) and a chkdsk will usually fix it.

Also, Ubuntu did not break your windows partition. Windows most likely broke your Windows partition. Unless you specifically tell Ubuntu to do something on your Windows partition, nothing you do in Ubuntu will affect it. Take the advice above, chkdsk it, Windows most likely corrupted some of it's own files. It's prone to do that and I've seen it happen a number of times before even when I was not dual booting.

=EDIT=
Also, if push comes to shove and you have to reinstall, don't let Windows use the whole disk. I've found that Windows often doesn't like when it's primary partition is resized and it will start corrupting it's file indexes, which causes problem similar to what you have been describing. If you reinstall, figure out how much space you want for Win and how much for Ubuntu. Install Windows and have it set up it's partition to the size you want Windows to use (about 100GB from the sound of it) then, when you install Ubuntu, have it use the remaining free space. This should mitigate the problem of Windows freaking out over it's primary partition being resized.

---

### Post by ktrnka on 2008-08-05
> **rfdeshon said:**
> I've set up dual boot XP/Linux PCs with GRUB dozens of time and grub has NEVER caused any problems with the windows partition. Most likely, the fact that he had to shrink his windows partition caused windows to freak out (I HAVE seen this) and a chkdsk will usually fix it.

Also, Ubuntu did not break your windows partition. Windows most likely broke your Windows partition. Unless you specifically tell Ubuntu to do something on your Windows partition, nothing you do in Ubuntu will affect it. Take the advice above, chkdsk it, Windows most likely corrupted some of it's own files. It's prone to do that and I've seen it happen a number of times before even when I was not dual booting.> **lisati said:**
> Hmmmm.. thinks for a moment.....

When I've installed Ubuntu for dual-boot, resized a Windows partition or something of that nature, XP has complained to me that CHKDSK needs to run. Usually it is happy to run CHKDSK for me and then restart. Note: it's a good idea to defrag your Windows partition before resizing it. 

Yesterday, I had the blue screen on my desktop on booting two or three times (I hadn't used the machine for a few days, it had been working before), solved for the moment by logging into safe mode and removing some software, rebooting, and reinstalling the ones I wanted to keep.

I agree totally agree with both of you, I just didn't want to type that much! I have seen problems occur when the NTFS partition is resized without windows being defragged first.

---

### Post by ownaginatious on 2008-08-05
> **rfdeshon said:**
> I've set up dual boot XP/Linux PCs with GRUB dozens of time and grub has NEVER caused any problems with the windows partition. Most likely, the fact that he had to shrink his windows partition caused windows to freak out (I HAVE seen this) and a chkdsk will usually fix it.

Also, Ubuntu did not break your windows partition. Windows most likely broke your Windows partition. Unless you specifically tell Ubuntu to do something on your Windows partition, nothing you do in Ubuntu will affect it. Take the advice above, chkdsk it, Windows most likely corrupted some of it's own files. It's prone to do that and I've seen it happen a number of times before even when I was not dual booting.

=EDIT=
Also, if push comes to shove and you have to reinstall, don't let Windows use the whole disk. I've found that Windows often doesn't like when it's primary partition is resized and it will start corrupting it's file indexes, which causes problem similar to what you have been describing. If you reinstall, figure out how much space you want for Win and how much for Ubuntu. Install Windows and have it set up it's partition to the size you want Windows to use (about 100GB from the sound of it) then, when you install Ubuntu, have it use the remaining free space. This should mitigate the problem of Windows freaking out over it's primary partition being resized.

Ya, I forgot to mention this is when resizing the partition. Unlike resizing utilities (i.e. acronis), it appears that Ubuntu does like to fix Windows after resizing it. It would rather just let windows die :d.

EDIT: Be cautious when allowing chkdsk to fix the partition. Chkdsk, at least when I had Windows 2000, seems to like to fix drive problems by simply deleting problem files rather than attempting to repair them. Screwed up my file server hard drive pretty bad it did.

---

### Post by ktrnka on 2008-08-05
ownaginatious: I'm not complainin. :) Though it's hard on the new people if they aren't completely comfortable in the Linux environment yet.

---

### Post by Ninjames on 2008-08-05
-Sweat.- Well. I tried that ntfsprog thing, restarted, still getting errors.

I laoded up a Windows CD I have and ran CHKDSK from both directories I was able to. After it said it was complete I typed "EXIT" and then restarted. Nothing was changed.


Anymore ideas other than CHKDSK? -sweat.- Sorry guys, I'm loving Ubuntu but this computer is shared and I need Windows.

If I reinstall Windows (IE following the setup to get Windows ready for my computer, rather than presisng R for recovery console) will it erase my data? I have a few gigs of data I don't want to lose, and then another 60 gigs of music on top of that I cant possibly live without.

Any more suggestions on fixing this? I assume its because I partitioned... augh.. what can I do, guys?

---

### Post by ktrnka on 2008-08-05
Try to get a hold of BARTPE and/or DUBCD2.0

They will be your last hope, otherwise:

Backup you windows stuff from the ubuntu side to a network drive or external drive. Reinstall windows. Then boot the ubuntu live cd and open a terminal.
Run this to restore GRUB
```
sudo grub
```

```
root (hd0,1)
```

hd0 being the first drive and 1 being the second partition: hopefully your ubuntu installation 

```
find /boot/grub/stage1
```

```
setup (hd0)
```

then reboot you machine.

---

### Post by Ninjames on 2008-08-05
If I get this BartPE thing, what do I do once I get it? It'll let me load up Windows, yeah? What do I do from there?


Another note, will uninstalling Ubuntu and removing the partition fix the problem?

I'm able to restore Windows because I have a recovery console I can use via the GRUB loader called "Windows NT/2000/XP" but that will delete all my data.

Please help just a bit longer, folks, and if it doesn't work... Can anyone help me locate an external drive to get? Also, if it comes down to it and I install Windows again, Ubuntu will still be on the PC? And that grub thing will be to allow me to boot it again?

Ugh this really sucks. I'm never experimenting with another OS again. xD I'll stick to Windows. I'm certain Windows messed itself up, but it did so because of Ubuntu.. I dunno, anymore suggestions, help, etc? WHat to do with BartPE? Defrag, chkdsk.. what?

---

### Post by Ninjames on 2008-08-05
How do I get BartPE from within Ubtuntu? Everything seems to be a windows exe.


Also.. if I just want to reinstall.. But I cant afford to get an external drive.. Is there any way I can uhm.. Say compress my MY Music folder (50GB) into several zipped files (THAT A WINDOWS PROGRAM CAN READ)and burn them as data to DVDs? Blank DVD can hold 4.7 GB can I write all of it as data to those, if so, what program in Ubuntu do I use to zip and write the files. I have approx. 30 blank DVDs so I have enough space altogether. Would that work? How do I do it?

I'd like to solve my problem if possible before reinstalling, however, now that I've established I CAN reinstall.

---

### Post by Ninjames on 2008-08-05
> **ktrnka said:**
> Try to get a hold of BARTPE and/or DUBCD2.0

They will be your last hope, otherwise:

Backup you windows stuff from the ubuntu side to a network drive or external drive. Reinstall windows. Then boot the ubuntu live cd and open a terminal.
Run this to restore GRUB
```
sudo grub
```

```
root (hd0,1)
```

hd0 being the first drive and 1 being the second partition: hopefully your ubuntu installation 

```
find /boot/grub/stage1
```

```
setup (hd0)
```

then reboot you machine.

Another thing (GUys I'm SO sorry for all these questions, but thank you for continuing to help me.) I know for sure that my computer has about 8GB aside on a partition labeled D: in windows for my recovery. Does that mean Ubuntu would then instead be the THIRD partition (when I get to this step)

Sorry again, but thanks.

---

### Post by Ninjames on 2008-08-05
Don't forget about me, guys!


ONE LAST QUESTION: (I think. ><)

When I started the recovery (didn't finish it) it said "Recovery will delete all data and files and replace them with original windows files blah blah"

Does that mean Ubuntu is gone? Or will Ubuntu still be there, as its technically partitioned off? Will using the live CD and terminal bring it back after all that or should I try reinstalling it completely after I reinstall Windows?

---

### Post by Ninjames on 2008-08-05
Please help guys, with just a few more pieces of information?

I guess I'm set on reinstalling Windows, but I need to know just a few things please. D:


1. When I make the zip files in Ubuntu of my files, this isn't like.. a weird.. linux only zip file right? Windows or WinRAR once I Have my computer back up will handle it fine, yes?

2. After I reinstall windows, it says it deletes everything. Does that include the Ubuntu partition?

3. My method of backup, using DVD discs and zip files will work, right? o.O

Thanks.

---

### Post by Qchan on 2008-08-06
[b][color=darkred]
If chkdsk doesn't help, then you have either 1) A driver issue or 2) a hardware issue. Try booting Windows into Safe Mode and see if you can get in that way. If so, you need to set up Windows XP so it doesn't reboot once you get a BSOD. To do that:

Click Start --> Right click on My Computer --> Properties.
Click the Advanced Tab and click the settings button for Startup and Recovery.

Make sure the "Automatically Restart" box is unchecked. Then Click OK and then click OK once again to close both Windows. Reboot your PC and try to boot into normal mode. Once the BSOD appears, read under the technical details. That will let us know what's going on.
[/b][/color]

---

