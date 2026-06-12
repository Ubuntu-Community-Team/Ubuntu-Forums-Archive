---
title: "GRUB problems on dual boot"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by usafwings on 2009-11-07
I have a problem that I don't exactly know how to diagnose, as I'm a new user to Ubuntu and Linux.

I was trying to set up my GRUB menu in terminal because I just installed Windows XP SP3. I've got a 500 G HDD and Each OS is set-up on their own partition.

          fdisk -1 does not work:




ubuntu@ubuntu:~$ fdisk -1
  fdisk: invalid option -- '1'
 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
         fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
         fdisk -s PARTITION           Give partition size(s) in blocks
         fdisk -v                     Give fdisk version
  Here DISK is something like /dev/hdb or /dev/sda
  and PARTITION is something like /dev/hda7
  -u: give Start and End in sector (instead of cylinder) units
  -b 2048: (for certain MO disks) use 2048-byte sectors
 

 Apparently terminal from a LiveCD-boot can't even find my partitions. GParted can, though. My Ubuntu install is perfectly in tact as well as the XP installation. XP flag is boot. I tried the reverse, and that was a no-go.

I also get this list of nonsense when I enter grub on terminal - which I couldn't until I reinstalled it.

Finally I typed grub in terminal and:

          grub> root (hd0,0)
  Error 21: Selected disk does not exist
  grub> find /boot/grub/stage1
  Error 15: File not found
  grub> find /boot/grub/stage2
  Error 15: File not found
 
Oh, sudo gedit grub/boot/menu.lst (or the like - still can't remember it off the top of my head) renders a big zip. Nothing displays in the menu list. What gives??

Thanks for any input. I know both installations are correct, if I can only get the GRUB working and get the system to find my partitions. Thanks again! ):P

wings

---

### Post by registerkar on 2009-11-07
Hi...I to am a linux newbie

If u r using Ubuntu 9.10 then this version uses Grub 2 & not Grub 1 as in 9.04
So boot in Ubuntu & type 'sudo update-grub' in terminal
Grub will detect all your installed OS & u should boot in both OS.

Can u just let us know about which version u r using?...

---

### Post by jheaton5 on 2009-11-07
You have a typo in your fdisk command it is l not 1

try again: fdisk -l

---

### Post by usafwings on 2009-11-07
Yes it's 9.10.

I thought it was l and not 1 as well at first, but I got an error message doing that. I'll check and see if it wasn't just operator error. Thanks for the help!

):P
wings

---

### Post by jheaton5 on 2009-11-07
> **registerkar said:**
> If u r using Ubuntu 9.10 then this version uses Grub 2 & not Grub 1 as in 9.04
So boot in Ubuntu & type 'sudo update-grub' in terminal
Grub will detect all your installed OS & u should boot in both OS.

That is the right answer if you are using grub2.

---

### Post by usafwings on 2009-11-08
Tried and failed. Any other ideas? :)

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$


):P
wings

---

### Post by usafwings on 2009-11-08
Also:

ubuntu@ubuntu:~$ fdisk -u

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...


ubuntu@ubuntu:~$ fdisk -b SSZ

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst
This renders a blank list.


...just to make sure.

---

### Post by oldfred on 2009-11-08
Grub2 does not have a menu.lst. Trying to edit it will just create a blank file.

to run copy this to your terminal:

```
sudo fdisk -l
```

You can copy with right click copy & right click paste or control-shift c in the terminal at the cursor location.

---

### Post by usafwings on 2009-11-08
Well I'm quite stupid as I consistently omitted the sudo command.

```
 sudo fdisk -l 
```Renders this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99459945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8510    68356543+  83  Linux
/dev/sda2            8511       12157    29294527+   5  Extended
/dev/sda3   *       12158       44028   256003807+   7  HPFS/NTFS
/dev/sda5            8511       12157    29294496   82  Linux swap / Solaris


Edit: I still get this, however:
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.


Thanks! ;)
usafwings

---

### Post by oldfred on 2009-11-08
I do not know if it is related to your problem or not, but you cannot have 2 boot flags on one drive. Use a liveCD and gparted to remove the boot flag from the linux partition. Only windows needs the boot flag.

---

### Post by usafwings on 2009-11-08
> **oldfred said:**
> I do not know if it is related to your problem or not, but you cannot have 2 boot flags on one drive. Use a liveCD and gparted to remove the boot flag from the linux partition. Only windows needs the boot flag.

I thought I had previously removed that flag. It is fixed now. 

What I can't figure out though is managing the boot in GRUB. I have GRUB2 but still even this doesn't work:

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.



When fdisk looks like:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99459945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8510    68356543+  83  Linux
/dev/sda2            8511       12157    29294527+   5  Extended
/dev/sda3   *       12158       44028   256003807+   7  HPFS/NTFS
/dev/sda5            8511       12157    29294496   82  Linux swap / Solaris



How do I reinstate/reinstall the GRUB as to accomplish my dual boot? All the tuts are for 9.04 or earlier.

Thanks! 8-[
usafwings

---

### Post by oldfred on 2009-11-09
Herman has instructions on reinstalling grub2:

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by usafwings on 2009-11-09
> **oldfred said:**
> reinstall grub2

I followed your link and it has a lot of awesome info. I tried reinstalling GRUB2 and this is what I got.

```
ubuntu@ubuntu:~$ ls /media
```renders: disk (I relabeled to make the process easier)

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub /dev/sda
```rendered a response similar to: unable to access device.map 
So, I continued with his guide.

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda
```renders: ubuntu@ubuntu:~

It seems that nothing happened. Is this correct, or will I get feedback saying that it had been installed?

Thanks! :)
wings

---

### Post by usafwings on 2009-11-09
The last command seems to have worked. I rebooted and GRUB has worked, and it booted me into Ubuntu.

Now my problem is this:
It seems I have no option to select the two OS's, it just auto-boots into Ubuntu.
How do I configure this boot menu for GRUB2?

Thanks!8-[
usafwings

Edit: I tried holding down shift during the boot process and the menu displayed. Windows XP was definitely not one of the choices, however, when I got into Ubuntu and rechecked my partitions, it's still on there. Any ideas?

---

### Post by oldfred on 2009-11-09
If the sudo update-grub2 command does not find the XP install it probably means you have a problem with  the XP install. You can add a manual setting  if you want.

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.
ranch hand's custom grub2
[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553)

If you want to know what is booting from where run this script:
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by usafwings on 2009-11-09
> **oldfred said:**
> sudo update-grub2 command...

This did just the trick! Thank you so much for the advice!

Awesome!\\:D/
wings

---

