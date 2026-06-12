---
title: "Can't mount SDHC.  Internal Reader"
date: 2009-11-20
forum: Hardware
---

### Post by mn_voyageur on 2009-11-20
I am unable to mount my SD card.  Have in the past.  My Treo reads from the card without any problems.  Insert the card into the laptop and the card won't mount.

For a while, it would mount, but it was read only.  (Even though I had permission.)

I was able to copy all of the files from my card during the read-only phase.  Now, I would like to grab the big eraser and wipe it clean.  

I do have a Windows machine, but that would not teach me what I have done wrong and how to fix it.

MN

---

### Post by prshah on 2009-11-20
> **mn_voyageur said:**
> that would not teach me what I have done wrong and how to fix it.

To find out what's wrong, you need to study the logs. To do this, open a terminal (Applications-Accessories-Terminal) and give the command```
tail -f /var/log/messages
```

Now, wait a couple of seconds, then plug in your SD(HC) card. Within a few seconds, some messages will flash onto your open terminal. Copy those lines and paste them here, and someone/me will be able to pinpoint the problem, explain it, and give advice on how to fix it.

I (humbly) congratulate you on your attitude. I also envy that you use a treo; my much-loved and much-hacked 650 died a few months back, and I use a crappy Windows Mobile phone now.

---

### Post by mn_voyageur on 2009-11-20
As instructed.  The messages are below.

Nov 20 07:13:17 mark-laptopS kernel: [30744.659835] mmc0: new SDHC card at address 8fe4
Nov 20 07:13:17 mark-laptopS kernel: [30744.663080] mmcblk0: mmc0:8fe4 SD08G 7.40 GiB 
Nov 20 07:13:17 mark-laptopS kernel: [30744.663160]  mmcblk0: p1

The card is an 8GB SDHC SanDisk.

The card is listed under "Computer."  However, when I try to mount, the reply is:
[INDENT]Cannot mount volume.
Invalid mount option when attempting to mount the volume.[/INDENT]

I appreciate the help.

MN

---

### Post by prshah on 2009-11-20
> **mn_voyageur said:**
> 
Nov 20 07:13:17 mark-laptopS kernel: [30744.659835] mmc0: new SDHC card at address 8fe4
Nov 20 07:13:17 mark-laptopS kernel: [30744.663080] mmcblk0: mmc0:8fe4 SD08G 7.40 GiB 
Nov 20 07:13:17 mark-laptopS kernel: [30744.663160]  mmcblk0: p1


Well at least the card is recognized; but I don't see any partition information. Can you please plug in the card, and (after a few seconds) run from the terminal these commands```
sudo fdisk -l
```

This command will give the partition information (You can sanitize it if you like), using which we can attempt a manual mount, which will give us more errors and clues.

Also, if you can post the output of ```
dmesg|tail
``` AFTER attempting a mount, it will be helpful.

---

### Post by mn_voyageur on 2009-11-20
[PHP]
[74225.196472] mmc0: new SDHC card at address 8fe4
[74225.200578] mmcblk0: mmc0:8fe4 SD08G 7.40 GiB 
[74225.200800]  mmcblk0: p1


Disk /dev/mmcblk0: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              11       19166     7757824    b  W95 FAT32[/PHP]

It would appear to me that the card is being seen by the computer, but for some reason, the computer won't mount the "drive."  

I am confused by the fact that my Treo accesses the card without any problems.

MN

---

### Post by prshah on 2009-11-21
> **mn_voyageur said:**
> 
the card is being seen, the computer won't mount the "drive."  

my Treo accesses the card without any problems.

We can try a manual mount to check for problems.

First, open a terminal and give the "tail -f /var/log/messages" command as in the previous post. Drag this terminal to one corner of the screen.

Then plug in the card, open another terminal, and first, check if the card is auto-mounted;```
mount | grep mmc
``` The command should return blank if the card is not mounted. If it is mounted, then the location returned is where it is actually mounted.

If it is not mounted, then study to tail -f output to find the device (in the previous post, it was "/dev/mmcblk0p1"; may be the same this time too.

Now, try a manual mount```
sudo mount -t vfat /dev/mmcblk0p1 /mnt -o defaults,rw
``` This command will return silently if the mount is successful; the contents can then be accessible in "/mnt".

If there is an error, (and I suspect there will be one), please check the tail -f output for more details.

You can also run a check (when the card is unmounted)```
sudo dosfsck -a /dev/mmcblk0p1 
``` Please note that there is a small possibility that you may lose data or files, so you do this at your own risk.

If your card manual-mounts successfully, then please post the tail -f output messages here for clues to see why it does not auto-mount.

---

### Post by mn_voyageur on 2009-11-21
"tail -f /var/log/messages" follows.

[PHP]	mark@mark-laptop:~$ mount | grep mmc
	mark@mark-laptop:~$ sudo mount -t vfat /dev/mmcblk0p1 /mnt -o defaults,rw
	mark@mark-laptop:~$ /mnt
	bash: /mnt: is a directory
	mark@mark-laptop:~$ mount | grep mmc
	/dev/mmcblk0p1 on /mnt type vfat (rw)

sudo dosfsck -a /dev/mmcblk0p1

	mark@mark-laptop:~$ sudo dosfsck -a /dev/mmcblk0p1
	dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
	/.Trash-1000/files/vm_test
	  Contains a free cluster (162105). Assuming EOF.
	Performing changes.
	/dev/mmcblk0p1: 2034 files, 210851/242304 clusters[/PHP]

I then ran it again to see what would happen:
[PHP]	mark@mark-laptop:~$ sudo dosfsck -a /dev/mmcblk1p1
	dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
	/dev/mmcblk1p1: 2033 files, 210851/242304 clusters
	mark@mark-laptop:~$ [/PHP]

Since nothing else appeared, I though it might work, but it didn't.

When I ran tail -f, this was returned.  Did I type the wrong command?
[PHP]	mark@mark-laptop:~$ tail -f 
	tail: warning: following standard input indefinitely is ineffective[/PHP]

Finally, the messages.  Pretty innocent until...
[PHP]mark@mark-laptop:~$ tail -f /var/log/messages

[117178.595801] mmc0: new SDHC card at address 8fe4
[117178.599039] mmcblk0: mmc0:8fe4 SD08G 7.40 GiB 
[117178.599120]  mmcblk0: p1
[117644.800614] mmc0: card 8fe4 removed
[117649.227758] mmc0: new SDHC card at address 8fe4
[117649.231110] mmcblk1: mmc0:8fe4 SD08G 7.40 GiB 
[117649.231193]  mmcblk1: p1
[117665.692551] ACPI: EC: missing confirmations, switch off interrupt mode.
[117666.197143] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[117666.197160] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff8800b7441f60), AE_TIME
[117666.197246] ACPI Exception (battery-0359): AE_TIME, Evaluating _BST [20080926]
[117693.464583] mmc0: card 8fe4 removed
[117697.179890] mmc0: new SDHC card at address 8fe4
[117697.189558] mmcblk1: mmc0:8fe4 SD08G 7.40 GiB 
[117697.190128]  mmcblk1: p1
[/PHP]

So, the question that jumps out at me is:  What does the "ACPI" logs indicate?

FYI - All of my files were backed up when the card went to "Read-Only." 

I appreciate the help.

MN

---

### Post by prshah on 2009-11-21
> **prshah said:**
> This command will return silently if the mount is successful; the contents can then be accessible in "/mnt".

You can also run a check (when the card is unmounted)

> **mn_voyageur said:**
> 
```
	mark@mark-laptop:~$ mount | grep mmc
	mark@mark-laptop:~$ sudo mount -t vfat /dev/mmcblk0p1 /mnt -o defaults,rw
	mark@mark-laptop:~$ /mnt
	bash: /mnt: is a directory
	mark@mark-laptop:~$ mount | grep mmc
	/dev/mmcblk0p1 on /mnt type vfat (rw)

	mark@mark-laptop:~$ sudo dosfsck -a /dev/mmcblk0p1
	dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
	/.Trash-1000/files/vm_test
	  Contains a free cluster (162105). Assuming EOF.
	Performing changes.
	/dev/mmcblk0p1: 2034 files, 210851/242304 clusters
```

```
	mark@mark-laptop:~$ tail -f 
	tail: warning: following standard input indefinitely is ineffective
```

```
mark@mark-laptop:~$ tail -f /var/log/messages
[117665.692551] ACPI: EC: missing confirmations, switch off interrupt mode.

```


Ouch. Please check if your card is accessible in the Treo.

I specifically said that the card **has to be unmounted** before running the dosfsck. From what you have posted, it seems you have run the fsck even though the card was mounted (in /mnt). You should have received a warning, I don't know why you didn't.

The card manual-mounted successfully. You could have checked your files in /mnt with the command```
ls /mnt
```

Now, if your card is still working, we have to check why automounting is not working. The ACPI errors are not relevant to this problem, I believe.

"tail -f" is a wrong command. The second time (with /var/log/messages) is correct.

Can you please check and confirm if the card is working and the files are accessible?

---

### Post by mn_voyageur on 2009-11-22
Yup, my Treo still likes the card.  I can even move files on and off the card when it is installed in my 700P.  I just can't get it to work when it is in the laptop.  (It worked in the laptop, but now it doesn't.)

The card does not mount.  It does see the card.  The card is listed under "Computer." However, I right click to mount the drive and it says:  
"Cannot mount volume.  Invalid mount option when attempting to mount the volume."

I appreciate the help.

MN

---

### Post by mn_voyageur on 2009-12-02
Bump.

---

### Post by mn_voyageur on 2009-12-16
Okay, I have now found my card reader listed:
[INDENT]./media/sdhc[/INDENT]

However, I still cannot mount the card.

The card shows up when I open "Computer."  It knows that I have inserted an 8 GB SDHC.  So where do I go from here?

Am I posting in the wrong place?

MN

---

### Post by mn_voyageur on 2009-12-18
Well, I still don't know how to automatically mount a memory card.

I do know that upgrading to Karmic solved the problem.

MN

---

### Post by kuckunniwi on 2011-01-17
I'm having the same problem with an 8Gb SDHC card on a brand new HP mini 110 3050ss running Kubuntu Lucid 64-bit. The same card works (and always has) fine on a 2 year-old Clevo laptop (running Kubuntu 10.10 64-bit). 

My lspci output is:

```



00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe


```

I tried opening *tail -f /var/log/messages*, and when I inserted the card, nothing showed up on the log.

```
 mount | grep mmc 
```  showed up blank.

Could this be a driver issue?

---

### Post by kuckunniwi on 2011-01-29
I solved the problem by downloading the drivers (PCIE card reader driver for Linux v.1.1 from Realtek > [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false")

If your card reader happens to be a Realtek, installation is easy:

1) Download package
2) extract (to home folder, p.e.)
3) Navigate to folder in konsole, or in dolphin, press F4.
4) sudo make
5) sudo make install
6) sudo depmod
7) reboot !

If you look around, I'm sure there's a fix for it somewhere! ;)

---

