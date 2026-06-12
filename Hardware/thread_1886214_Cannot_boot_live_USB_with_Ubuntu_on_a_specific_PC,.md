---
title: "Cannot boot live USB with Ubuntu on a specific PC, on others the USB works fine?"
date: 2011-11-24
forum: Hardware
---

### Post by deckoff on 2011-11-24
**What I do:**
I prepare Ubuntu live USB and boot with it. I select the USB pen drive. The PC tries to boot from it.
**What happens**
**I receive an error message: **
[I]Verifying DMI Pool Data ....... Update Success
Boot Error[/I]
(THAT IS ALL, REALLY, NOTHING MORE) 
**What is expected:**
A normal boot procedure.
**Some other information:** 
1) No matter how I prepare the USB, I get the same result. The USB works just fine on some other PC.
2) The PC will boot from USB made to boot MS-DOS.
3) The PC is dual-boot, Win7 and Ubuntu(installed from CD)
4) The BIOS is Phoenix-Award(version of bios dated 2008), the motherboard is comparatively new.
5) i failed to boot via plop linux boot manager.

---

### Post by deckoff on 2011-11-27
**Bup plus some info:**
I tried bypassing BIOS  (I suspect) limitations with plop LiveCD, but still boot fails...

---

### Post by docbop on 2011-11-27
Sounds like there is system drivers the USB doesn't have for your specific hardware.

---

### Post by deckoff on 2011-11-27
> **docbop said:**
> Sounds like there is system drivers the USB doesn't have for your specific hardware.

The usb will not boot, but CD with the same OS will. So, i think, the problem is that the BIOS does not boot correctly the USB. I found the info that some Award-Phoenix BIOS(mine is too Award Phoenix) are buggy and the USB has to be in USB zip mode. Unfortunately, formatting the drive that way, the PC will still not boot. THE PC  will still boot if the USB is created with hp bootable flash utility. So, I am either doing something wrong, or just have not found the correct tutorial. 
Probably, someone ho is willing to help, to guide me through the process.

---

### Post by sudodus on 2011-11-27
> **deckoff said:**
> The usb will not boot, but CD with the same OS will ...
Unfortunately USB booting is not yet fully standardized or debugged. But why do you want to boot from USB when it works from CD on this one? Maybe we can find some work-around ;-)

---

### Post by deckoff on 2011-11-27
> **sudodus said:**
> Unfortunately USB booting is not yet fully standardized or debugged. But why do you want to boot from USB when it works from CD on this one? Maybe we can find some work-around ;-)

Just because I want to try out new distro releases on this PC, and it is much easier to prepare USB than CD ( not to mention, I run out of empty CDs lately).
I tried this link [here]("http://www.rigadicomando.org/node/58"), but this method does not work with 11.10.

---

### Post by sudodus on 2011-11-27
> **deckoff said:**
> Just because I want to try out new distro releases on this PC, and it is much easier to prepare USB than CD ( not to mention, I run out of empty CDs lately).
I tried this link [here]("http://www.rigadicomando.org/node/58"), but this method does not work with 11.10.
Try this method to boot directly from iso images on your hard drive
[http://ubuntuforums.org/showpost.php?p=11227153&postcount=349](http://ubuntuforums.org/showpost.php?p=11227153&postcount=349)
It works for me (to run live sessions of Ubuntu 10.04 LTS and newer versions of Ubuntu and LinuxMint)

---

### Post by deckoff on 2011-11-28
I am not quite sure if I get this 100% quite right - 
On PC with Linux( or better, newer Ubuntu release installed) and GRUB installed, the GRUB menu entry is added, so the USB is seen as ISO ad run.
```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /media/multimed-2/CD/candidate.iso" {
set isofile="/CD/candidate.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
 Is that right, or I am missing something?
This will solve the problem for me with that particular PC. I hope I will not run into situation where I have to boot with USB and grub is not installed.
The particular version of my BIOS is Phoenix-Award 6.00 PG

---

### Post by sudodus on 2011-11-28
> **deckoff said:**
> I am not quite sure if I get this 100% quite right - 
On PC with Linux( or better, newer Ubuntu release installed) and GRUB installed, the GRUB menu entry is added, so the USB is seen as ISO ad run.
```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /media/multimed-2/CD/candidate.iso" {
set isofile="/CD/candidate.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
``` Is that right, or I am missing something?
This will solve the problem for me with that particular PC. I hope I will not run into situation where I have to boot with USB and grub is not installed.
The particular version of my BIOS is Phoenix-Award 6.00 PG
An iso file on the HDD is used, so you need no USB drive at all. The iso file is (hardlinked to) ***/CD/candidate.iso*** (on the partition **/dev/sda2** mounted on **/media/multimed-2** in my case). You must edit the[COLOR=Red] red[/COLOR] text in order to make it fit where your iso file is located.

Decide where you want to have your iso-files and post the output of the terminal command
```
df
``` That would make it possible for me to help with details.

---

### Post by BC59 on 2011-11-28
Well booting from a USB is not always that easy:

> **Known Issues**

Natty Narwhal 11.04 is having issues with USB flash drives from SanDisk that have U3 Launchpad. You can either use another brand or use either u3-tool from Ubuntu Repositories or SanDisk's U3 Launchpad Removal Tool to remove U3.

10.04.3 is having issues. You might get a segmentation fault if used from command line. There are many launchpad bugs regarding segmentation fault (eg: 572611).

The 9.10 CDs and DVDs are missing the usb-creator.exe program used by the Windows installation processes discussed below. To install the i386 desktop version to a USB flash drive from a disk image on Windows, use the incredibly easy process described at [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) . When you boot the resulting live persistent USB, you can install to your hard disk if you wish at any time, or not.

If you get "Incorrect CD-ROM detected" error on detection stage, reboot, press F6 and then ESC to go to manual boot line editing, and add the option 'cdrom-detect/try-usb=true'.

If the above doesn't solve your CD-ROM detection problem and you used the "Universal USB Installer" to prepare your USB flash drive, another solution might be trying UNetbootin. If you are encountering this problem with UNetbootin, press tab at the splash screen to access the boot line editor.

Some BIOS's (eg., the Eee PC netbook') have trouble recognizing that the USB is bootable. You may have to trick it into booting using the following method: At boot, enter the BIOS by pressing F2. Then, right as you exit the BIOS, hit the Esc key. For some systems, this will bring up the boot menu.

The error "Can not mount /dev/loop1 on /cow" is because usb-creator.exe is not creating a valid casper-rw file holding ext2/ext3 filesystem. Fix: 1) Use Unetbootin or 2) After running usb-creator.exe, recreate casper-rw using cygwin tools or [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/). (As of April 2010)

---

### Post by deckoff on 2011-11-28
This is the output of df:

```
/dev/sda5              6889984   5747288    792696  88% /
udev                    498240        12    498228   1% /dev
tmpfs                   203356       948    202408   1% /run
none                      5120         0      5120   0% /run/lock
none                    508388       600    507788   1% /run/shm
/dev/sda6             19685656  14246088   4439584  77% /home
```

Assuming, I want to run an ISO file , which is in 
```
/home/CD/candidate.iso
```

I should create hardlink to the ISO I want to boot, and place it in ```
/home/CD/,
``` name it ```
candidate.iso
```.

The entry should look like this
```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from [COLOR="red"]/dev/sda6[/COLOR]/CD/candidate.iso" {
set isofile="/CD/candidate.iso"
loopback loop ([COLOR="Blue"]hd0,2[/COLOR])$isofile
}
```

I am not quite sure what should I in the blue part of the entry.
Did I get the other parts right?

---

### Post by sudodus on 2011-11-28
> **deckoff said:**
> This is the output of df:

```
/dev/sda5              6889984   5747288    792696  88% /
udev                    498240        12    498228   1% /dev
tmpfs                   203356       948    202408   1% /run
none                      5120         0      5120   0% /run/lock
none                    508388       600    507788   1% /run/shm
/dev/sda6             19685656  14246088   4439584  77% /home
```Assuming, I want to run an ISO file , which is in 
```
/home/CD/candidate.iso
```I should create hardlink to the ISO I want to boot, and place it in ```
/home/CD/,
``` name it ```
candidate.iso
```.

The entry should look like this
```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from [COLOR=red]CD@/dev/sda6;[/COLOR]**[COLOR=Red] /home/CD[/COLOR]**/candidate.iso" {
set isofile="/CD/candidate.iso"
loopback loop ([COLOR=Blue]hd0,[COLOR=Red]6[/COLOR][/COLOR])$isofile
}
```I am not quite sure what should I in the blue part of the entry.
Did I get the other parts right?
Important: partition number [COLOR=Red]6
[COLOR=Black]Text "Boot...": only clarifying comment[/COLOR]
[/COLOR]

---

### Post by sudodus on 2011-11-28
Look at the original link; the code in 
/etc/grub.d/40_custom
must contain two more lines afterwards
linux ...
initrd ...
totally 6 lines (and [COLOR=Red]**}**[/COLOR] in the last line)

---

### Post by deckoff on 2011-11-28
OK, so it worked.
This makes me think that an empty CD that boots to grub, with grub entry that specifies USB mount should work more or less the same way. 
BTW, I tried with Mint12, and it is kind of slow using this way, but that might be because of the old hardware.

---

### Post by oldfred on 2011-11-28
Just some more explaination of ways to loopmount boot ISO files directly from hard drives or flash drives. Similar to above:

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

Some have created scripts to automate the process and boot many different ISO from one flash drive. Different boot loaders are used by different scripts:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by sudodus on 2011-11-28
> **deckoff said:**
> OK, so it worked.
This makes me think that an empty CD that boots to grub, with grub entry that specifies USB mount should work more or less the same way. 
BTW, I tried with Mint12, and it is kind of slow using this way, but that might be because of the old hardware.
Yes, there are many ways to do it. Find your own favourite way :-)

One reason why booting is slower than from 'standard install' is that the iso image is compressed and the software must be expanded before being started.

---

### Post by sudodus on 2011-11-28
> **oldfred said:**
> Just some more explaination of ways to loopmount boot ISO files directly from hard drives or flash drives ...
Great list of possible alternatives! I'm sure at least one should work for everybody :-)

---

### Post by deckoff on 2011-11-28
finally, it seems, I got 2 how-tos after asking for just one thing. Definitely, the method proposed by sudodus is the one to choose for system with already installed grub. 
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 is more or less the thing i was originally searching for. I have not looked through it, but this should be it. s, thanx to oldfred, too:)
One last:
Why it is hd0 and not sda in the loop command.
I consider this thread solved :)

---

### Post by oldfred on 2011-11-28
In my boot_info script I find Lucid used this as the default style.

This is on a MBR(msdos drive):
set root='(/dev/sdc,msdos7)'

But the newer versions reverted to (this is my gpt drive):

set root='(hd3,gpt3)'

They must have found some issues with the /dev/sdX style that works better with just the hdX style.

---

### Post by deckoff on 2011-12-08
My issue is definitely BIOS (Award-Phoenix 6.00PG)issue :
finally I managed too boot GRUB-based USB linux Live distros with DOS-formatted and DOS-bootable USB and added grub4DOS. 
Grub4dos is used to chainload(start) the GRUB-based (Unetbootin, Ubuntu) USB.
Brief description of the method I used is here[http://askubuntu.com/questions/81667/cannot-boot-live-usb-with-ubuntu-on-a-specific-pc-on-others-the-usb-works-fine]("http://askubuntu.com/questions/81667/cannot-boot-live-usb-with-ubuntu-on-a-specific-pc-on-others-the-usb-works-fine")

---

