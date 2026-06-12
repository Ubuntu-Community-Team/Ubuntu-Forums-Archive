---
title: "USB Stick doesn't react"
date: 2016-06-19
forum: Hardware
---

### Post by superdude2 on 2016-06-19
Hello,
I'm writing this thread because i haven't found any solution yet. The problem is that after formatting my USB stick 2 days ago(`sudo mkfs.ntfs /dev/sdb1`) from FAT to NTFS to get rid of 4 GB file limit it doesn't react with OS (Xubuntu 14.04). It's a 32 GB USB stick from Toshiba. Everything seemed to be okay until the reboot. Since then i can't access it. I tried various things but still the same.On windows 10 however i can see F drive but can't access it either.  


Output of some commands:


  lsusb 
```
Bus 001 Device 011: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:000a A4Tech Co., Ltd. Optical Mouse Opto 510D / OP-620D
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``` 

dmesg | tail -n10
```
[11631.572258] [UFW AUDIT] IN=eth0 OUT= MAC=00:25:22:8c:c7:a0:08:10:78:23:75:aa:08:00 SRC=151.101.1.69 DST=192.168.1.3 LEN=1496 TOS=0x08 PREC=0x00 TTL=47 ID=20787 DF PROTO=TCP SPT=443 DPT=48938 WINDOW=300 RES=0x00 ACK URGP=0 
[11631.572303] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.3 DST=151.101.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55410 DF PROTO=TCP SPT=48938 DPT=443 WINDOW=1444 RES=0x00 ACK URGP=0 
[11631.572480] [UFW AUDIT] IN=eth0 OUT= MAC=00:25:22:8c:c7:a0:08:10:78:23:75:aa:08:00 SRC=151.101.1.69 DST=192.168.1.3 LEN=1396 TOS=0x08 PREC=0x00 TTL=47 ID=20788 DF PROTO=TCP SPT=443 DPT=48938 WINDOW=300 RES=0x00 ACK PSH URGP=0 
[11631.572499] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.3 DST=151.101.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55411 DF PROTO=TCP SPT=48938 DPT=443 WINDOW=1444 RES=0x00 ACK URGP=0 
[11631.572719] [UFW AUDIT] IN=eth0 OUT= MAC=00:25:22:8c:c7:a0:08:10:78:23:75:aa:08:00 SRC=151.101.1.69 DST=192.168.1.3 LEN=1496 TOS=0x08 PREC=0x00 TTL=47 ID=20789 DF PROTO=TCP SPT=443 DPT=48938 WINDOW=300 RES=0x00 ACK URGP=0 
[11631.572737] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.3 DST=151.101.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55412 DF PROTO=TCP SPT=48938 DPT=443 WINDOW=1444 RES=0x00 ACK URGP=0 
[11631.573826] [UFW AUDIT] IN=eth0 OUT= MAC=00:25:22:8c:c7:a0:08:10:78:23:75:aa:08:00 SRC=151.101.1.69 DST=192.168.1.3 LEN=1286 TOS=0x08 PREC=0x00 TTL=47 ID=20790 DF PROTO=TCP SPT=443 DPT=48938 WINDOW=300 RES=0x00 ACK PSH URGP=0 
[11631.573851] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.3 DST=151.101.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55413 DF PROTO=TCP SPT=48938 DPT=443 WINDOW=1444 RES=0x00 ACK URGP=0 
[11631.765579] [UFW AUDIT] IN=eth0 OUT= MAC=00:25:22:8c:c7:a0:08:10:78:23:75:aa:08:00 SRC=151.101.1.69 DST=192.168.1.3 LEN=564 TOS=0x08 PREC=0x00 TTL=47 ID=2825 DF PROTO=TCP SPT=443 DPT=48937 WINDOW=237 RES=0x00 ACK PSH URGP=0 
[11631.765610] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.3 DST=151.101.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=5726 DF PROTO=TCP SPT=48937 DPT=443 WINDOW=1444 RES=0x00 ACK URGP=0 
```


    cat /etc/mtab 
```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
selinuxfs /sys/fs/selinux selinuxfs rw,relatime 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
/dev/sda7 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
/home/boss/.Private /home/boss ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=19ba0418664290d3,ecryptfs_fnek_sig=5cd3a2573947e2d1 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=boss 0 0

```



    ls /dev/ | grep sd  
```
sda
sda1
sda2
sda3
sda4
sda5
sda6
sda7
sdb
```

    tail -f /var/log/messages  
```
tail: cannot open &#8216;/var/log/messages&#8217; for reading: No such file or directory
```


    lsmod | grep usb  

```
usb_storage 62209 0 
usbhid 52659 0 
hid 106148 3 hid_a4tech,hid_generic,usbhid
```

    df -h  
```
Filesystem Size Used Avail Use% Mounted on
udev 2.0G 12K 2.0G 1% /dev
tmpfs 396M 1.3M 394M 1% /run
/dev/sda5 28G 20G 6.5G 76% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
none 5.0M 0 5.0M 0% /run/lock
none 2.0G 62M 1.9G 4% /run/shm
none 100M 36K 100M 1% /run/user
overflow 1.0M 16K 1008K 2% /tmp
/dev/sda7 613G 185G 397G 32% /home
/home/boss/.Private 613G 185G 397G 32% /home/boss
```
    sudo fdisk -l  

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
135 heads, 14 sectors/track, 1033611 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf7bd90fe


Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 206848 585222747 292507950 7 HPFS/NTFS/exFAT
/dev/sda3 585224192 586143743 459776 27 Hidden NTFS WinRE
/dev/sda4 586145790 1953523711 683688961 5 Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5 586145792 644739071 29296640 83 Linux
/dev/sda6 644741120 648644607 1951744 82 Linux swap / Solaris
/dev/sda7 648646656 1953523711 652438528 83 Linux

```

    lsblk  
```
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 931.5G 0 disk 
&#9500;&#9472;sda1 8:1 0 100M 0 part 
&#9500;&#9472;sda2 8:2 0 279G 0 part 
&#9500;&#9472;sda3 8:3 0 449M 0 part 
&#9500;&#9472;sda4 8:4 0 1K 0 part 
&#9500;&#9472;sda5 8:5 0 28G 0 part /
&#9500;&#9472;sda6 8:6 0 1.9G 0 part 
&#9492;&#9472;sda7 8:7 0 622.2G 0 part /home
sr0 11:0 1 1024M 0 rom 

```



I'm sorry for that spam but i couldn't find spoiler option so it's the best i could afford.It's weird that fdisk, df and even gparted can't see it. I need some help from you ASAP. It's quite tough problem for me.

PS:I searched for the same topics but if there's a same thread with working solution just tell me and i will delete it immediately.


I look forward to hearing from you, 


SuperDude

---

### Post by vasa1 on 2016-06-19
Please consider using code tags rather than html tags when posting output from the terminal. It looks better that way. Thanks!

---

### Post by superdude2 on 2016-06-19
Ok, Thank You. I just wanted to make less space in my post . I'll keep that in my mind.

Still looking for help with my problem,
superdude

---

### Post by sudodus on 2016-06-19
Try to format the pendrive with mkusb according to these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Wipe menu](https://help.ubuntu.com/community/mkusb/wipe)

The second option in the wipe menu should help you create what you want:

**b "Big drive: create GUID partition table with NTFS partition"**

---

### Post by superdude2 on 2016-06-19
Hello,
thanks for reply. I got that mkusb but i don't know if it's safe(details in attachment). It looks like it will wipe my hdd instead of usb stick. Can i change target in next window?

---

### Post by sudodus on 2016-06-19
mkusb does not see your pendrive (it can see only your internal drive). Something is very wrong, when it does not see your pendrive (as a mass storage device).

You mentioned that you can see it in Windows. Is that in the same computer, when you have rebooted it into Windows, or is it in another computer?

Maybe rebooting into Xubuntu will make things work.

Have you tried with all the USB ports of the computer (and if possible all USB ports of other computers too)? With some luck, you can find a place where it works.

In order for tools like mkusb and gparted to work, the computer must see the drive as /dev/sdx, where x is the drive letter, for example b, so for example /dev/sdb.

-o-

If you have bad luck, your drive is damaged. See this link about pendrive lifetime.

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by superdude2 on 2016-06-19
I have only one PC right now with dual boot(Win/Linux). I meant that on Windows boot i can see usb disk but cant access it. I have tried all usb ports but it's the same. I have another usb stick but it works fine on Win and Linux.
> [COLOR=#000000]Maybe rebooting into Xubuntu will make things work.[/COLOR] What do you mean by that? I'm on Linux almost all the time. I have Win only for programs that aren't on Ubuntu yet.

---

### Post by steeldriver on 2016-06-19
AFAIK it's syslog not dmesg that logs udev trigger events; try

```

tail -Fn0 /var/log/syslog

```

and then plugging in the device - post back what you see

---

### Post by sudodus on 2016-06-19
> **superdude2 said:**
> > Maybe rebooting into Xubuntu will make things work.
What do you mean by that? I'm on Linux almost all the time. I have Win only for programs that aren't on Ubuntu yet.

Sorry that I did not express clearly what I meant. Sometimes a re-partitioned or re-formatted USB pendrive needs a reboot to work correctly. So I was simply suggesting to reboot (into Xubuntu).

---

### Post by yancek on 2016-06-19
You can see it on Xubuntu but can see it, meaning the drive/partition on windows.  So what happens when you try to access it and what are you trying to access?  Is there anything on it?  If you're creating and ntfs filesystem and have windows available, why not do it in windows?  Should work in Xubuntu  but it is a windows proprietary filesystem.  In addition to the suggestions above, you could try creating a partition before formatting.  The output you posted above shows different partitions on sda but only the sdb drive.

---

### Post by superdude2 on 2016-06-20
I cannot see it on Xubuntu. That's the problem. On windows i can only see F drive but when i click on it it says that i should connect device because it's ejected. I want to open this drive with file manager. It's empty.about that ntfs on windows, you're right. I totally forgot that i can do it there since i spend a lot of time on Linux. 
> [COLOR=#000000]The output you posted above shows different partitions on sda but only the sdb drive.[/COLOR] 
The thing is that i can only see /dev/sda/(my 1 TB hdd), nothing else.Back then i could see /dev/sdb1 but not anymore. If any other output needed just tell me which.
> [COLOR=#000000] In addition to the suggestions above, you could try creating a partition before formatting. [/COLOR]
Do you mean now or before? If now then please help me because i don't know how to do it on 'invisible' partition.

---

### Post by X-RED_Tech on 2016-06-21
Have you checked in the disk/drive management utility (in Windows)?
If the drive is there then the right-click menu should have all the required options to delete the partition, create and format a new one.
If not then you should seriously consider the possibility of a failing or already failed drive. In that case software cannot help.

---

### Post by superdude2 on 2016-06-22
Hello,
Sorry for my absense but i was quite busy.


> **steeldriver said:**
> AFAIK it's syslog not dmesg that logs udev trigger events; try

```

tail -Fn0 /var/log/syslog

```

and then plugging in the device - post back what you see

Output ```
TOS=0x00 PREC=0x00 TTL=56 ID=46523 PROTO=TCP SPT=443 DPT=52667 WINDOW=277 RES=0x00 ACK URGP=0 
Jun 22 16:39:19 m-desktop kernel: [18550.320022] usb 1-6: new high-speed USB device number 4 using ehci-pci
Jun 22 16:39:19 m-desktop kernel: [18550.453249] usb 1-6: New USB device found, idVendor=0c76, idProduct=0005
Jun 22 16:39:19 m-desktop kernel: [18550.453256] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 22 16:39:19 m-desktop kernel: [18550.453261] usb 1-6: Product: USB Mass Storage
Jun 22 16:39:19 m-desktop kernel: [18550.453265] usb 1-6: Manufacturer: GENERIC 
Jun 22 16:39:19 m-desktop kernel: [18550.453702] usb-storage 1-6:1.0: USB Mass Storage device detected
Jun 22 16:39:19 m-desktop kernel: [18550.453799] scsi5 : usb-storage 1-6:1.0
Jun 22 16:39:19 m-desktop mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6"
Jun 22 16:39:19 m-desktop mtp-probe: bus: 1, device: 4 was not an MTP device
Jun 22 16:39:20 m-desktop kernel: [18552.105076] scsi 5:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 0 CCS
Jun 22 16:39:20 m-desktop kernel: [18552.106905] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jun 22 16:39:21 m-desktop kernel: [18552.111454] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```
Thanks and sorry for not seeing your post. As i can see something is going on. It can see scsi and sdb device if i'm not mistaken. But what to do now ? Can i link it to the mounting point somehow?

> **X-RED_Tech said:**
> Have you checked in the disk/drive management utility (in Windows)?
If the drive is there then the right-click menu should have all the required options to delete the partition, create and format a new one.
If not then you should seriously consider the possibility of a failing or already failed drive. In that case software cannot help.
Yes i have but it windows can't see it either. Only my hdd is seen . Yea i'm slowly preparing to worst case.

---

### Post by X-RED_Tech on 2016-06-22
Are you absolutely sure it doesn't show up in the **[COLOR=#000000]*disk/drive management utility*[/COLOR]** ?
Unformatted or not properly formatted drives won't appear in the file manager but should appear in the said utility with their partitions as 'raw', unknown or whatever is the terminology Windows is using this days.

---

### Post by superdude2 on 2016-06-22
Yes i am. Only thing i can see there is this usb drive(F) as an empty partition. All i can do is change letter and location. When i do it(assign it to a new folder) it says that drive is empty.

---

### Post by westie457 on 2016-06-22
Is the USB stick empty? Or has unimportant files on it?

Have you tried in Windows Admin Command Prompt a 'chkdsk' with no repair options just to check if there are any errors? This action may be enough to get the stick working.

---

### Post by superdude2 on 2016-06-22
It is empty and can't be accessed. Well i haven't yet. I will try then and let you know guys.

---

### Post by X-RED_Tech on 2016-06-22
> **superdude2 said:**
> Yes i am. Only thing i can see there is this usb drive(F) as an empty partition. All i can do is change letter and location. When i do it(assign it to a new folder) it says that drive is empty.

So you see it after all... Don't you have this options in the right-click menu? -> [http://www.plesis.com/wp-content/uploads/2013/12/efi3.png](http://www.plesis.com/wp-content/uploads/2013/12/efi3.png)


PS - chkdsk is also a very good idea and I would have suggested it before but you kept insisting it didn't show up in Windows either.

---

### Post by superdude2 on 2016-06-22
Well i tried chkdsk. Output from chkdsk f: /F and and f: /R  :
```
Cannot open volume for direct access
```
I've also tried all variations of drives and options but works only for raw c: .

> **X-RED_Tech said:**
> So you see it after all... Don't you have this options in the right-click menu? -> [http://www.plesis.com/wp-content/uploads/2013/12/efi3.png](http://www.plesis.com/wp-content/uploads/2013/12/efi3.png)

PS - chkdsk is also a very good idea and I would have suggested it before but you kept insisting it didn't show up in Windows either.


> **superdude2 said:**
> I have only one PC right now with dual boot(Win/Linux). I meant that on **Windows boot i can see usb disk but cant access it.** I have tried all usb ports but it's the same. I have another usb stick but it works fine on Win and Linux.
What do you mean by that? I'm on Linux almost all the time. I have Win only for programs that aren't on Ubuntu yet.

Sorry i got confused and made a mistake. And no i don't have it. All opitons are locked except change letter/path and help.

edit: I could make a snapshot but since my win10 is upgraded i can't change my native language unless i do it on win 7 and then reupgrade.

---

### Post by X-RED_Tech on 2016-06-22
It's probably defective so, again, there's nothing you can do from either OS.

You should be able to download additional languages in the Windows Update but that is besides the point. Windows was mentioned/recommended here as an additional "diagnostics tool" only. Otherwise I don't support Windows and this forum likewise.
There's no need for a screenshoot. "[COLOR=#000000]All opitons are locked except change letter/path and help" should be enough to conclude you need to find yourself another USB stick.

That said, I defer to the experts that commented here already hopping they suggest something else.[/COLOR]

---

### Post by superdude2 on 2016-06-22
Yea, probably you're right. I was thinking the same but it's strange that there's some sign that show 'some' reaction for connecting. Still, it won't help anyway now.

---

### Post by westie457 on 2016-06-22
In my limited experience before condemning the stick it might be a good idea to give TestDisk a try.

TestDisk runs under Linux and Windows also it is in the repos. to install ```
sudo apt-get install testdisk
``` to run ```
sudo testdisk
```

See [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) for more details and instructions

---

### Post by X-RED_Tech on 2016-06-22
> **westie457 said:**
> In my limited experience before condemning the stick it might be a good idea to give TestDisk a try.

The thing is it had been tried before if you care to read the whole thread. It doesn't show up as a drive in Ubuntu so no software can access it.
It is seen in Windows but the Windows tools don't work either. Could a third party software recover the contents? Maybe (I really doubt it) but that's not the point because there's nothing to salvage there - the user was trying to format it when it failed -, but even if it was and the said software somehow managed to recover something, that alone wouldn't make the drive work again.

---

### Post by superdude2 on 2016-06-22
> **westie457 said:**
> In my limited experience before condemning the stick it might be a good idea to give TestDisk a try.

TestDisk runs under Linux and Windows also it is in the repos. to install ```
sudo apt-get install testdisk
``` to run ```
sudo testdisk
```

See [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) for more details and instructions

Thank you for last pieces of hope but i'm afraid that **X-RED_Tech **is right. Unfortunately testdisk can't detect it either... 
I'm starting to look for some new storage device. May i ask you what external hdd do you recommend for the lowest price? 500 GB should be enough.

edit: Sorry if this question was wrong. I think this topic can be closed.

---

