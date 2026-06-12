---
title: "BIOS and Boot question."
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2009-05-07
I want to install Ubuntu onto a Dell computer but when I go into setup menu there is no option to set cdrom or cdrw in the boot sequence. I contacted Dell and tried several methods to reset the BIOS but none worked. In the boot sequence the only options are ; 1. Floppy, 2. Hard drive. I downloaded the startup files from Dell but it was 1.5Mb, so would not fit on 3.5" floppy 1.44Mb, so that method of booting is no longer an option. I tried it on a CD and Thumbdrive to see (hopefully) if it would boot but it didn't, the lights lit up briefly but defaulted to the HD and loaded Windows 2000.

Currently there is Windows 2000 Professional, password protected (I don't have the password), Dell's Bios number listed as v.A06 and it also shows an Adaptec A1C-7899 BIOS v.25113 (SCSI). This has dual Intel Pentium lll 933Mhz processors (Intel). The primary drive is the SCSI Fujitsu MAJ3091MP Hard drive with a second drive being an EIDE Western Digital WD300 30GB Hard drive. The Fujitsu is connected through the LVD SCSI connector and the Western Digital through the Primary EIDE connector. That is about all the information I have about the computer that I gathered from a visual inspection and by accessing the BIOS Setup.

Now that all that is out of the way, my question is; If I were to format the HD (boot disk) and erase all the OS (Windows 2000) would the computer then seek a new OS bootup file (Ubuntu CD) and install it? Would that allow the seek for startup files begin at the floppy, then CD option. I need to find a workaround to get Windows off this computer and put my OS of choice on. So Windows definitely will go no matter what.
Any help is greatly appreciated and thanks in advance.[COLOR="Red"]****[/COLOR]

---

### Post by logos34 on 2009-05-07
[Smart Boot Manager]("https://help.ubuntu.com/community/SmartBootManager") might be able to fire up the cdrom

---

### Post by dsimpson on 2009-05-07
logos34,

Thanks for the reply, went to site, downloaded extracted but don't know exactly what to do from there. Still looking for instructions on placing onto floppy disk. Can you offer advice on the process.

---

### Post by logos34 on 2009-05-07
either execute the Rawrite app from Start>Run>'CMD' box 

or click on the Rawrite.exe in the extracted folder to start [the gui]("http://www.chrysocome.net/images/rawwrite.png")

Then select Write tab, navigate to the sbm.bin image on the ubuntu CD (or get the img [here]("http://linux.simple.be/tools/sbm")).  Write it to floppy.  Now you have bootable floppy...Boot it on the Dell and you get a menu with CDROM boot option

Or use the **dd if=sbm.bin of=/dev/fd0** if making the floppy on a linux machine

---

### Post by dsimpson on 2009-05-08
I tried the command for linux but wasn't sure how it was done, I used Terminal but and it says No such file or directory. I downloaded and extracted to my desktop but don't know where to go from there, I wasn't able to extract to the floppy and cannot copy to it also. I don't use windows so the Rawrite.exe wouldn't work on my computer. I use Linux exclusively, that is why I am trying to install onto the dual cpu computer.
How do you use the command; dd if=sbm.bin of=/dev/fd0 to install the files onto the floppy?

---

### Post by HyRax on 2009-05-08
The downloaded ISO needs to be burned to a CD first - you will need another computer to do that, or if you can wait a few weeks, use the ShipIt service at ubuntu.com to get an original CD mailed out to you.

As for the Dell machine, can you boot the Ubuntu CD by pressing either ESC or F1, F2, F5, F8, F10 or F12? Most BIOS's will use ONE of these keys to either bring up a boot device menu or will automatically attempt to boot off other devices instead of the HDD.

And I didn't know you could get dual Pentium III boards... you learn something new everyday...

---

### Post by logos34 on 2009-05-08
> **HyRax said:**
> 
As for the Dell machine, can you boot the Ubuntu CD by pressing either ESC or F1, F2, F5, F8, F10 or F12? Most BIOS's will use ONE of these keys to either bring up a boot device menu or will automatically attempt to boot off other devices instead of the HDD.


hope that works for you, though it's odd that the Bios would allow you to boot cdrom when it doesn't list cdrom device the way you first tried.

If no go, post back, we'll sort out the sbm thing...it's normally a very simple procedure

---

### Post by dsimpson on 2009-05-08
No I am not able to change the list of boot options, the only one beside HD is floppy. Is it possible the OS is used to lock it out, it was able to write to the CD's but it doesn't show up in the Setup Menu. The computer was a workstation desktop which ran on its own HD and not linked to a network. Being the primary HD is the SCSI HD, could that have anything to do with the lack of boot options? That is the drive that has Windows 2000 on it and is the default boot HD. I haven't found what the other HD (EIDE) was used for yet.
As for the CD issue, I do have a Gutsy CD with the sbm.bin file in it. Is that the one that is used to install onto the floppy? And it would probably be best to do it step by step if there are many steps to the process so I get it right. I am pretty fair when it comes to following directions although understanding exactly what is transpiring is beyond me a lot of the times. Appreciate the help, thanks to you both.

---

### Post by logos34 on 2009-05-08
> **dsimpson said:**
> 
As for the CD issue, I do have a Gutsy CD with the sbm.bin file in it. Is that the one that is used to install onto the floppy? 

yes, that's it...Just about any ubuntu live cd has the sbm image.

Mount it and copy sbm.bin to your working directory ($HOME, Desktop, whatever).

format the floppy

# fdformat /dev/fd0u1440

then copy img to floppy with dd command above

# dd if=sbm.bin of=/dev/fd0

done

If you ever get it to boot the ubuntu live cd, just accept guided install option--'entire hard disk' and it will wipe win2000, replacing it with ubuntu.  Simple as that.  Just verify that it chooses the right disk (it may pick the ide drive).  You could also choose to install on the IDE, and then manually specify in the subsequent 'Format?' option to erase the scsi by checking the box.  Or use Gparted later to just delete the entire windows partition.  Not much to it

No idea about what's causing bios selection issue...doubt its the OS preventing

---

### Post by dsimpson on 2009-05-08
When I try to format the floppy with fdformat /dev/fd0u1440 I get the message; /dev/fd0u1440: Device or resource busy

I seem to be unable to format the floppy. The disk that I have has msdos on it, do I need to replace the formatting?

I went ahead and did the sudo dd if=sbm.bin of=/dev/fd0
and the output was; 2880+0 records in   2880+0 records out
although nothing showed up in the floppy. 

I then tried to see what would happen if I did; fdformat /dev/fd0 w/o the identifier and got; Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... 

Need more clarification, somewhere along the way a step was missed or I couldn't get the desired result. Thank you for your patient assistance, I really do appreciate it.

---

### Post by logos34 on 2009-05-08
Here's the way I just did it:

format with mke2fs or mkfs.msdos

> user@ubuntu:~$ mkfs.msdos /dev/fd0
mkfs.msdos 2.11 (12 Mar 2005)

copy
> 
user@ubuntu:~$ sudo dd if=sbm.bin of=/dev/fd0
2880+0 records in
2880+0 records out
1474560 bytes [COLOR="Red"](1.5 MB) copied[/COLOR], 99.2988 s, 14.8 kB/s
user@ubuntu:~$ cmp sbm.bin /dev/fd0
user@ubuntu:~$

compare didn;t find a difference, so no output.  OK.

done.


here's what fdformat should have output when you ran it:

> user@ubuntu:~$ fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... done
user@ubuntu:~$ 

---

### Post by dsimpson on 2009-05-08
Sorry to always come up with bad news, but here is what I got when trying to do the fdformat; 

 sudo fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... 
ioctl(FDFMTTRK): Device or resource busy

msdos is already on the floppy, so I tried to do; 

 sudo dd if=sbm.bin of=/dev/fd0, and I got this

2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.0301896 s, 48.8 MB/s

The floppy drive made some noise, like it was working but when I checked the properties on the disk, it showed nothing with a clean disk. Any other ideas? 

the floppy was formatted when I got it, I will find another and try that and wait for your reply.

---

### Post by dsimpson on 2009-05-08
DUH!!! finally figured it out, all my lack of knowledge, I had the disk mounted when I tried to install the files and it wouldn't write to a mounted disk. Thank you again for your patience, I think it may work now, on to step 2, which is trying it out on the other system, wish me luck, I could use it judging from the past trials. lol!

---

### Post by logos34 on 2009-05-08
ok, was wondering...yeah having it mounted doesn't help...Iwas wracking my brains trying to figure out where you went wrong...even booted my sbm floppy to double check...works fine.

Btw-after you write the img to the floppy, no contents will show up if you mount it, but the vol name appears (does on mine in the file browser side pane--'SMART BTMGR')

---

### Post by dsimpson on 2009-05-08
logos34

Had a problem trying to load the live CD so used the safemode and got the live CD up and running and now Ubuntu is about 90% installed as I write this. Thanks so very much, I can now mark this as solved. If I find a place to post a thank you, you can be sure I will. Duane:)

---

### Post by logos34 on 2009-05-08
my pleasure.  glad it finally booted. good luck with install

---

