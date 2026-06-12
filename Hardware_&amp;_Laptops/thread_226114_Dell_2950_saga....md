---
title: "Dell 2950 saga..."
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by Grizzly_Adams on 2006-07-30
Greetings all,

I have some shiny new Dell 2950 machines to install Ubuntu on and I am having difficulty.  I thought I would post the details of what I have had to do so far, in order that others may profit from my experience.

Issue #1:  The installer is unable to detect the network card.  It is possible to continue past this point and install the OS so that is what I have done.
Resolution:  Continue on past this point.

Issue #2: The installer detects the HDD's attached to the internal RAID controller fine, but first boot after installation is unable to detect the HDD's and hence does not load.
Resolution:  As found in this thread [http://kmuto.jp/b.cgi/debian/d-i-2615.htm](http://kmuto.jp/b.cgi/debian/d-i-2615.htm) there is some bug in the Debian installation somewhere in that it does not compile the "megaraid_sas" driver into the initrd.img file.  So once the ubuntu installation is complete but BEFORE you elect to reboot the computer, do the following:

Alt+F2
chroot /target
echo "megaraid_sas" >> /etc/mkinitramfs/modules
mkinitramfs -o /boot/initrd.img-2.6.15-1-486 2.6.15-1-486
exit
Alt+F1

Issue #3:  System hangs during shutdown after install.
Resolution:  Give it sufficient time to ensure it is shutting down as best it can, then use that big button on the front of the 'puter.

Issue #4:  Related to issue #1 - no network when system loads.  Resolution:  None at this stage.  I followed the advice of another person and tried loading the driver manually but to no effect (ie. modprobe bnx2).  The output of a lspci is as follows:

# lspci | grep -i broad
 PCI bridge: Broadcom: Unknown device 0103 (rev c2)
 Ethernet Controller:  Broadcom Corporation:  Unknown device 164c (rev 11).

If anyone can help resolve this (hopefully) final issue it would be much appreciated.

I can download the Redhat drivers for the Broadcom Ethernet card  but they are in RPM format which does not assist me much :-\

---

### Post by Grizzly_Adams on 2006-07-31
Problem with network card solved.

Ubuntu does not detect the network cards during installation, however it is possible to activate them after first boot by adding the necessary entry for the interface in the /etc/network/interfaces file, then ifup'ing the interface.

So I can confirm that it is possible (though a little difficult to setup) to run Ubuntu 6.06 on a Dell 2950.

---

### Post by ScislaC on 2006-08-02
You rock man! Thanks very much!

---

### Post by jbaloul on 2006-08-17
I can confirm that the same issues go for the Ubuntu install on the Dell PowerEdge 1950 ...

The resolution mentioned works with the Ubuntu 6.06 LTS Server Install CD...
which loads kernel 2.6.15-23-server

It does NOT work with the new 6.06.1 Server install CD which loads the new 2.6.15-26-server kernel...
The newer Kernel does not detect the disks properly...I am using the SaS disks in a mirror RAID configuration, and the installer sees 3 disks, the 2 physical ones and the virtual one.

Other than that, after install, network configuration, & dist-upgrade to the 2.6.15-26-server kernel it does work however one more issue is to be noted.

**Additional Issue**
When Setting a static IP to the NIC, the interface does not come up after reboot...it pretends to be up but no communication to and from the interface is possible...

**Resolution**
as root
```

cd /etc/rcS.d/
vim S99restartNetPatch.sh

```
insert these lines...
```

#!/bin/bash
/etc/init.d/networking restart

```
make the patch executable...
```

chmod +x S99restartNetPatch.sh

```
you can now reboot and it should come up fine

Thank You very very much for the initial resolution as it definetly was a life saver.

--
Cheers,
Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by RRico on 2006-08-18
...guess I'm not the only one having problems with the PE-2950.

I'm experiencing a similar problem viewing the disks during the install. I'm using four 146GB disks configured as raid 10 and the installer is listing every disk individually no raid is seen- the server has a perc5 raid card.

Jacob you mention that the 6.06 CD will work but I can't find that version anywhere all links on the web point to 6.06.1- Where did you get your copy from?

You also mentioned that you were able to complete the install even though you experienced the issue viewing the raid config properly- how did you solve it? Did you load the megaraid_sas module before partitioning the disks?

Any advise would be greatly appreciated.

Rico

---

### Post by jbaloul on 2006-08-18
Rico,
The 6.06 = kernel 2.6.15-23-server can be downloaded here:
[http://cdimage.ubuntu.com/releases/6.06/release/](http://cdimage.ubuntu.com/releases/6.06/release/)

Yes the 6.06 sees the raid array as one disk at install time and not as individual disks like the 6.06.1

You have to follow the instructions that Grizzly_Adams gave, but use the 6.06 CD...

Once everything is up, you can dist-upgrade and apply my NIC patch...

Let me know if you need any additional info...


One thing i am a bit worried about is you still see to many letters in /dev/sd* and the disks don't flash together... i wonder if i am just being paranoid or maybe its just pretending to raid...i haven't done the real hardcore test of pulling one disk out yet...

JB

---

### Post by RRico on 2006-08-18
Thanks for the link!!! I just started downloading the ISO. 

I actually prefer Debain but my boss wants me to use a user-friendly distro- hence the reason for Ubuntu. I'm going to follow Grizzly Adam's advise and go a step further and pull out a disk to simulate a failure. I'll post my results when I'm done. 

Cheers,

Rico

---

### Post by RRico on 2006-08-21
Okay, here's the scoop:

I used the 6.06 version and the installer sees all disks individually and a virtual disk (/dev/sdf) as the raid 10 virtual drive. I proceeded with the install and used Grizzly_Admas instructions but was not able to boot the system. The megaraid_sas module loaded fine the problem is that the installer  doesn't recognize the raid-10 config properly or the disk as /dev/sda as it should. 

So, I logged on to distrowatch and discovered Lineox [http://www.lineox.net](http://www.lineox.net). They just released a new version based on RHEL4AS on the 15th of August.

I burned myself a copy and voila! The installer loads the megaraid_sas module, the raid-10 config is recognized as /dev/sda and so are the broadcom GB NICs. Since Dell provides many apps in rpm format I might as well go with something that's based on RH.

I was able to get vmware-server installed with some minor hacking -- used this guide on the vmware forum

[http://www.vmware.com/community/thread.jspa?messageID=455100&#455100](http://www.vmware.com/community/thread.jspa?messageID=455100&#455100)

Now, I'm trying to get OpenManage 5.0 installed but tech support at Dell said that they haven't been able to get it to work either. I can live without being able to view the raid config but my boss might not like it. I guess I'll have to wait until Dell comes up with a 64-bit version of OM that will work on Linux.

I'll post my questions about OM on the Dell Linux forum. 

Thanks for the help Jacob.

Rico

---

### Post by jbaloul on 2006-08-21
Oh man. that stinks...

changing distro to RH based to get that stuff to work is bad...

Ubuntu probably didn't like the RAID 10 cause mine was RAID 1 and it worked...

I hoped for a better outcome...and i hope that my disks are really mirroring and that when / if that day comes i won't find out that they didn't the hardway...

just for the heck of it could you post your:
```

ls -l /dev/sd*
mount
df -ah
fdisk -l /dev/sda

```

thanks,
JB

---

### Post by mpvano on 2006-08-21
I used to have the same problem in breezy with earlier dell servers with my ethernet adapters (which dapper now supports) and was able to solve the problem by adding the name of the driver module to /etc/modules.

Drivers in /etc/modules are loaded very early in the boot process so they will be available for nfs, etc.

Once the I got the driver loading automatically, the configuration information I put into /etc/network/interfaces was also automatically honored.

I don't know the name of the drivers for your card, but it should be asy enough to find out from dmesg.

hope this works for you...

Mario

---

### Post by RRico on 2006-08-21
JB- here is it:

The server has 5 equal disks (146GB 10k rpm- raid-10) one is a hot-spare 

[root@agcvh01 ~]# ls -l /dev/sd*
brw-rw----  1 root disk 8,  0 Aug 19 08:50 /dev/sda
brw-rw----  1 root disk 8,  1 Aug 19 08:50 /dev/sda1
brw-rw----  1 root disk 8,  2 Aug 19 08:50 /dev/sda2
brw-rw----  1 root disk 8,  3 Aug 19 08:50 /dev/sda3
brw-rw----  1 root disk 8,  4 Aug 19 08:50 /dev/sda4
brw-rw----  1 root disk 8,  5 Aug 19 08:50 /dev/sda5
brw-rw----  1 root disk 8,  6 Aug 19 08:50 /dev/sda6
brw-rw----  1 root disk 8,  7 Aug 19 08:50 /dev/sda7
brw-rw----  1 root disk 8,  8 Aug 19 08:50 /dev/sda8
brw-rw----  1 root disk 8,  9 Aug 19 08:50 /dev/sda9
brw-rw----  1 root disk 8, 16 Aug 19 12:50 /dev/sdb


[root@agcvh01 ~]# mount
/dev/sda8 on / type ext3 (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw,gid=5,mode=620)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sda2 on /boot type ext3 (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda9 on /home type ext3 (rw)
/dev/sda6 on /tmp type ext3 (rw)
/dev/sda3 on /usr type ext3 (rw)
/dev/sda5 on /var type ext3 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)


[root@agcvh01 ~]# df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             981M  636M  296M  69% /
none                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /dev/pts
usbfs                    0     0     0   -  /proc/bus/usb
/dev/sda2             251M   18M  221M   8% /boot
none                  3.9G     0  3.9G   0% /dev/shm
/dev/sda9             254G   18G  224G   8% /home
/dev/sda6             2.0G   40M  1.8G   3% /tmp
/dev/sda3             5.8G  1.1G  4.5G  19% /usr
/dev/sda5             3.9G  160M  3.5G   5% /var
none                     0     0     0   -  /proc/sys/fs/binfmt_misc
sunrpc                   0     0     0   -  /var/lib/nfs/rpc_pipefs


[root@agcvh01 ~]#fdisk -l /dev/sda

Disk /dev/sda: 292.3 GB, 292326211584 bytes
255 heads, 63 sectors/track, 35539 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5          37      265072+  83  Linux
/dev/sda3              38         802     6144862+  83  Linux
/dev/sda4             803       35539   279024952+   5  Extended
/dev/sda5             803        1312     4096543+  83  Linux
/dev/sda6            1313        1567     2048256   83  Linux
/dev/sda7            1568        1822     2048256   82  Linux swap
/dev/sda8            1823        1949     1020096   83  Linux
/dev/sda9            1950       35539   269811643+  83  Linux

---

### Post by ondrass on 2006-08-22
> **jbaloul said:**
> It does NOT work with the new 6.06.1 Server install CD which loads the new 2.6.15-26-server kernel...
The newer Kernel does not detect the disks properly...I am using the SaS disks in a mirror RAID configuration, and the installer sees 3 disks, the 2 physical ones and the virtual one.

See [#57265](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/57265) for kernel patch which should fix it.

---

### Post by nobone on 2006-08-22
I am having exactly the same problem.

I tried the solution provided by Grizzly_Adams but it didn't work.
I had to change /boot/grub/menu.lst to use root(0,0) instead of the "root(0,5)" it had on. I also had to run "grub-install /dev/sdf"

I have 5 disks doing raid5. Ubuntu shows me /dev/sda to sde as physical drives, 73GB each and /dev/sdf as the virtual drive with 290GB.


I managed to boot it up and it is working fine, but it just doesn't fell right to have all the /dev/sdX appearing and have to use /dev/sdf.
I am also getting some error messages related to "Read I/O error on /dev/sda4 and /dev/sde4"


I booted it up with the CentOS 4.3 cd and it detects the raid properly, it hides all the /dev/sdX and it only shows /dev/sda as the virtual disk.

Sorry if my post is not very detailed, but I don't have the machine running now to post the exactly error logs and changes I made to menu.lst.

Unfortunatelly, I'll probably have to go for CentOS.

Cheers.

---

### Post by RRico on 2006-08-24
For anyone interested on getting the 2950 to work on Debain Amd64 see this link:

[http://kmuto.jp/b.cgi/debian/d-i-2615.htm](http://kmuto.jp/b.cgi/debian/d-i-2615.htm)

And look for the last post titled: Dell 2950 working!

I had the same issue-- my boot path was set incorrectly by Grub.

Rico

---

### Post by davidw on 2006-09-01
I got everything running by means of the megaraid sas driver.  It was a pain, but manageable.  The problem is the damn network cards, which used to come up, but aren't doing anything at all right now.

I've been modprobe'ing and removing, ifconfig up and downing, and anything else I could think of, but the f&(**&*'s won't work.  I checked the cable, and it works fine when plugged into another system.  I'm pretty much out of ideas.... without a network connection, it's going to be a real pain trying to get another kernel onto the damn thing.

---

### Post by paul.maddox on 2006-09-11
FYI - I found you can monitor and administer the megaraid_sas array using MegaCLI

See this thread:
[http://ubuntuforums.org/showthread.php?t=252689](http://ubuntuforums.org/showthread.php?t=252689)

I'm currently writing a wrapper script for MegaCLI that can be run from CRON to monitor and alert via email on the raid health status.

I'll upload the script here when it's done.

---

### Post by davidw on 2006-09-11
It turns out that the bnx2 cards themselves had a problem: they didn't hold ethernet cables well, so contact was intermittent, causing, obviously, serious problems.  Dell quickly replaced the motherboard.

---

### Post by Contivity on 2006-09-19
I really want to run Ubuntu, but Can't find 6.06, they only have 6.06.1. Seems like there's no workaround to make 6.06.1 to work with Poweredge 2900 with PERC 5i. Anyone that can get it to work, please let me know

---

### Post by Roboto on 2006-09-25
I found the release here:

[http://old-releases.ubuntu.com/6.06.0/](http://old-releases.ubuntu.com/6.06.0/)

---

### Post by Robert Citek on 2006-10-03
Summary: success installing Dapper Drake on a Dell PowerEdge 2950.

Thanks to all for the tips and tricks.  Here are our notes on how we installed Ubuntu 6.06.1 LTS on our Dell PowerEdge 2950.  Our Dell PE had two SAS drives configured as RAID-1 (mirror).

[LIST]
[*] Boot with Ubuntu 6.06.1 LTS AMD64
[*] Install server 
[*] Language: English
[*] Location: United States
[*] Keyboard: American English
[*] Network Firewire: No
[*] No network: Continue
[*] Hostname: Ubuntu
[*] HTTP Proxy: {Enter}
[*] Partition: Erase entire disk : SCSI2 (Dell Perc)
[*] Partition confirm: Yes
[*] Time Zone: Central
[*] System Clock UTC: No
[*] New user: {some username}
[*] Account name: {some account name}
[*] password: {some password}
[*] re-enter password: {some password}
[*] After the CD ejects, fix the initrd, install grub in the right place, fix menu.lst, config networking like so:

Alt+F2

```
chroot /target

# fix initrd
echo megaraid_sas >> /etc/mkinitramfs/modules
cp /boot/initrd.img-2.6.15-26-amd64-server /boot/initrd.img-2.6.15-26-amd64-server.old
mkinitramfs -o /boot/initrd.img-2.6.15-26-amd64-server 2.6.15-26-amd64-server

# install grub
grub-install /dev/sdc

# change (hd2,0) to (hd0,0) in menu.lst
grep hd2 /boot/grub/menu.lst
cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
sed -e 's/hd2/hd0/g' /boot/grub/menu.lst.orig > /boot/grub/menu.lst

# configure networking
echo '
# The Ethernet network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
' >> /etc/network/interfaces

touch /etc/resolv.conf

# exit the chroot
exit

# unmount /target
umount /target

# reboot (optional)
Alt+SysRq+B
```
Alt+F1 

[*] Finished: continue 
[/LIST]

Note: the above notes are for a 2-disk RAID.  If you have more disks, you'll need to adjust /dev/sdc and hd2 accordingly.  For example, if you have a 4-disk RAID, then the logical drive will be /dev/sde and hd4.  I have not tried installing on a system with more than one logical drive.  Please post if you have.

What made this installation challenging were three items:
[LIST=1]
[*]megaraid_sas driver not in the initrd
[*]Ubuntu seeing the logical drive as the next "physical drive"  (/dev/sdc) instead of as a separate logical device (e.g. /dev/md0)
[*]Grub seeing the first drive (hd0) as the first physical drive (/dev/sda) within linux and as the logical drive (/dev/sdc) at boot time.
[/LIST]

Regards,
- Robert

---

### Post by jbaloul on 2006-10-03
Hi Robert,
Very nice...

Did you test the mirror by any chance? Did you pull out a drive?

JB

---

### Post by Robert Citek on 2006-10-05
> **jbaloul said:**
> Did you test the mirror by any chance? Did you pull out a drive?
Not yet.  But will do. - Robert

---

### Post by Robert Citek on 2006-10-05
> **jbaloul said:**
> Did you test the mirror by any chance? Did you pull out a drive?

Yes.  I did the following:
[LIST=1]
[*]Powered off
[*]Pulled the second drive (/dev/sdb)
[*]Powered on -- the PERC complained, but I continued
[*]Let grub start
[/LIST]
Although the kernel started to boot it didn't finish.  I suspected it was because the grub stanza contained "root=/dev/sdc1".  So, I tried again:
[LIST=1]
[*]Powered off
[*]Powered on
[*]After grub started, edited the kernel line and changed /dev/sdc1 to /dev/sdb1
[*]Continued booting
[/LIST]
This time Ubuntu seemed to boot just fine, i.e. I was able to login.  I thought this odd because an "fdisk -l" showed only drives /dev/sda and /dev/sdb, the physical and logical drive respecitively.  I would have thought that without /dev/sdc the entries in /etc/fstab would be invalid.

The third test was to rebuild the array:
[LIST=1]
[*]Powered off
[*]Re-inserted the second drive
[*]Powered on
[*]Entered the PERC configuration
[*]Followed the instructions in the [PERC Users Guide]("http://support.dell.com/support/edocs/storage/RAID/PERC5/en/ug/index.htm") for clearing a Foreign disk and adding a Global Hot Spare.
[*]Rebooted into Ubuntu
[/LIST]
Seemed to work just fine.  I was able to log in and "fdisk -l" showed all three drives: the two physical (/dev/sda and /dev/sdb) and one logical (/dev/sdc).  I happened to reboot the machine a few hours later and checked the rebuild of the array.  It seemed to finish just fine.

I still find it odd that both the physical and the logical drives appear sequentially as SCSI devices.

I would like to try hot-swapping, but don't have a user-space application for this installed, yet.  Anyone have any recommendations (e.g. MegaCLI)?

HTH,
- Robert

---

### Post by Technoviking on 2006-10-06
Hmmm....
After rebooting, my PowerEdge 2950 gets stuck at 
Uncompressing Linux... Ok, booting the kernel

Any ideas?

---

### Post by Robert Citek on 2006-10-06
> **Mike said:**
> Hmmm....
After rebooting, my PowerEdge 2950 gets stuck at 
Uncompressing Linux... Ok, booting the kernel

Any ideas?
The most likely reason is that the kernel option root= points to the wrong location, e.g. "root=/dev/sda1" when it should be /dev/sdc1.

One solution is to remove the boot options "splash" and "quiet" and add the option "1" to the end of the kernel line in grub.  You will then see any error message that happen.

Two questions:
[LIST]
[*]What version of Ubuntu are you installing (e.g. 6.06.1 AMD64, 6.06.0 AMD64, other)?
[*]What RAID level are you using (e.g. 1, 0, 5, other)?
[/LIST]

Regards,
- Robert

P.S.: What happened to Mike's post?

---

### Post by jbaloul on 2006-10-06
Sounds Promising...

Thanks for the details man.

JB

---

### Post by Technoviking on 2006-10-06
> **Robert Citek said:**
> 

P.S.: What happened to Mike's post?

I solved the problem, so I removed the post :). Although I now get errors with my kernel after apt-get dist-upgrade.

---

### Post by Technoviking on 2006-10-06
With linux-image-2.6.15-27-server [2.6.15-27.48] my Ubuntu crashes hard at boot.

I have a PowerEdge 2950 with 4-146 SAS drives using RAID-5.
/ = /dev/sda1
swap = /dev/sda2
/home = /dev/sda3
```

[missed some error messages, scrolled too fast]
[42949376.320000] sde: asking for cache data failed
[42949376.320000] sde: assuming drive cache: write through
[42949376.620000] Buffer I/O error on device sda, logical block 164296704
[42949376.620000] Buffer I/O error on device sda, logical block 164296705
[42949376.620000] Buffer I/O error on device sda, logical block 164296704
[42949376.620000] Buffer I/O error on device sda, logical block 164296705
[42949376.620000] Buffer I/O error on device sda, logical block 164296754
[42949376.620000] Buffer I/O error on device sda, logical block 164296754
[42949376.620000] Buffer I/O error on device sda, logical block 16429675
[42949376.620000] Buffer I/O error on device sda, logical block 164296754
[42949376.620000] Buffer I/O error on device sda, logical block 164296754
[42949376.620000] Buffer I/O error on device sda, logical block 164296754
[42949379.550000] EXT3=fs: journal inode is deleted.

mount: Mounting /dev/sda1 on /root failed: Invalid arguement
mount: Mounting /root/dev on /dev/.static/dev/ failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
```
This server will boot fine to linux-image-2.6.15-23-server
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/64454](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/64454)

Any ideas?
Mike

---

### Post by Robert Citek on 2006-10-08
> **Mike said:**
> With linux-image-2.6.15-27-server [2.6.15-27.48] my Ubuntu crashes hard at boot.
 ...
Any ideas?

Yes.  I suspect you have the same problem as before: the megaraid driver is not distinguishing between physical and logical drives.

With RAID 5, your physical drives are /dev/sd{a,b,c,d} and you logical drive is /dev/sde, as this message implies:
```

[42949376.320000] sde: asking for cache data failed
[42949376.320000] sde: assuming drive cache: write through

```

So, you probably have entries like "root=/dev/sda1" in your /boot/grub/menu.lst, entries like "/dev/sda*" in your /etc/fstab, and grub installed at /dev/sda.

What you need is the following:
[LIST=1]
[*]have grub installed on /dev/sde:
```
grub-install /dev/sde
```
[*]change all the sda entries to sde in /boot/grub/menu.lst
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sed -e 's/sda/sde/g' /boot/grub/menu.lst.bak > /boot/grub/menu.lst
```
[*]change all sda entries to sde in /etc/fstab
```
cp /etc/fstab /etc/fstab.bak
sed -e 's/sda/sde/g' /etc/fstab.bak > /etc/fstab
```
[/LIST]

The way to do that is to boot into recovery mode with the install CD and drop into the shell using Alt-F2.

Let us know if this works for you or if you have any questions.

Regards,
- Robert

---

### Post by mutalisk on 2006-10-09
Robert Citek,

Thanks for your guide, it saved me a lot of headache!

I only saw one thing that it was missing...  I think your missing a "cd /boot" right before "cp initrd.img-2.6.15-26-amd64-server initrd.img-2.6.15-26-amd64-server.old".  And I had to use "grub-install /dev/sde for my system instead of /dev/sdc.  And I had to change hd4 to hd0 in /boot/grub/menu.1st.  And I also had to edit /grub/device.map so it just had (hd0) /dev/sde.

PS, for those who might not know if you do a basic server install, you will need to do the following to get sshd going.

sudo apt-get install ssh
sudo aptitude install openssh-server

---

### Post by Robert Citek on 2006-10-09
> **mutalisk said:**
> Thanks for your guide, it saved me a lot of headache!
You're welcome, although most of the credit goes to those who posted before I did.

> **mutalisk said:**
> I only saw one thing that it was missing...  I think your missing a "cd /boot" right before "cp initrd.img-2.6.15-26-amd64-server initrd.img-2.6.15-26-amd64-server.old".
Indeed, I was.  Went back and corrected that.   Thanks for pointing that out.

> **mutalisk said:**
> And I had to use "grub-install /dev/sde for my system instead of /dev/sdc.  And I had to change hd4 to hd0 in /boot/grub/menu.1st.  And I also had to edit /grub/device.map so it just had (hd0) /dev/sde.
Yes.  I updated my previous post with a note if one has more physical drives.  

As for modifying /boot/grub/device.map, I didn't make a note of that because I didn't change it.  Should I have edited it?  What prompted you to edit it?

FWIW, here's my /boot/grub/device.map file:
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
```

Regards,
- Robert

---

### Post by Speeder on 2006-10-22
FYI the edgy kernel (2.6.17-10-server) fixes the physical drive problem, but

sda: asking for cache data failed 
sda: assuming drive cache: write through 

it should really be write back..

ALSO did anyone find any decent raid managment software for the perc card? something that supports online expansion, hot swaps, etc.

---

### Post by rcgabriel on 2006-10-27
> **Speeder said:**
> FYI the edgy kernel (2.6.17-10-server) fixes the physical drive problem, but

sda: asking for cache data failed 
sda: assuming drive cache: write through 

it should really be write back..

ALSO did anyone find any decent raid managment software for the perc card? something that supports online expansion, hot swaps, etc.

There is the MegaRAID Storage Manager from LSI (downloadable from the LSI site under support for any of their RAID controller cards) that supports the same LSI OEM cards as MegaCLI, and thus might in theory work reasonably well with the Dell PERC hardware (since MegaCLI works with it).  However, it is distributed as an RPM only and I am not enough of a Debian/Ubuntu guru to get Alien to eat the RPM happily and create a .deb from it to see if it really works.

If anybody takes a crack at this and gets it working, I'd love to know.

My two PowerEdge 2950s are working great with Ubuntu 6.06.1 LTS now, thanks to the info in this thread.  It would make me feel a little more happy with my RAID setup if I could get something like MegaRAID storage manager working with Ubuntu too.

---

### Post by paul.maddox on 2006-10-27
I've tried installing the LSI MegaRaid Storage Manager using Alien to convert the RPM to a deb but didn't have much luck.

So... I have started creating some basic monitoring stuff for the mega raid driver.

At the moment I have written a wrapper script for the MegaCLI utility which currently checks for:

 - Degraded Raid Arrays
 - Offline Raid Arrays
 - Critical Disks
 - Failed Disks

It runs overnight using cron.daily and notifies me via email (using sendmail).

At the moment it's still quite basic but feel free to take a look:
```

root@web1:~# echo "deb http://apt.office-shadow.com dapper main" >> /etc/apt/sources.list
root@web1:~# apt-get update
root@web1:~# apt-get install mega-status

```

You'll need to edit the config file (/etc/mega-status.conf) and change the email address otherwise i'll start getting warnings about your failed raids!

Like other people have said, this is nothing in comparison to proper raid monitoring and management software but at the moment at least i'm getting notified of problems so they don't go unnoticed.

Edit: I've only spent a few spare hours working on this and it probably has a few bugs in it still, but I can guarantee it won't compromise any data on your RAID structure. It just uses MegaCLI to query the status of the RAID and parses the output. I'd be interested to hear if this works for people or if anyone finds any big bugs in it!

---

### Post by chewie124 on 2006-11-05
Just a quick question - what's the deal with using the AMD64 server install disk?  The kernel images work for the dual core Xeons?

TIA

---

### Post by rcgabriel on 2006-11-05
chewie - that's correct, the Ubuntu "AMD64" architecture covers both AMD64 and EM64T (the 64 bit Intel platform).  

I'm running the AMD64 install on my Poweredge 2950 with two Xeon 5130 dual core processors, and it works great in general (with the exception of some general x64 platform hiccups, which you can read about in the 64-bit forum here, though they all have pretty easy workarounds).

---

### Post by Robert Citek on 2006-11-05
> **Speeder said:**
> FYI the edgy kernel (2.6.17-10-server) fixes the physical drive problem, but ...
Confirmed.  Reinstalling using edgy (ubuntu-6.10-server-amd64.iso) on the Dell PowerEdge 2950 worked almost flawlessly.  The only thing that didn't work was dhcp networking.  However, after rebooting, I configured  /etc/network/interfaces to use static IPs, which worked just fine.

Regards,
- Robert

---

### Post by jfdill_2 on 2006-11-06
I just finished installing 6.06.1 LTS amd64 server on a PowerEdge 1950 using the instructions from this thread.  There is one last wrinkle if you want to use LVM2:  vgscan will find duplicate UUIDs because it will read the devices on /dev/sda, /dev/sdb, and /dev/sdc and so on, depending on how many physical drives you have.

I have 2 drives in a RAID1 configuration.  I had to add filters to /etc/lvm/lvm.conf to stop it from scanning /dev/sda and /dev/sdb.  For simplicity, I did this:

```

scan = [ "/dev/evms" ]

filter = [ "a|/dev/evms/sdc|", "r|/dev/evms/sda|", "r|/dev/evms/sdb|" ]

```

It concerns me that this will "break" if one of the drives fails and sdc turns into sdb.  Maybe there is a more elegant or correct way to do this so it won't break.  If I figure it out, I can clean this up later.

---

### Post by Robert Citek on 2006-11-06
> **jfdill_2 said:**
> Maybe there is a more elegant or correct way to do this so it won't break.  If I figure it out, I can clean this up later.
You may want to try installing with Edgy (6.10).  The driver seems to be fixed in Edgy so that only one drive (the logical drive) appears.

Regards,
- Robert

---

### Post by paul.maddox on 2006-11-06
> **Robert Citek said:**
> You may want to try installing with Edgy (6.10).  The driver seems to be fixed in Edgy so that only one drive (the logical drive) appears.

It's very tempting, but edgy doesn't have the same long-term support. Is it really okay for production servers?

---

### Post by chewie124 on 2006-11-07
Glad to see the bug where all the physical drives are shown in a RAID array has a solution committed.  Next question - anybody know the ETA when the next update to the linux kernel that includes this patch will be released?

TIA!

---

### Post by rcgabriel on 2006-11-07
Paul - I agree 100%.  I have two rather critical servers that are going to be shipped out to our colo for production use next week.  They seem to be working fantastically with Ubuntu 6.06LTS right now, after following the steps in this thread.  

I've had zero problems with these servers, and moving to Edgy just for the aesthetics of not having the two dangling detected drives seems unnecessary to me.  It would be nice to be able to roll out more servers with a stock install process and not to have to do the extra install steps, but it's not worth moving to a less stable Ubuntu release.

---

### Post by hogman23 on 2006-11-08
> **Robert Citek said:**
> Confirmed.  Reinstalling using edgy (ubuntu-6.10-server-amd64.iso) on the Dell PowerEdge 2950 worked almost flawlessly.  The only thing that didn't work was dhcp networking.  However, after rebooting, I configured  /etc/network/interfaces to use static IPs, which worked just fine.

Regards,
- Robert


I tried installing the 6.10 server, but now we have no keyboard???  Anyone know how to fix this?

---

### Post by peacefrog on 2006-12-08
Im a bit a Ubuntu noob, but this has been very informative. Im running 6.06 Dapper on a PowerEdge 2950 I think I have everything working correctly except the Broadcom drivers which this had addressed. 

Im just curious if I get DHCP correctly handing out addresses, is anyone having issues doing PXE booting right into the server on a thin client or WinTerminal?

---

### Post by Robert Citek on 2006-12-08
> **hogman23 said:**
> I tried installing the 6.10 server, but now we have no keyboard???  Anyone know how to fix this?

The keyboard worked for us.  I'm assuming you've checked the obvious: keyboard is plugged in the USB port and the keyboard works in other machines.    After that, check if other USB devices work in that USB port and if the keyboard works with other Linux distros (e.g. Knoppix) on the PE2950.

Let us know how it goes.

Regards,
- Robert

---

### Post by chewie124 on 2006-12-08
I ran into a similar problem.  It was resolved when I switched from a crappy POS USB keyboard from target to a crappy POS ps/2 keyboard from dell, but I used a ps/2 to usb converter to connect it.  the brand is: CHESEN PS2 to USB Converter

---

### Post by gabrielcz on 2006-12-30
> **Grizzly_Adams said:**
> Problem with network card solved.

Ubuntu does not detect the network cards during installation, however it is possible to activate them after first boot by adding the necessary entry for the interface in the /etc/network/interfaces file, then ifup'ing the interface.

So I can confirm that it is possible (though a little difficult to setup) to run Ubuntu 6.06 on a Dell 2950.

Hi dude, new here..  I have same problem, but I dont' undestand how to "activate" exclacly
Im new here, can you tell me how exacly please? I will thank you :P

---

### Post by chewie124 on 2006-12-30
It's been a little while, but IIRC, after first boot, you just need to tell the kernel to use the tg3 module for the ethernet driver.  So, in short, add either the [FONT="Courier New"]tg3[/FONT] or the [FONT="Courier New"]bnx2[/FONT] module to /etc/modules, and then make sure /etc/network/interfaces is setup right.  You should have connectivity on your next reboot.

I'm sorry I can't be more specific with the module,  IIRC, using the Ubuntu Kernel (dapper), I had to use the [FONT="Courier New"]tg3[/FONT] ethernet driver.  But now it's running the XEN kernel, and when I do an lsmod, it's using the [FONT="Courier New"]bnx2[/FONT] driver.

HTH!

Happy New Year!

---

### Post by efuller on 2007-01-11
Paul.maddox,

I dont have mail going on the server I want to put up. Just data and VPN. Any simple way I could use your script to send myself notification without the hassle of setting up sendmail? Maybe a different mail protocol?

---

### Post by quad3d@work on 2007-01-18
I'm still having issues getting it to work on PE 1950s. I've tried both 6.06 and 6.06.1 32-bit server installation.

It seems like it's detected w/ bnx2 module and loads up correctly (dmesg). I can't ping GW, can't ping other box on same network... etc. I can ping the IP(s) I assigned the NIC.

I tried disabling bnx2 module and use tg3 but doesn't seem to work at all. Can't even load up the NICs.

Can anyone shed some lights on this? Any suggestions appreciated.

p.s. Same box loads up on RHEL4 fine and NIC works. I compared various things between the two and seems to be same configs.

---

### Post by chewie124 on 2007-01-18
Can you ping out after the network has been setup when you've booted it up off the ubuntu installation disk?

anything interesting in dmesg or in /var/log/messages?

I used the AMD64 bit installation for my 2950.  are the 1950's strictly 32 bit?

---

### Post by quad3d@work on 2007-01-19
During installation CD bootup NIC isn't detected at all.

dmesg or /var/log/message doesn't show anything abnormal that I can see...

```
ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 169
eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B1) PCI-X 64-bit 133MHz found at mem f4000000, IRQ 169, node addr 0015c5ee6ab3
ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 169
eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B1) PCI-X 64-bit 133MHz found at mem f4000000, IRQ 169, node addr 0015c5ee6ab1
bnx2: eth0: using MSI
bnx2: eth1: using MSI
```I can tail -f /var/log/messages and unplug/plug the NIC cable seeing it saying eth1 link down and link up... etc.

I'm going to switch to a different VLAN and try out see if it works or not.... if not I might test out 64-bit installation since from what I've read quite a few people got it working in instead of 32.

---

### Post by jbaloul on 2007-01-19
Hey Guys,
Just went through the same Saga with yet another PowerEdge...this time a 420SC...

Bottom line,
If you don't need or aren't looking for the long term dapper support, and/or don't want to get into hacks...go with Edgy (6.10-server) it detects everything out of the box!

So our Thread Experience is now safe to say that all of the below are effected:
PE 2950
PE 1950
PE 420SC

--
JB
[http://howtoforums.net](http://howtoforums.net)

---

### Post by quad3d@work on 2007-01-19
Ok, I figured out what was the problem.

We running 14 different VLANs here and the Cisco switch port my server plugged into was configured to diff. VLAN. Another case of PEBKAC... Thanks for the help.

---

### Post by reech on 2007-03-22
For those that would like to monitor their machines/perc arrays  I managed to get omsa installed on my 2950/dapper 6.06.1  like so: 

install openipmi and ipmitool:
```
sudo apt-get install openipmi 
sudo apt-get install ipmitool
```

install lib32ncurses and ia32-libs:
```
sudo apt-get install -f lib32ncurses5
sudo apt-get install -f ia32-libs
```

grab omsa:
```
wget ftp://ftp.sara.nl/pub/outgoing/dell/binary-amd64/dellomsa_5.1.0-5_amd64.deb
```

install omsa:
```
dpkg -i dellomsa_5.1.0-5_amd64.deb
```

For starters:```
sudo omreport storage controller
```

the CLI userguide is here (seems a little removed from reality):
[http://support.dell.com/support/edocs/software/svradmin/5.1/en/cli/html/index.htm](http://support.dell.com/support/edocs/software/svradmin/5.1/en/cli/html/index.htm)

disclaimer - : have forced some packages here - follow these instructions at your own risk.

---

### Post by Ichibod on 2007-04-04
Hey all... great comments and help here!

Sorry, I'm so late to the party, but I just got my hands on a new Dell 2950 w/ a single quad-core Xeon and 3 SAS drives that I have stacked into a single logical RAID-5 disk.

My situation is this:  I need to get a Linux server up and running within the next few weeks, and the objective is to not ***pay*** for Linux.  (You can read that as "no RedHat & no SuSe". :))  Ubuntu would be my poison of choice, as I've been a fan of it for some time now on the desktop side of life.

Now, after having tried just about everything version of Ubuntu on the market (along with every trick or tip I could find on the 'Net - including lots of good ones from this thread), I still have a few issues outstanding.

At present, I have the box loaded with the AMD64 version of 6.10 desktop.  (I chose desktop, as a few key services I need to host require X.  So, after running the server install a time or three and then having to fetch X, I decided to go straight for it.)  Overall, the system is running well and seems responsive.  However, a few system messages are still bothering me...

My key issues:
1.)**APIC** - Though not mentioned here, a 'dmesg | grep error' shows me:
```

APIC error on CPU1: 00(40)
APIC error on CPU2: 00(40)
APIC error on CPU3: 00(40)

```
... as in the following context ...
```

[  180.418107] Initializing CPU#3
[  180.495144] Calibrating delay using timer specific routine.. 3193.02 BogoMIPS (lpj=6386051)
[  180.495152] CPU: L1 I cache: 32K, L1 D cache: 32K
[  180.495154] CPU: L2 cache: 4096K
[  180.495157] CPU: Physical Processor ID: 0
[  180.495159] CPU: Processor Core ID: 3
[  180.495166] CPU3: Thermal monitoring enabled (TM2)
[  180.495783] Intel(R) Xeon(R) CPU           E5310  @ 1.60GHz stepping 07
[  180.499140] APIC error on CPU3: 00(40)
[  180.499156] Brought up 4 CPUs

```
I saw this message regardless of the Ubuntu version I installed.  (Everything from 6.06.0 -> 6.10.)  From my online reading, it sounds like this is a known bug that some have fixed with a BIOS update.  ([https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66900](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66900))  I, however, have Dell's latest BIOS for my machine (1.2.0) and am still having it.  I've read where I can potentially disable it with a parameter or 2 to the kernel, but I'm wondering what the impact would be there to my system.  I'd obviously prefer to just resolve this w/o trying to shut APIC off.  Thoughts?

2.)**RAID issues** - Like everyone else here, I'm still having a bit of trouble with my PERC5 RAID controller.  On the whole, things *seem* fine.  The system boots, I can read and write, etc.  During install of 6.10 (both server and desktop versions), only the logical drive showed up.  (On my box, it was listed as **/dev/sda**.)  Having installed everything there, I'm still getting the following warnings:
```

sda: test WP failed, assume Write enabled

```
and
```

sda: asking for cache data failed
sda: assuming drive cache: write through

```
(the context for both of these follows:)
```

[  184.488569] scsi0 : LSI Logic SAS based MegaRAID driver
[  184.489846]   Vendor: SEAGATE   Model: ST3300555SS       Rev: T107
[  184.489859]   Type:   Direct-Access                      ANSI SCSI revision: 05
[  184.490964]   Vendor: SEAGATE   Model: ST3300555SS       Rev: T107
[  184.490975]   Type:   Direct-Access                      ANSI SCSI revision: 05
[  184.492049]   Vendor: SEAGATE   Model: ST3300555SS       Rev: T107
[  184.492060]   Type:   Direct-Access                      ANSI SCSI revision: 05
[  184.549790] Probing IDE interface ide1...
[  184.575043] usbcore: registered new driver usbfs
[  184.575067] usbcore: registered new driver hub
[  184.576187] USB Universal Host Controller Interface driver v3.0
[  184.576238] GSI 18 sharing vector 0x4A and IRQ 18
[  184.576242] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 74
[  184.576253] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  184.576257] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[  184.576366] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[  184.576391] uhci_hcd 0000:00:1d.0: irq 74, io base 0x0000dce0
[  184.576475] usb usb1: configuration #1 chosen from 1 choice
[  184.576497] hub 1-0:1.0: USB hub found
[  184.576504] hub 1-0:1.0: 2 ports detected
[  184.590867]   Vendor: DP        Model: BACKPLANE         Rev: 1.00
[  184.590881]   Type:   Enclosure                          ANSI SCSI revision: 05
[  184.655919]   Vendor: DELL      Model: PERC 5/i          Rev: 1.00
[  184.655931]   Type:   Direct-Access                      ANSI SCSI revision: 05
[  184.670641] SCSI device sda: 1169686528 512-byte hdwr sectors (598880 MB)
[  184.670731] sda: test WP failed, assume Write Enabled
[  184.670762] sda: asking for cache data failed
[  184.670765] sda: assuming drive cache: write through
[  184.670849] SCSI device sda: 1169686528 512-byte hdwr sectors (598880 MB)
[  184.670936] sda: test WP failed, assume Write Enabled
[  184.670966] sda: asking for cache data failed
[  184.670968] sda: assuming drive cache: write through
[  184.670972]  sda: sda1 sda2 <<6>GSI 19 sharing vector 0x52 and IRQ 19
[  184.680477] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 82
[  184.680486] PCI: Setting latency timer of device 0000:00:1d.1 to 64

```
This all tells me that Ubuntu still isn't buddying up to my PERC adapter as I'd like.  Thoughts here?  I would love to kill off as many of these messages as possible.  However, I understand some of them may be harmless enough to ignore.  I just need someone to help me sort out the difference.  :)

3.) **ACPI** (not to be confused with the *APIC* issue above.) - I'm also getting the following:
```

[  181.879976] fb0: VGA16 VGA frame buffer device
[  182.908316] Capability LSM initialized
[  182.944533] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[  182.944539] ACPI: Getting cpuindex for acpiid 0x5
[  182.944545] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[  182.944549] ACPI: Getting cpuindex for acpiid 0x6
[  182.944554] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[  182.944558] ACPI: Getting cpuindex for acpiid 0x7
[  182.944564] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[  182.944568] ACPI: Getting cpuindex for acpiid 0x8

```
Is this something to worry about?

Thanks again for all your help and excellent posts!

Ichi

---

### Post by Ichibod on 2007-04-10
Quick update...

I tried tossing the 7.04-beta 64-bit desktop software on the machine, and all of the APIC issues appear resolved.  HORRAY!

So, all that remains are the sda warnings associated with the PERC5 controller.  Any thoughts on that.

I do wish I had something with some longer term support up and running this well, but for my operation, I'll trade LTS for stability if I need to.

---

### Post by ipfreely on 2007-04-10
Hi All,
Thanks for all the info.  I have used this info to get my server up and running.  
During the bootup I get a bunch of I/O Buffer Errors.  Is this normal?
I am using Ubuntu 6.06.1 64 bit version.  Below are the errors

 I am running 3 drives in a RAID5 Config.

 [   89.045100] sd 0:0:2:0: Attached scsi disk sdc
 [   89.045179] SCSI device sdd: 284164096 512-byte hdwr sectors (145492 MB)
 [   89.045223] sdd: asking for cache data failed
 [   89.045506] sdd: assuming drive cache: write through
 [   89.045891] SCSI device sdd: 284164096 512-byte hdwr sectors (145492 MB)
 [   89.045931] sdd: asking for cache data failed
 [   89.046208] sdd: assuming drive cache: write through
 [   89.046214]  sdd: sdd1 sdd2 < sdd5 >
 [   89.051056] sd 0:2:0:0: Attached scsi disk sdd
 [   89.451993] Buffer I/O error on device sda1, logical block 136303360
 [   89.452341] Buffer I/O error on device sda1, logical block 136303361
 [   89.452674] Buffer I/O error on device sda1, logical block 136303362
 [   89.453014] Buffer I/O error on device sda1, logical block 136303363
 [   89.453377] Buffer I/O error on device sda1, logical block 136303360
 [   89.453729] Buffer I/O error on device sda2, logical block 0
 [   89.454062] Buffer I/O error on device sda1, logical block 136303361
 [   89.454396] Buffer I/O error on device sda1, logical block 136303362
 [   89.460683] Buffer I/O error on device sda1, logical block 136303363
 [   89.466777] Buffer I/O error on device sda2, logical block 0

Thanks,
Chris

---

### Post by ndefontenay on 2007-04-12
Hi.

My company just bought a Dell 2950.

I planned to install Ubuntu 6.06 LTS on it but failed to do so. I had no keyboard and no mouse.

It's detected at the very beginning, but when I'm prompted to choose a language for the installation, the keyboard and mouse light goes off and I can't use it anymore...

I've tried to install kubuntu 6.06 LTS desktop edition and it installed better...

However, when I reboot the server I fall into the "No Operating system detected" trap.

I'm planning to download the 6.10 release instead. I've heard everything worked out of the box and I'm quite ok to live without support after 2008. This server is meant for VMware and development. No production.

Has anyone faced keyboard/mouse problem on 6.10?

Thanks

---

### Post by ColdCanuck on 2007-04-18
> **Ichibod said:**
> Hey all... great comments and help here!

Sorry, I'm so late to the party, but I just got my hands on a new Dell 2950 w/ a single....

```

[  184.670641] SCSI device sda: 1169686528 512-byte hdwr sectors (598880 MB)
[  184.670731] sda: test WP failed, assume Write Enabled
[  184.670762] sda: asking for cache data failed
[  184.670765] sda: assuming drive cache: write through

```


This all tells me that Ubuntu still isn't buddying up to my PERC adapter as I'd like.  Thoughts here?  I would love to kill off as many of these messages as possible.  However, I understand some of them may be harmless enough to ignore.  I just need someone to help me sort out the difference.  :)




Not really. The "error message" is saying the disk is not WP (Write Protected) which is generally a good thing for disks you wish to write to. (The error message comes from the scsi layer providing support for CF cards etc, which can be Write Protected)

The second message just means what it says, the Linux driver is assuming that the controller has a write through cache. The PERC can be set to write-back or write-through., but does not tell the kernel which it is, so the driver is assuming write through, the safer assumption.

The latest BIOS from Dell is 1.3.7, released in the last week. You might want to try a BIOS update to fix some of the other warts. This of course just opens you to a whole new world of hurt, as all the firmware update tools are RH based. You might want to monitor the linux-poweredge mailing list at dell.com, there are lots of Ubuntu people there.

---

### Post by badmojo on 2007-05-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I followed someones post here, sorry I forget who... how to work around this problem with 1950/2950 perc5 raid and managed to get the system up and running (successfully now for 5 months) using 6.06.1 server x86. 
It's our production email server. So thank you whoever it was.

Now I have recently read that the bug related to the physical disks has been resolved with linux-image 2.6.15-28 from security updates.

Any advice on how to go about getting this working so that I do not see sda, b, c, d, and sde (logical drive).
I would feel much better if I simply have sda (logical) showing up and not all of the physical disks.

I installed the kernel image using apt and rebooted, no luck, it simply hangs during startup.
Had to go back to previous kernel (2.6.15-26).
I am assuming I am missing something but unsure what.

Has anyone done this successfully :confused:

---

### Post by jfdill_2 on 2007-05-11
> **badmojo said:**
> **This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I followed someones post here, sorry I forget who... how to work around this problem with 1950/2950 perc5 raid and managed to get the system up and running (successfully now for 5 months) using 6.06.1 server x86. 
It's our production email server. So thank you whoever it was.

Now I have recently read that the bug related to the physical disks has been resolved with linux-image 2.6.15-28 from security updates.

Any advice on how to go about getting this working so that I do not see sda, b, c, d, and sde (logical drive).
I would feel much better if I simply have sda (logical) showing up and not all of the physical disks.

I installed the kernel image using apt and rebooted, no luck, it simply hangs during startup.
Had to go back to previous kernel (2.6.15-26).
I am assuming I am missing something but unsure what.

Has anyone done this successfully :confused:

I did, also on a production mail server, but I got no love from GRUB, I ended up switching to LILO just to get the thing up and running again, don't remember what was the exact error or why I couldn't get GRUB to boot though.  At least liloconfig worked beautifully.  I think it had something to do with having both RAID1 and LVM and GRUB no longer being able to find some of the stages.  Booting from a Feisty Fawn Desktop CD (amd64) and using Live mode was easier than trying to do it with the Dapper CD which still has a "broken" kernel, or using the Feisty Fawn Server CD in "Rescue" mode.  I have another server to do in the near future, I think this is the procedure I'm going to follow:

1. install LILO
2. purge GRUB
3. run liloconfig
4. boot system from Feisty Fawn Desktop for amd64 CD
5. mount root on e.g. /media/target
6. mount -bind /proc, /sys, and /dev to the target
7. chroot /media/target
8. edit /etc/fstab, check lilo.conf
9. run lilo; sync; lilo; sync (paranoid overkill from the good ol' days!)
10. umount -a
11. exit chroot
12. umount proc, sys, and dev in the target
13. umount /media/target
14. reboot, eject CD, and cross fingers!

I'll try to keep better notes of what I do next time, please don't kill me if this blows up ur box!

---

### Post by iskatyel on 2007-05-17
This has been a very informative thread and I read it carefully before ordering my PE 1950, assuming I would be able to work through these issues.  I seem to be getting a totally different problem, though, and any advice would be appreciated.  

First, my PE 1950 has a PERC5/i in RAID 1 with 2 250GB 7.2k rpm drives and is running dual quad-core 1.6Ghz Xeons with 4GB of RAM.

I have tried 6.06.1 and 7.04, 64-bit and 32, desktop and server, and I get the same error at the same point during the install.  It loads the linux kernel, then the screen reads: 
[1099.412147] sda: asking for cache data failed 
[1099.412205] sda: assuming drive cache: write through 

The numbers in brackets change each time I attempt to start the install and from what I have read these errors may be normal.  At any rate, after this it always goes into an endless loop printing:

on 6.06.1: “/build/buildd/cdebconf-0.97ubuntu3/src/debconf.c:135 (main): Cannot initialize debconf template database” 

and on 7.04: “/build/buildd/cdebconf-0.111ubuntu2/src/debconf.c:135 (main): Cannot initialize debconf template database”

Again, any help or suggestions at this point would be great as I am pretty stuck.

Dan

---

### Post by jbaloul on 2007-05-17
Guys,
I have to share with you yet another experience with the Dell 1950...

We have been using the Dell 1950 with Ubuntu Dapper pretty much since we started this thread here...I have been happy with the performance and we wanted to take things a bit further.
I have been running it as a vmware server and all was well, till...
We decided to get fancy and attempt to add a 750GB eSata disk hooked up to the onboard Sata controller.
The idea was to push the server to its limits while running multiple vmware guests in SMP mode (dual cpu config) using vmware server .
Well turns out my friends that not only does Ubuntu NOT support sata & vmware SMP the way it should be, but NO current Linux kernel can handle it !!!!
Your probably saying to yourself right now "this guy is crazy, linux has been supporting sata & vmware forever..."
well wrong...let me just show you a glimpse of the errors we got from benchmarking this baby...

when read and right destinations are from sata disk to sata disk (same disk)
   and kernel = 2.6.20-15-generic #2 SMP (feisty)
result = 

```

May 11 18:47:39 jbdual kernel: [  517.040000]          res 50/00:00:c0:7c:67/00:00:28:00:00/e0 Emask 0x1 (device error)
May 11 18:47:39 jbdual kernel: [  517.196000] ata1.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May 11 18:47:39 jbdual kernel: [  517.260000] ata1.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May 11 18:47:39 jbdual kernel: [  517.260000] ata1.00: configured for UDMA/133
May 11 18:47:39 jbdual kernel: [  517.264000] ata1: EH complete
May 11 18:47:39 jbdual kernel: [  517.308000] SCSI device sda: 1465149168 512-byte hdwr sectors (750156 MB)
May 11 18:47:39 jbdual kernel: [  517.308000] sda: Write Protect is off
May 11 18:47:39 jbdual kernel: [  517.312000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
 
That is written to the log every once in a while...and the system freezes and unfreezes, sometimes fatally



when read and right destinations are from sata disk to local disk
   and kernel = 2.6.17-10-generic #2 SMP (edgy)
result = no problem, copy succeed

when read and right destinations are from sata disk to sata disk 
   and kernel = 2.6.17-10-generic #2 SMP (edgy)
result = 
```

May 11 11:07:16 sandbox kernel: [17190144.332000] ata1: status=0x50 { DriveReady SeekComplete }
May 11 11:07:16 sandbox kernel: [17190144.332000] sda: Current: sense key: No Sense
May 11 11:07:16 sandbox kernel: [ 17190144.332000]     Additional sense: No additional sense information

```
....copy succeed..system freezes....integrity and reliability a question


when read and right destinations are from sata disk to local disk
   and kernel = 2.6.15-26-server #1 SMP (dapper)
result = no problem, copy succeed

when read and right destinations are from sata disk to sata disk
   and kernel = 2.6.15-26-server #1 SMP (dapper)
result =
```

May 11 15:27:38 vmhostdell kernel: [43018680.390000] ata1: status=0x51 { DriveReady SeekComplete Error }
May 11 15:27:38 vmhostdell kernel: [43018680.390000] ata1: error=0x84 { DriveStatusError BadCRC }

```
....copy fails

now take a look at this...
online research:
[http://www.google.com/search?hl=en&q=ata1%3A+status%3D0x50+%7B+DriveReady+SeekComplete+%7D&btnG=Google+Search](http://www.google.com/search?hl=en&q=ata1%3A+status%3D0x50+%7B+DriveReady+SeekComplete+%7D&btnG=Google+Search) 

[http://bugzilla.kernel.org/show_bug.cgi?id=7516](http://bugzilla.kernel.org/show_bug.cgi?id=7516)

**BOTTOM LINE**
We not only tried everything we found online, but also tried using a Promise pci card.
Tried multiple versions of the distro, multiple versions of vmware, changed cables, changed box's, and much more...
Nothing is reliable enough to do REAL work with....The minute you start heavy I/O the system becomes unstable.
The closest thing to making it work was with Feisty (7.04) which has the latest kernel, however that too is unreliable, and Feisty is so broken its not even funny...vmware has to be hacked to make it work, apache ssl certificates is broken, scanning is broke, and more...i cannot beleive they released it the way they did.
AND NOW for the saddest part of all...
We tried to install Windows 2003 on the server just for the heck of it...I can tell you guys, that for the first time Windows rescued us from Linux...everything just worked: eSata, Vmware SMP, systems where flying!
I would be so happy if anyone would come to the rescue and prove me wrong ...or else we will be migrating a cluster of Ubuntu servers to Windows ;'(

Praying for the future of Linux,
Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by jfdill_2 on 2007-05-18
> **iskatyel said:**
> I have tried 6.06.1 and 7.04, 64-bit and 32, desktop and server, and I get the same error at the same point during the install.  It loads the linux kernel, then the screen reads: 
[1099.412147] sda: asking for cache data failed 
[1099.412205] sda: assuming drive cache: write through

Sorry I can't tell you what the problem is, but I can tell you that it is NOT that, that is just a warning message and should not cause any problems at all, for sure it would not cause the system to lock up.  Basically, the kernel tried to ask the hardware if write caching is enabled, the kernel did not get a response, or did not understand the response that it received, so it assumes the more conservative option.  That message is a red herring.

---

### Post by jfdill_2 on 2007-05-18
> **iskatyel said:**
> At any rate, after this it always goes into an endless loop printing:

on 6.06.1: “/build/buildd/cdebconf-0.97ubuntu3/src/debconf.c:135 (main): Cannot initialize debconf template database” 

and on 7.04: “/build/buildd/cdebconf-0.111ubuntu2/src/debconf.c:135 (main): Cannot initialize debconf template database”

Again, any help or suggestions at this point would be great as I am pretty stuck.

Dan

A similar problem seems to happen in Debian, could be a problem with ACPI or some kernel module.  The error message could be a side-effect of you hitting Ctrl-C.  Booting with noapic and/or acpi=off kernel options may help, but I am not sure how to do that with the install CD.  I'd say stick with amd64 and Feisty Fawn (7.04) that should have the best complement of drivers for PE1950, but try Desktop, Server, and/or Alternate CDs, whichever you have not tried yet.

[http://www.nabble.com/Problem-with-debconf-on-AMD64-of-Etch-RC1-t3168792.html](http://www.nabble.com/Problem-with-debconf-on-AMD64-of-Etch-RC1-t3168792.html)

Another possibility is that the CDs that you are writing are bad for some reason, or there is a problem with the CD drive in the server, whether it is the drive itself, or access to the CD drive from ubuntu.  You could try the option to check the CD.  I'd probably also try booting a KNOPPIX CD to see if that loads successfully or yields more errors.  Another option might be to boot off a KNOPPIX CD, set up and mount your partitions, then use debootstrap to "install" Ubuntu onto the server, I vaguely recall seeing a howto somewhere to do this, think it was for an older version of Ubuntu.

---

### Post by iskatyel on 2007-05-18
Alright, I went home and slept on it.  Got up this morning and disconnected the keyboard and mouse from the KVM switch, plugged a USB keyboard and mouse in the face of the server and it works like a champ.  We have had some trouble with our PE 2950 that is running NetWare 6.5 hanging when the mouse is connected as well.  Several reboots later it looks like the problem is actually the keyboard I was using.  

We had an IBM server keyboard with the integrated pointer stick for use on the rack and it gives us no trouble for any of our HP workstations running WinXP, the Win2k3 server running on a PE 650, Ubuntu 6.06.1 running on a PE 650, or a custom Linux-based IDS running on a PE 850, but Netware 6.5 and Ubuntu anything on a PE 1950 or PE 2950 will choke and hang with this keyboard connected.  Perhaps it's because the keyboard is a natively PS/2 keyboard getting adapted to plug into the USB on the 2950 and 1950?  At any rate, do not use IBM P/N 37L0888 with a PE 2950 or 1950, you will regret it.

As far as the PERC5/i issues are concerned, 7.04 loaded great with no issues.

Best,
Dan

jfdill_2 - Thanks for the suggestions, I had tried running it with both noapic and acpi=off with no success (in the installer you do this by hitting F6 and then editing the install command before beginning) and I did the MD5 checksums to verify the integrity of the disks.  That was about all the ideas anyone had searching the ubuntu forums and googling so I posted here.  It looks like the debconf installer problem is usually a pretty basic problem with the hardware or the install disks and everything looks fine now on my PE 1950.

---

### Post by jfdill_2 on 2007-05-19
> **iskatyel said:**
> Alright, I went home and slept on it.  Got up this morning and disconnected the keyboard and mouse from the KVM switch, plugged a USB keyboard and mouse in the face of the server and it works like a champ.  We have had some trouble with our PE 2950 that is running NetWare 6.5 hanging when the mouse is connected as well.  Several reboots later it looks like the problem is actually the keyboard I was using.

This could be very useful information, I'm likely to run into that problem sometime myself.  I have my 1950 hooked up to a Belkin PS/2 keyboard / mouse to USB dongle then that connects to a PS/2 KVM, since the KVM also connects to a bunch of (somewhat older) servers that have PS/2 ports.

---

### Post by badmojo on 2007-06-01
> **jbaloul said:**
> Guys,
I have to share with you yet another experience with the Dell 1950...

We have been using the Dell 1950 with Ubuntu Dapper pretty much since we started this thread here...I have been happy with the performance and we wanted to take things a bit further.
I have been running it as a vmware server and all was well, till...
We decided to get fancy and attempt to add a 750GB eSata disk hooked up to the onboard Sata controller.
The idea was to push the server to its limits while running multiple vmware guests in SMP mode (dual cpu config) using vmware server .
Well turns out my friends that not only does Ubuntu NOT support sata & vmware SMP the way it should be, but NO current Linux kernel can handle it !!!!
Your probably saying to yourself right now "this guy is crazy, linux has been supporting sata & vmware forever..."
well wrong...let me just show you a glimpse of the errors we got from benchmarking this baby...

when read and right destinations are from sata disk to sata disk (same disk)
   and kernel = 2.6.20-15-generic #2 SMP (feisty)
result = 

```

May 11 18:47:39 jbdual kernel: [  517.040000]          res 50/00:00:c0:7c:67/00:00:28:00:00/e0 Emask 0x1 (device error)
May 11 18:47:39 jbdual kernel: [  517.196000] ata1.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May 11 18:47:39 jbdual kernel: [  517.260000] ata1.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May 11 18:47:39 jbdual kernel: [  517.260000] ata1.00: configured for UDMA/133
May 11 18:47:39 jbdual kernel: [  517.264000] ata1: EH complete
May 11 18:47:39 jbdual kernel: [  517.308000] SCSI device sda: 1465149168 512-byte hdwr sectors (750156 MB)
May 11 18:47:39 jbdual kernel: [  517.308000] sda: Write Protect is off
May 11 18:47:39 jbdual kernel: [  517.312000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
 
That is written to the log every once in a while...and the system freezes and unfreezes, sometimes fatally



when read and right destinations are from sata disk to local disk
   and kernel = 2.6.17-10-generic #2 SMP (edgy)
result = no problem, copy succeed

when read and right destinations are from sata disk to sata disk 
   and kernel = 2.6.17-10-generic #2 SMP (edgy)
result = 
```

May 11 11:07:16 sandbox kernel: [17190144.332000] ata1: status=0x50 { DriveReady SeekComplete }
May 11 11:07:16 sandbox kernel: [17190144.332000] sda: Current: sense key: No Sense
May 11 11:07:16 sandbox kernel: [ 17190144.332000]     Additional sense: No additional sense information

```
....copy succeed..system freezes....integrity and reliability a question


when read and right destinations are from sata disk to local disk
   and kernel = 2.6.15-26-server #1 SMP (dapper)
result = no problem, copy succeed

when read and right destinations are from sata disk to sata disk
   and kernel = 2.6.15-26-server #1 SMP (dapper)
result =
```

May 11 15:27:38 vmhostdell kernel: [43018680.390000] ata1: status=0x51 { DriveReady SeekComplete Error }
May 11 15:27:38 vmhostdell kernel: [43018680.390000] ata1: error=0x84 { DriveStatusError BadCRC }

```
....copy fails

now take a look at this...
online research:
[http://www.google.com/search?hl=en&q=ata1%3A+status%3D0x50+%7B+DriveReady+SeekComplete+%7D&btnG=Google+Search](http://www.google.com/search?hl=en&q=ata1%3A+status%3D0x50+%7B+DriveReady+SeekComplete+%7D&btnG=Google+Search) 

[http://bugzilla.kernel.org/show_bug.cgi?id=7516](http://bugzilla.kernel.org/show_bug.cgi?id=7516)

**BOTTOM LINE**
We not only tried everything we found online, but also tried using a Promise pci card.
Tried multiple versions of the distro, multiple versions of vmware, changed cables, changed box's, and much more...
Nothing is reliable enough to do REAL work with....The minute you start heavy I/O the system becomes unstable.
The closest thing to making it work was with Feisty (7.04) which has the latest kernel, however that too is unreliable, and Feisty is so broken its not even funny...vmware has to be hacked to make it work, apache ssl certificates is broken, scanning is broke, and more...i cannot beleive they released it the way they did.
AND NOW for the saddest part of all...
We tried to install Windows 2003 on the server just for the heck of it...I can tell you guys, that for the first time Windows rescued us from Linux...everything just worked: eSata, Vmware SMP, systems where flying!
I would be so happy if anyone would come to the rescue and prove me wrong ...or else we will be migrating a cluster of Ubuntu servers to Windows ;'(

Praying for the future of Linux,
Jacob
[http://howtoforums.net](http://howtoforums.net)

Jbaloul, we're running VMware server on our 2950 with 6x 500GB sata hardware raid5, no problems or errors.

Debian 4.0 (2way smp) (2.6.18-4-amd64 #1 SMP Mon Mar 26 11:36:53 CEST 2007 x86_64 GNU/Linux), 
Dell OMSA utils, VMware Server, VMware-mui, Samba+AD, and various other services.
This server hosts about 6 VMs simultaneously, our financial servers Mas90 & FAS100 and a few other database systems used internally.
It also hosts some testbed VM images for Cisco CallManager 5.0 and Cisco Unity.

We also run Ubuntu 6.06.1 i686 (4way smp) on a 1950 for our corporate email server, pretty much the same software with VMware as above plus Postfix, Apache, MySQL, no problems other than the megaraid sas bug.
This system handles about 200,000 emails a month, plus the spam filtering on top of that.
Needless to say Disk activity is rather high here.

Both of these systems are under pretty heavy load continuously.

Please don't take this the wrong way, but are you sure your not crying wolf?
Or maybe just user error? Maybe I'm not understanding your problem correctly?

---

### Post by jbaloul on 2007-06-01
badmojo,
From looking at your configuration it looks much different than the one i described.
* Your setup consists of "6x 500GB sata hardware raid5" on a controller that is different than mine.
* 2.6.18-4-amd64 is a Debian kernel that i did not try.
* I did not install, "Dell OMSA utils" which definitely can impact the results. My install is strait clean ubuntu with vmware server.
* You did not mention if you have any of the Guest OS's in Dual CPU mode? That is where the disasters start in VMware on Linux.

Like I said...no problems before till we started to get fancy...
The onboard SATA controller on the Dell PE 1950 and an external Promise SATA PCI card where the ones giving the disk errors & the VMware Dual CPU Guests of course.

Many in this thread are running different configs so it is hard to tell who is "crying wolf" or not, i can see your point...but I know that in my case we pretty much did everything possible.

Jacob

---

### Post by badmojo on 2007-06-01
> **jbaloul said:**
> badmojo,
From looking at your configuration it looks much different than the one i described.
* Your setup consists of "6x 500GB sata hardware raid5" on a controller that is different than mine.
* 2.6.18-4-amd64 is a Debian kernel that i did not try.
* I did not install, "Dell OMSA utils" which definitely can impact the results. My install is strait clean ubuntu with vmware server.
* You did not mention if you have any of the Guest OS's in Dual CPU mode? That is where the disasters start in VMware on Linux.

Like I said...no problems before till we started to get fancy...
The onboard SATA controller on the Dell PE 1950 and an external Promise SATA PCI card where the ones giving the disk errors & the VMware Dual CPU Guests of course.

Many in this thread are running different configs so it is hard to tell who is "crying wolf" or not, i can see your point...but I know that in my case we pretty much did everything possible.

Jacob

Jacob, to quote you "but NO current Linux kernel can handle it !!!!".
What does it matter then if I'm running a similar Debian Kernel...? ;)

* Why should OMSA make any major difference? It's a system monitoring tool for the most part.
Dell OMSA was installed about 4 months after the system went into production, the 1950 has been running since mid December, so that is about 2 months of heavy usage,
without Dell OMSA installed. 

* I've also run a 1950 in a classroom/lab environment with 8 simultaneous VMs as well with the non raid controller from Dell as well, just a simple SAS disk. No problems.
I just didn't mention it because it is no longer in my hands. 
The one, and 5 others just like it are only now running Windows Server 2003 and get shipped around the country every week for classes/labs we hold. That was running Edgy.
This decision was made to make it easier on the instructors - they are intimidated by anything without a point and click interface.
   - Never put Dell OMSA on this one...

* Yes we use VMware with multiple Dual CPU Guests.

* Curious, your errors are related to ata1, and every "error" with sd* in it seems to not be an error but a simple message - did I miss some change in which sata/sas disks are now referred to as ata1.
Are you sure you don't have a failing disk? Windows isn't as verbose about failing disks as Linux/BSD is in my experience.

I don't mean to be picking at this, I'm just curious - maybe I'm ignorant to the problem and will be bitten by this just as you have been? ;)

Our systems don't sound all that different. But if you are more comfortable with Windows thats not for me to judge ;)

Kind regards,
       -Jeff

---

### Post by jbaloul on 2007-06-01
Hey Jeff,
first off, this debate is good...that is what it is all about, so feel free & comfortable...

The "No kernel can handle it" was more regarding the SMP and VMware..here take a look at some links:
From:
[http://www.vmware.com/support/server/doc/releasenotes_server.html](http://www.vmware.com/support/server/doc/releasenotes_server.html)
"...
Experimental support for 64-bit Ubuntu 6.x as host and guest operating systems. 
..."
"...
Experimental support for two-way Virtual Symmetric Multiprocessing (Virtual SMP). 
..."

Just so you see i am not the only one ;-) :
[http://www.vmware.com/community/search.jspa?forumID=219&threadID=&q=cpu+dual+100%25&objID=f219&dateRange=all&userID=&numResults=15&rankBy=10001](http://www.vmware.com/community/search.jspa?forumID=219&threadID=&q=cpu+dual+100%25&objID=f219&dateRange=all&userID=&numResults=15&rankBy=10001)

Regarding the kernel and card itself...
It makes a huge difference in our systems...
I found out (the hard way) that it is not only the card type which needs to be supported by the distro's kernel, but it is also the Disk type and firmware of the card or onboard chipset for the SATA controller....for example the Promise card we bought did not support the 750gb seagate drive, only 500's...where adaptec cards did.

The disk error referred to ata1 is the sd disk, as mentioned in the  previous kernel bug link in my original post. The system even locks up in certain cases as i mentioned.

Working with the Dell+Ubuntu+Vmware(one CPU guests)+SAS is working great...at one point i had about 20 VM's running on the system...its just the deadly mix of the eSata 750GB disk with the Dual CPU guests which killed the show.

I am equally comfortable in both worlds, *nix & Windows...I just heavily prefer ( in this case a VMWare Server)  a headless linux box, and that is for many obvious reasons.


Peace & Health,
Jacob

---

### Post by uforic on 2007-07-17
Hello all, I like some advice and suggestions on a complete move over to Ubuntu.

Here are the specs to my companies' Dell servers:
Dell PowerEdge 1850
2 x Intel Xeon 3.0GHz (EM64T)
2 x 1GB DDR2 400 SDRAM, ECC, registered
Integrated Single channel LSI53C1030 Ultra320 SCSI controller with 2 x 36GB 15k rpm Ultra320 SCSI Drives
Embedded ATI Radeon 7000-M with 16MB SDRAM video controller
Dual embedded Intel 82541EI Gigabit Ethernet NIC with PXE and WOL

In the process of ordering this for the 1850:
Optional embedded single channel Ultra320 SCSI integrated PERC 4e/Si with 256MB of battery-backed cache

Dell PowerEdge 2950
2 x Intel Dual Core Xeon 2.0GHz (5130-EM64T)
2 x 2GB DDR2 533 SDRAM, ECC, registered
Integrated PERC 5/i SAS 3.0 Gb/s RAID controller with 256MB of battery-backup cache with 4 x 73GB 15k rpm SAS Drives
Embedded ATI Radeon ES1000 with 16MB memory video controller
Dual embedded Broadcom NetXtreme IITM  5708 Gigabit Ethernet NIC with fail-over and load balancing.

Systems and platforms in these servers are as follows:
Dell 1850
-Apache
-php
-vsftp
-wordpress 2.2.1
-phpbb 2.0.22
-phpchat
-java irc
and looking at an opensource video and audio stream platform. Most probably with red5

Dell 2950
-Apache
-Mysql
-php
-vsftp
-postfix (for transport purposes only, low traffic)

What we have now are on windows 2003 server, obviously its become a headache for us and most importantly its become very unstable over the last year and half. Our setup is for a high traffic website with its focus on the phpbb forum and wordpress blog, all content of these 2 platforms are stored in mysql. And inside these 2 platforms, we provide live chat, java irc type chat and will start to provide streaming audio and video as well, also having these content stored in mysql. The postfix mail transport is mostly used in registration and newsletters to our members, therefore not a high traffic mail server.

Presently we are on only one PE1850 with all the services described minus the streaming part. So as you can see, its really taxing the server alot, so after researching and reading all the Dell server related post in Ubuntu forum, we decided to start preparing for a complete migration.

Here is our planning:
PE1850 - we will do a raid 0 on the present drives with a new PERC 4e/Si controller add-on. This will not only increase our drive space but also improve on the disk I/O. Its secondary gigabit ethernet port is use for database connection. 
PE2950 - We will do a raid 1+0 or raid 5 (but after doing all the research, for performance but with space sacrifices, we are leaning towards raid 1+0 but would like any advice from you guys, thanx)  this server main purpose is for Mysql and mail services. It will connect with our front end services like web, phpbb and wordpress via its secondary gigabit ethernet port. 

We are no experts by all means nor we are linux experience users, so any suggestions or advice to the above setup is much appreciated.

Here are my questions:
1. We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly, so I believe choosing Feisty Fawn 7.04 server edition is the best way to go, is this a correct move?

2. After reading all the posts in this forum, we have alot of worries regarding Dell's PERC raid controllers and Ubuntu driver supports. Since we need to do raid setup in both servers, are all these drivers ready out of the box, and getting everything to work like the we planned is going to work or we will face alot of issues?

3. I know the following are a bunch of old debates but my company is in China, 1. our techs/programmers are windows people, so gui environment is a must; 2. this is a world of kiddy hackers and virus infested environment, therefore all extra layer of protection and security are necessary. 3. our co-lo is quite a ways from our office, therefore a or a few remote management software are needed.
So here go my questions:
     1.	We will need a gui remote access, so we are going to install gnome in our servers and
         by using ssh and NoMachine’s NX servers, are there any security involved? There will be
         also all webmin that needs to be install as well, see any security issues in these?

     2.	Since we have all these remote access in the server, a firewall is a must; we looked at
         ubuntu-firewall and firestarter, which is better for our needs? Or are there any better
         ones?

     3.	I know this is much debated subject, is anti-virus needed in our setup? Our mail server is
         mostly outgoing mails, and very little incoming (at least we will ignore most of them) and
         we will not use pop, its all system emails.

4. We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us? 

We really appreciate all advice and suggestion, and please excuse any dumb questions (as we are not familiar with linux) from here on, thank you in advance.

---

### Post by gregorybe on 2007-09-08
The last two days I have trying to firgure out installing ubuntu desktop on a Poweredge 2950,
First I tried installing ubuntu-6.06.1-desktop-amd64  but the install cd just doesn&#8217;t boot into the environment.

My harddrive config:
3x 74GB SAS in RAID5
2x 250GB SATA in raid1
1x 250GB no raid

Then, I started the ubuntu-6.06.1-desktop-i386 install cd, I ran the installer, after the installation finished I mounted the logical SATA RAID  drive in /home/ubuntu/test/
What I did after that:
```
su
chroot /home/ubuntu/test/
grub-install /dev/sdh (because if I opened Disks, the DELL PERC RAID5 drive was assigned sdh)
ERROR: &#8216;Not found or not a block device&#8217;

```
Because of this error I tried doing the same in a new terminal window without chroot, then the error is: 
Unknown partition table signature
Could not find device fot /boot: Not found or not a block device
I also tried the rest:
```

# fix initrd
echo megaraid_sas >> /etc/mkinitramfs/modules
cp /boot/initrd.img-2.6.15-26-386  /boot/initrd.img-2.6.15-26-386.old
mkinitramfs -o /boot/initrd.img-2.6.15-26-386 2.6.15-26-386

# install grub
grub-install /dev/sdh 

# change (hd2,0) to (hd0,0) in menu.lst
grep hd7 /boot/grub/menu.lst
cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
sed -e 's/hd7/hd0/g' /boot/grub/menu.lst.orig > /boot/grub/menu.lst

```
But still get the error: 
Grub Loading stage 1.5.
Error 21

Error 21 means :
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.

Does Anyone has  a solution? 
Thank you
PS: I use the desktop version because it works easier for me

**[COLOR="Red"]PROBLEM SOLVED, I will post the solution tomorrow...[/COLOR]**

---

### Post by tr011 on 2007-09-18
> **Grizzly_Adams said:**
> 
Issue #4:  Related to issue #1 - no network when system loads.  Resolution:  None at this stage.  I followed the advice of another person and tried loading the driver manually but to no effect (ie. modprobe bnx2).  The output of a lspci is as follows:

# lspci | grep -i broad
 PCI bridge: Broadcom: Unknown device 0103 (rev c2)
 Ethernet Controller:  Broadcom Corporation:  Unknown device 164c (rev 11).


Hi every one!, any one can help me with the nework configuration? I'm working with a dell 2950  and i allready loaded the bnx2 drivers and my /etc/network/interfaces after i added the "eth0" and "eth1" looks like this:

##############################
auto lo eth0 eth1
iface lo inet loopback
##############################
What i'm doing worng? becouse i still got the message:

PCI bridge: Broadcom: Unknown device 0103 (rev c2)
Ethernet Controller: Broadcom Corporation: Unknown device 164c (rev 11).

I have all ready done This: [http://ubuntuforums.org/showthread.php?t=217566&highlight=dell+2950+network](http://ubuntuforums.org/showthread.php?t=217566&highlight=dell+2950+network)

But i still can't recognize the network cards :(

Thanks!

---

### Post by Alfomio on 2007-10-31
Hi guys,

thanks for the summary of really helpful infos. =D>
I´ve successfully installed 6.06.1 64 bit on a PE 1950 in a really short time without having big problems.

My config of the PE 1950:

one quad core 2.33 GHz
4 GB RAM
2 * 250 GB SATA II  in RAID 1 (PERC)

> **badmojo said:**
> **This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57265) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I followed someones post here, sorry I forget who... how to work around this problem with 1950/2950 perc5 raid and managed to get the system up and running (successfully now for 5 months) using 6.06.1 server x86. 
It's our production email server. So thank you whoever it was.

Now I have recently read that the bug related to the physical disks has been resolved with linux-image 2.6.15-28 from security updates.

Any advice on how to go about getting this working so that I do not see sda, b, c, d, and sde (logical drive).
I would feel much better if I simply have sda (logical) showing up and not all of the physical disks.

I installed the kernel image using apt and rebooted, no luck, it simply hangs during startup.
Had to go back to previous kernel (2.6.15-26).
I am assuming I am missing something but unsure what.

Has anyone done this successfully :confused:

I´ve update the kernel 2.6.15-29 and the machine runs perfect. Before you reboot the machine after the update you should change some entries in /boot/grub/menu.lst and /etc/fstab,
because the system only knows sda, no sdb, c, d and so on.

menu.lst:
....
title           Ubuntu, kernel 2.6.15-29-amd64-server
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-amd64-server root=/dev/[COLOR="Red"]sda[/COLOR]1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-amd64-server
savedefault
boot

title           Ubuntu, kernel 2.6.15-29-amd64-server (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-amd64-server root=/dev/[COLOR="Red"]sda[/COLOR]1 ro single
initrd          /boot/initrd.img-2.6.15-29-amd64-server
boot
...

fstab:
change all sdc to sda


I´ve tested with booting on both disk, only disk 0 and only disk 1. No errors.

Good luck!

---

### Post by tech4him on 2008-01-04
Thanks for all the information here. We have [posted our experience]("http://www.tech4him.com/node/9") with 6.06.1 LTS on a new 2950 on our site ([http://www.tech4him.com/node/9]("http://www.tech4him.com/node/9")). Before anyone says anything, yes we are running the standard 32bit kernel not 64bit...still testing the 64bit o/s.

We are using this server as a VMware host. We tested the setup by adding two Ubuntu LAMP servers and a Windows 2003 Server with SQL Server 2005 and Reporting services as VM's on this host. We then got some testing scripts executing from various clients placing loads on all three VM's. While the servers were being tested we pulled drive a drive from the array with no problems. We reinserted the drive later and watched the controller handle rebuilding the drive. 

It worked like a charm. Next we will be testing pulling drive 0 from the array and rebooting to ensure grub is correctly handled throughout the array.

Now we are just trying to track down a weird networking issue with the server. :confused:

Hope this helps.

---

### Post by Scootin159 on 2008-01-04
> **tech4him said:**
> Now we are just trying to track down a weird networking issue with the server. :confused:

I'm not sure if you already noticed this, but in our install (similar to yours, but we are using CentOS for the host OS), we found that Eth0 and Eth1 were actually switched in reference to the ports on the back.  Sounds silly, but took us a while to figure it out.

---

### Post by tech4him on 2008-01-08
Thanks for mentioning the ETH0/1 switch. Yeah, I found this out after 3 days of fighting intermittent network outages of only a few seconds each, but annoying. Had duplicated the IP on both NICs with the onboard remote access. Duh! Thought they were both on the same NIC but actually the Ubuntu install saw them opposite of what they are labeled. Remove the other NIC's connection and IP and problem went away. 

Funny enough, when trying to diagnose to see if a duplicate IP was the problem, I only got one ARP response and not two like I had anticipated. Pretty wild, but fixed now. 

So again, thanks for brining it up!

---

### Post by hotani on 2008-01-15
WOW! Why don't I just stab myself in the eye with a fork?!

I installed CentOS 4.6 (64 bit) earlier this week on the same 1950 server with RAID1 and it went off without a hitch. Now with Ubuntu 6.06.1 (64 bit) there is a whole frikking LIST of problems (display, network, unrecognized RAID, failure to boot, etc, etc..). I'm still staring at a GRUB Error 21, and have tried several of the fixes posted in this thread. 

We needed CentOS for a certain finicky app server (cold fusion - blech.), but after comparing the experiences, we're most likely going to throw out the idea of using Ubuntu for **all 6 webservers** and go with CentOS 5 which actually **supports the hardware**. gah.

---

### Post by tech4him on 2008-01-16
hotani,

Keep in mind that I believe Ubuntu Server 6.10 and above support the hardware. It's just that many of us in an enterprise environment are trying to stick with 6.06 LTS because of the long-term support rather than upgrading every six months. (or atleast that's why we stuck with 6.06).

I believe the next LTS version will be 8.04 which should come out in April if I am not mistaken. I'm going to bet these issues with the 2950 hardware will be resolved since it will be on the newer kernel.

Just my 1/2 cent thoughts.  :)

---

### Post by hotani on 2008-01-16
Yes - LTS is exactly the reason we were attempting to use 6.06 and not the latest and greatest. Unfortunately we need these servers built now, not in April so waiting for the next LTS release is not an option.

Today I loaded CentOS 5 on the 1950 and it worked great. Plus it is supported till 2014!

---

### Post by tech4him on 2008-01-17
hotani,

Haha....well certainly can't blame you for that. I have discussed going the same direction here over the past two months, however the desire is to plow forward with Ubuntu for a number of reasons. Thus why all the notes on how we got it working. 

Hopefully Canonical and the Ubuntu community see the business / enterprise side of this otherwise we may see slow adoption for enterprise servers and limit Ubuntu to just a desktop distro. That would be a shame.

Anyhow, glad to hear you got it working on another platform. It can be done on Ubuntu 6.06.1 but it certainly is not for the weak at heart. 

BTW, I got some kernel updates the other day and it rewrote my menu.lst for grub. Hung on boot and had to reconfigure the menu.lst file again. Ugh!

---

### Post by densone on 2008-02-19
Hi, I am wondering if it is possible for this issue to occur with later version of Ubuntu. I believe that I am seeing something similar with Gutsy. Any advice would be great. 

sc

---

### Post by lodbot on 2008-03-10
> **reech said:**
> For those that would like to monitor their machines/perc arrays  I managed to get omsa installed on my 2950/dapper 6.06.1  like so: 

install openipmi and ipmitool:
```
sudo apt-get install openipmi 
sudo apt-get install ipmitool
```

install lib32ncurses and ia32-libs:
```
sudo apt-get install -f lib32ncurses5
sudo apt-get install -f ia32-libs
```

grab omsa:
```
wget ftp://ftp.sara.nl/pub/outgoing/dell/binary-amd64/dellomsa_5.1.0-5_amd64.deb
```

install omsa:
```
dpkg -i dellomsa_5.1.0-5_amd64.deb
```

For starters:```
sudo omreport storage controller
```

the CLI userguide is here (seems a little removed from reality):
[http://support.dell.com/support/edocs/software/svradmin/5.1/en/cli/html/index.htm](http://support.dell.com/support/edocs/software/svradmin/5.1/en/cli/html/index.htm)

disclaimer - : have forced some packages here - follow these instructions at your own risk.reech, what could go wrong with this?  I'm running 6.06 on a 1950, and the box is currently in colo.  I want to understand the risks of setting up monitoring before making any changes to a production box.  I don't know enough about this sort of thing to make the decision myself, and I can't really find any other information.  What are your thoughts?  Thanks!

EDIT: probably important to note that I'm running dual Intel Xeons.

---

### Post by lodbot on 2008-03-16
> **lodbot said:**
> reech, what could go wrong with this?  I'm running 6.06 on a 1950, and the box is currently in colo.  I want to understand the risks of setting up monitoring before making any changes to a production box.  I don't know enough about this sort of thing to make the decision myself, and I can't really find any other information.  What are your thoughts?  Thanks!

EDIT: probably important to note that I'm running dual Intel Xeons.Update: I followed those exact steps and it's working.  I find the following command to be more useful when monitoring the array:
```
sudo omreport storage controller controller=0
```

Thanks for the guide, reech!

---

### Post by jbaxley14 on 2008-04-09
hey i have been trying to partition up a perc 5/i array in RAID 5 and create a virtual disk up to 8 TB, i can create the partition, but when i try to send information to it, i sometimes (sometimes) get input/output errors.  but only with users that aren't root.

if i try and restart the server, the booting fails stating that the filesystem couldn't read the super blocks.  

the array is on a Dell MD1000.

any help you could give would be great!

---

### Post by AllanM on 2008-07-08
Can confirm that Ubuntu Hardy 8.04.1 LTS server 64-bit installs fine on Dell PowerEdge 2950 III.

Just installed on two identical systems with dual cpu, 16Gb, and perc/6i controller configured to raid 5 with 3x450Gb SAS drives.

Broadcom Gb2 port mapped to eth0 during install as others have found so would advise to use that one if you only need one connection. I was expecting some issues with Broadcom drivers but they worked first time.

:):):)

---

