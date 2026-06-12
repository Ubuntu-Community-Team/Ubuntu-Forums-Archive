---
title: "Windows XP wont boot"
date: 2008-07-21
forum: General Help
---

### Post by NozirohLacitrev on 2008-07-21
Dunno if it's a problem with XP or Ubuntu, but I restarted XP one time and it wouldn't reboot, now whenever I try to boot it it comes up with some "UNMOUNTABLE" something error, I can't read the rest because it goes by too fast.
It will load normally up until it's time for it to go "Welcome" then it goes blue screen and restarts.

I tried looking at my partitions in a manager and it says /dev/sda1 is unmounted and I can't mount it, does this have anything to do with it?

Please help I'm in sort of an emergency and I **need** XP.

---

### Post by justleen on 2008-07-21
that sound like a "normal" windows problem..

Can you get into safe mode at all? 
or last know good config?

---

### Post by WRDN on 2008-07-21
I had that problem in the past, and I solved it by reinstalling XP.

---

### Post by drs305 on 2008-07-21
I'd go to SuperGrub Disk. It can solve all manner of linux and windows boot problems. The link is to the Windows boot problems wiki. You can get links to the download page from there.

[Howto Boot Windows without problems]("http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems")

---

### Post by NozirohLacitrev on 2008-07-21
> **justleen said:**
> that sound like a "normal" windows problem..

Can you get into safe mode at all? 
or last know good config?

Safe mode wont work, not really sure what you mean by last known good configuration.

And drs305, I have it downloaded but K3B wont burn it onto a CD, it just says unknown error,

---

### Post by drs305 on 2008-07-21
> **NozirohLacitrev said:**
> And drs305, I have it downloaded but K3B wont burn it onto a CD, it just says unknown error,

I just downloaded it to see if it worked. From the wiki page, I went to the Super Grub Disk Main Web Page link near the top of the screen. Next I clicked on the right pane link to "Download CDROM" and then "Download CDROM Mirror #0". I downloaded 0.9730 iso and it burned fine by right clicking in nautilus and selecting "Write to Disk".

If the iso is burned correctly, you will see 2 directories (rr_moved, boot) and one file (boot.catalog).

---

### Post by justleen on 2008-07-21
Super grub wont help.. windows is booting, but then crashing... so its just plain ol' windows troubles.

I did encouter this a few times.. sometimes a fixboot (from rescue mode) fixed it, some times a reinstall.. probaly some files needed to boot are corrupt, most likely due to inproper shutdown (this is guessing ofcourse). reinstall might seem a hefty solution, but then again, its a common windows solution...

---

### Post by Vishal Agarwal on 2008-07-21
You need to boot the computer with windows cd. Then go to recovery mode. there select the 1 or 2 option according your windows partition. then run the command fdisk /mbr.
This will re write your master boot record. then you will be able to boot with windows.

[COLOR="Red"]CAUTION : Be careful that using this fdisk/mbr command will overwrite your grub boot loader, and you will not be able to boot your computer in UBUNTU. you will need to reinstall the grub boot loader.[/COLOR]

[COLOR="Red"]CAUTION: Use this command only if you are sure, to afford loss of your data. Because this all process needs some expertise, and with windows I am not very sure that it is only a booting problem or something else.[/COLOR]

---

### Post by justleen on 2008-07-21
> **Vishal Agarwal said:**
> You need to boot the computer with windows cd. Then go to recovery mode. there select the 1 or 2 option according your windows partition. then run the command fdisk /mbr.
This will re write your master boot record. then you will be able to boot with windows.

[COLOR="Red"]CAUTION : Be careful that using this fdisk/mbr command will overwrite your grub boot loader, and you will not be able to boot your computer in UBUNTU. you will need to reinstall the grub boot loader.[/COLOR]

[COLOR="Red"]CAUTION: Use this command only if you are sure, to afford loss of your data. Because this all process needs some expertise, and with windows I am not very sure that it is only a booting problem or something else.[/COLOR]

1. XP doenst have fdisk command anymore.. thats win95/98. win xp uses fixboot and fixmbr
2. dont overwrite your MBR, its working fine as is.. windows just wont boot! (yes, a new mbr will be installed upon reinstalling windows.. but if you can fix it with recovery mode, you might not need a new mbr just yet)

---

### Post by NozirohLacitrev on 2008-07-21
1. He's right it's not a boot error: it's a drive error to the best of my knowledge.

2. I don't have a Windows disc. XD

---

### Post by WRDN on 2008-07-21
As justleen has said, its not an issue with the bootloader. I believe this happens if system files are corrupted, and XP will restart just before the login screen.

Boot from the XP disk and press R to enter the recovery console.
Then, type "chkdsk /f" which will try and find bad sectors/ corrupted files and fix it. You could also try the command "chkdsk /p" to perform an extensive check of the disk.

EDIT: I've just seen the above post mentioning he does not have the XP disk. In that case, in Ubuntu access the XP partition, and copy the file called "chkdsk.exe" from /WINDOWS/system32. Put this on a floppy/ other medium and boot from it then run the commands mentioned.

---

### Post by NozirohLacitrev on 2008-07-26
I was told by a good friend of mine that he had this exact problem twice before, and both times he fixed it by unplugging and plugging in the jumper in the back of the inside of the tower, before I try this I would like to know everyone's input on this.

Thanks.

---

### Post by NozirohLacitrev on 2008-07-26
Sorry about double post, but I managed to snap a pic of the error before it vanished, I copied the text into the text editor:

> A problem has been detected and Windows has been shut down to prevent damage
to your computer.

UNMOUNTABLE_BOOT_VOLUME

If this is the first time you've seen this stop error screen,
restart your computer. If this screen appears again, follow
these steps:

Check to make sure any new hardware or software is properly installed.
If this is a new installation, ask your hardware or software manufacturer
for any Windows updates you might need.

If problems continue, disable or remove any newly installed hardware
or software. Disable BIOS memory options such as caching or shadowing.
If you need to use safe mod to remove or disable components, restart
your computer, press F8 to select Advanced Startup options, and then
select safe mode.

Technical Information:

*** STOP: 0x000000ED (0x86CEE900, 0xc0000006, 0x00000000, 0x00000000)

---

### Post by Vishal Agarwal on 2008-07-27
Did u installed any new Hardware ?

Otherwise boot in safe mode and remove any hardware without drivers appearing in "Other" in windows hardware panel.

---

