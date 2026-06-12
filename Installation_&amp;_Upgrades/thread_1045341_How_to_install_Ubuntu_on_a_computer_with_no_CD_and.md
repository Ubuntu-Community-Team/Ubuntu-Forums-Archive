---
title: "How to install Ubuntu on a computer with no CD and no Floppy?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by gnugu on 2009-01-20
Hello,
I have an Xploretech iX104RD tablet ([http://www.xploretech.com/index.pl?id=2931&isa=Category&op=show](http://www.xploretech.com/index.pl?id=2931&isa=Category&op=show)) that doesn't have a CD and doesn't have a floppy.

BIOS only supports boot from HDD, LAN, USB Floppy and USB CD - not USB Flash. There is no newer version of BIOS available.

I have bootable USB Flash with Ubuntu 8.10 on it.

Tablet has XP tablet edition on it.

What I want to do is boot to Ubuntu to make sure that everything works fine before I install it.

I tried installing into windows from my USB Flash but it failed shortly after it complained about there being only 248MB of memory.

So the question is - how can I boot to Ubuntu?

If I could get GRUB installed in front of Windows I would be able to set it to boot from USB Flash. But how do I get GRUB installed when I can't boot to Linux?

Is there a way to fool BIOS into thinking that USB Flash is USB CD?

Any other suggestions?

Thanks.

---

### Post by druellan on 2009-01-20
As far as I know this should work, I mean, you should be capable to boot into the Live distro using the USB stick. Take a look at the Bios, sometimes the USB must be the primeray boot device to work.

---

### Post by gnugu on 2009-01-20
I'll give it another look, but from what I have seen I can only move the device priority up and down and there is only USB Floppy and USB CD.
I tried both, the USB stick lit up for a while and then it booted to XP anyway.

Also the manufacturer told me that that particular model doesn't support boot from USB stick.

Thanks.

---

### Post by dabl on 2009-01-20
I think you can fool your tablet into booting from a USB stick, using the "fromiso" method.  Google "usb fromiso" and I'm sure you can find a lot of information. I've only done it for sidux:

[http://manual.sidux.com/en/hd-install-opts-en.htm#fromiso](http://manual.sidux.com/en/hd-install-opts-en.htm#fromiso)

Basically you will prepare your USB stick according to the instructions, copy the ISO file onto it, and it will boot like a CD -- to the computer it looks like a bootable CD. No guarantees for *buntu -- but I think it's doable.  :)

---

### Post by icanfly0307 on 2009-01-20
You have windows xp on your tablet right? And it has an ethernet port? 

1. Download UNetBootin for Windows from here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

2. Run UNetbootin from where ever you downloaded it and select Ubuntu from the Distribution Drop Down Menu.

3. Select the version; I recommend 8.10

4. Press OK

5. A couple of files will be downloaded from the internet and after that's done, click "Reboot Now".

6. When your tablet starts up again, your computer will show two boot options: "Windows XP" and "Unetbootin". Highlight Unetbootin and press enter. Wait for one minute and the installer will start up normally. ***_NOTE:_*** You need to be connected to the internet for this method to work.

Hope this helps. Good Luck!!! :)

---

### Post by gnugu on 2009-01-21
icanfly0307,
I tried unetbootin. I did not select the distro from the drop down but rather offered it an ISO file.
After restart nothing happened. I figure that all it did was to create a bootable USB pen drive.

Then I discovered Grub4DOS ([https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)). Unzipped into my C:\ and modified boot.ini adding Grub.
Now my Windows boot loader shows Grub as an option and I can actually run Grub.

Now I need to learn how to modify Grub menu file to add the option to boot from Live Ubuntu USB Pen Drive.

Can anyone help with that?

Thanks.

---

### Post by gnugu on 2009-01-21
First of all thanks to everyone who responded to my question.

Secondly, the title of this thread should really read "How to BOOT Ubuntu" rather then "How to install..".

I have not tested this solution on a tablet in question, but I have tested it on a desktop in my office and it works, so I'm pretty confident.

Q: How can I boot to live Ubuntu USB when my machine BIOS does not support boot from USB, has no Floppy and no CD but has USB and LAN? Machine has some sort of Windows installed.

A: I expect that you already have a live Ubuntu USB pen drive. If not read this [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent). It's not the goal of this exercise.

Once you have a live USB pen drive do:
   1. Get [Grub4DOS]("https://gna.org/projects/grub4dos/").
   2. Unzip to C:\ or somewhere else and read this [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager") for what needs to be in C:\.
   3. For XP modify boot.ini file (is hidden and read-only). Add [FONT="Courier New"]C:\grldr="Start GRUB4DOS"[/FONT] at the end of the file. See [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager") for more info or how to do it for VISTA.
   4. Edit menu.lst file make it look like this:

[FONT="Courier New"]# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.


color black/cyan yellow/cyan
timeout 30
default /default

title Windows XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

title Ubuntu 8.10 from USB
fallback 1
root (hd2,0)
kernel /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /casper/initrd.gz

title Reboot
savedefault --wait=2
reboot

title Halt
savedefault --wait=2
halt[/FONT]


The line [FONT="Courier New"]root (hd2,0)[/FONT] will have to change to whatever hd is your USB.

When you reboot you will see Windows boot loader offering you to boot to Windows XP or Grub4DOS. When you select Grub4DOS then GRUB will come up with its own screen where you can select to boot Ubuntu.

I hope this will help somebody.

*** For the tablet I had to install PLoP [http://www.plop.at/en/bootmanager.htm](http://www.plop.at/en/bootmanager.htm). Used the "Run from GRUB" method.

Copy [FONT="Courier New"]plpbt.bin[/FONT] to C:\.
Copy [FONT="Courier New"]plpcfgbt.exe[/FONT] to C:\. This is a configuration tool that you will be able to download from the site mentioned above.
Run [FONT="Courier New"]plpcfgbt stm=hidden cnt=on cntval=1 dbt=usb plpbt.bin[/FONT]

After restart select GRUB from Windows boot manager and then PLoP from GRUB.

---

### Post by icanfly0307 on 2009-01-21
So you got it to work? :)

---

### Post by gnugu on 2009-01-21
Yes! The combination of yours and dabl's posts pointed me to Grub4DOS and from there it was just putting the pieces together.

Can't wait to get home to try it on the tablet and get rid of last XP standing in my household ;).

---

### Post by Mig Daddy on 2009-01-21
I created a live usb for Intrepid on my WinXP system at work.  When I try to boot it on my Dell Mini, I get the following message: "invalid or damaged bootable partition"

any idea why this is happening and how to fix it?  i already tried doing this with 3 different copies of the iso.

---

### Post by gnugu on 2009-01-21
Your USB comes out of the box formated as FAT16. You **must** format it to FAT32 and then create a live image again.

---

### Post by Mig Daddy on 2009-01-22
> **gnugu said:**
> Your USB comes out of the box formated as FAT16. You **must** format it to FAT32 and then create a live image again.

figured it out.  flash drive was fat32 to begin with.  4gb kingston.  i used gparted to make a 1gb partition and it worked fine.  adding a lba flag to the original 4gb partition did not help.  the flag is not necessary for the 1gb partition.

ubuntu will recognize multiple partitions on a single flash drive.  winxp does not, at least the way my computer is set up.  it only recognizes the 1gb boot partition.

now running intrepid just fine.

---

