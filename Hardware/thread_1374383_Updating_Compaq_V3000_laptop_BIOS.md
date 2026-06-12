---
title: "Updating Compaq V3000 laptop BIOS"
date: 2010-01-06
forum: Hardware
---

### Post by kimw08 on 2010-01-06
Hi everyone,

I'd like to update my (way out of date) bios on my Compaq V3000 notebook - however on the Compaq website there is only a WinFlash exe available for updating bios!! GRRR!! I decided to live dangerously and tried to run the exe through Wine (possibly very stupid, I know!), but it just finished with "this BIOS is not for your notebook/PC" (which can't be right, because it is the one for my specific model number).

Anyone have any ideas on how to update BIOS where only a WinFlash exe is available? Any help/suggestions much appreciated... I don't have access to a copy of Windows, both my computers are single-boot Karmic. :)

Thanks!

---

### Post by Ibidem on 2010-01-06
In general, standard advice is:
DON'T update the BIOS just because it's old; only do it when there is a known fix for a known issue.
Flashing the BIOS is inherently risky (especially when not using the official tool), as a partial flash may render the computer unbootable and there are (a few) bugs introduced now and then.
In other words, it may get worse.
The BIOS appears to be Phoenix (a DOS flash tool exists).  So the short version is:
1.  Obtain the update as a .bin file
2.  Obtain the correct utility (PHLASH16 or perhaps PH1614) from [http://www.biosman.com/bios-flash.html](http://www.biosman.com/bios-flash.html)
3.  Prepare a DOS boot flash drive (easier than making CD), if your bios is new enough to boot from usb.
4.  Add both PH*.EXE and *.bin to the boot (flash or floppy) drive.
5. Reboot from the DOS drive.
6. Run ph* *.bin (use the real name)
I assume you can use a command line and know wild cards.
The fuller version is here:[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

You might look here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us)
That sounds like it might be relevant to you, if you are having problems now.

I have a floppy image with just boot files and the update utility, if you want.
Hope this helps,
Ibidem

---

### Post by kimw08 on 2010-01-06
Thanks Ibidem

Reason I want to update my BIOS is because I've got a serious overheating problem running Ubuntu (laptop crashes using Skype or playing video for more than 10 minutes). From what I've read in threads relating to the overheating problem (seems to be common from 9.04 onwards), updating BIOS is a good fix, and the Compaq website says that the bios update is to fix some bugs (including a fan bug). 

To clarify - when you say "get update as a bin file" do you mean convert the exe to bin? Because the update is ONLY available as a WinFlash exe on Compaq (no other formats available)?

---

### Post by Ibidem on 2010-01-07
I'm sorry I didn't respond sooner.  That went a little past what I know, so I had to look around.
Apparently the Winflash exe includes your bios update, which it extracts before proceeding.  Look for a *.ROM or perhaps .bin file in the directory where you ran winflash; if it isn't there, then repeat the process, but kill winflash before it checks your model.
 This should get you the rom image, which is what you need.
Then proceed with the standard directions.
[Here]("http://www.mydellmini.com/forum/ubuntu-netbook-remix/246-bios-a01.html#post4674") are the directions I am going from for this post.
And if you want to create a DOS flash drive (the easiest way I know),
1.  Install NASM, the Netwide Assembler (the script below uses it)
2.  Download and extract this archive: [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/sys-freedos-linux/sys-freedos-linux.zip](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/dos/sys/sys-freedos-linux/sys-freedos-linux.zip)
And make the perl script executable (you can use Properties).
3.  Determine the device which corresponds to your flash drive (PROBABLY /dev/sdb1, but check):
Figure out the location where your flash drive gets mounted (open in the file manager, and note this)
Open a terminal
Run the command "mount", with no arguments.
There should be a line like this:
/dev/sdb1 on /media/FEDORA type vfat (various nonsense)
If the type is vfat, and  the second location (eg, /media/FEDORA in my case) is right, the device (/dev/sdb1 in my example) corresponds to the flash drive.
4.  Unmount the flash drive.
5.  Now run the perl script as root, identifying the target device:
sudo sys-freedos.pl  --disk=/dev/sdb1
IF the flash drive is /dev/sdb1 (substitute the appropriate device)
(The script compiles a FreeDOS bootsector and writes it directly to the start of the disk; the latter means that you must unmount the disk and run as root)
6.  Download the FreeDOS kernel & command.com, then extract.
Remount the flash drive and copy the needed files over (including "kernel.sys", "command.com", your update tool PH*.EXE, and the bios image)
Boot from the flash drive, and it should work.
Hope this helps,
Ibidem

---

