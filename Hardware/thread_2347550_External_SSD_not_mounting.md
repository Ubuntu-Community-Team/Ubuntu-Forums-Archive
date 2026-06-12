---
title: "External SSD not mounting"
date: 2016-12-26
forum: Hardware
---

### Post by jackwhitaker3 on 2016-12-26
I have a sony 256GB SSD USB drive that I've formatted as FAT on Mac OS. Works fine on the mac but I'm unable to mount it on Ubuntu. It doesn't show up in gparted. Any ideas?

---

### Post by DuckHook on 2016-12-26
Please provide background and context.

[LIST=1]
[*]Are you dual booting a Mac and it shows on one OS and not the other, or
[*]using SSD on a separate and different machine?
[*]What HW are you using ('puter & SSD specs)?
[*]Is the port USB 2 or 3?
[*]If USB 3, is cable rated for USB 3?
[*]Have you tried a different port?
[*]Are you connecting through a hub? If so, try connecting directly.
[/LIST]
It's good to provide as much detail as possible when seeking help. ;)

With SSD hooked up, from Ubuntu pls post back output of the following:```
lsusb
``````
sudo blkid
``````
lsblk -aS
``````
sudo lshw -sanitize -C disk
```...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by jackwhitaker3 on 2016-12-27
> **DuckHook said:**
> Please provide background and context.

[LIST=1]
[*]Are you dual booting a Mac and it shows on one OS and not the other, or 
[*]using SSD on a separate and different machine? 
[*]What HW are you using ('puter & SSD specs)? 
[*]Is the port USB 2 or 3? 
[*]If USB 3, is cable rated for USB 3? 
[*]Have you tried a different port? 
[*]Are you connecting through a hub? If so, try connecting directly. 
[/LIST]
It's good to provide as much detail as possible when seeking help. ;)

With SSD hooked up, from Ubuntu pls post back output of the following:```
lsusb
``````
sudo blkid
``````
lsblk -aS
``````
sudo lshw -sanitize -C disk
```...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the *Adv Reply* toolbar.

Thanks for the reply!

I'm using two separate machines. Running Ubuntu 16.04 on a Dell Precision 3510 laptop.

The port, cable and device are all USB 3. I've tried all 3 USB 3 ports on the laptop. Not through a hub.

lsusb: ```
Bus 002 Device 002: ID 054c:087d Sony Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:5686 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0a5c:5832 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
sudo blkid
[sudo] password for jack: 
/dev/nvme0n1: PTUUID="19e49b9f-736c-4545-adae-a22ff15a95d9" PTTYPE="gpt"
/dev/nvme0n1p1: UUID="306B-5907" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="ecab417c-16f3-4db0-b1e8-1217129eb6d0"
/dev/nvme0n1p2: UUID="0104ba29-1a11-49d8-96d2-0a95da543366" TYPE="ext4" PARTUUID="29612cdf-1db3-4e5f-b5e5-77728064360b"
/dev/nvme0n1p3: UUID="65540a84-cdb2-45e9-adb8-c172a5f34e55" TYPE="swap" PARTUUID="71be7857-7218-42fc-8ddc-a50b1c024979"
```

```
lsblk -as
NAME      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0       7:0    0         0 loop 
loop1       7:1    0         0 loop 
loop2       7:2    0         0 loop 
loop3       7:3    0         0 loop 
loop4       7:4    0         0 loop 
loop5       7:5    0         0 loop 
loop6       7:6    0         0 loop 
loop7       7:7    0         0 loop 
nvme0n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1 259:0    0 238.5G  0 disk 
nvme0n1p2 259:2    0 230.1G  0 part /
&#9492;&#9472;nvme0n1 259:0    0 238.5G  0 disk 
nvme0n1p3 259:3    0   7.9G  0 part [SWAP]
&#9492;&#9472;nvme0n1 259:0    0 238.5G  0 disk
```

```
sudo lshw -sanitize -C disk
  *-disk UNCLAIMED        
       description: SCSI Disk
       product: PSZ-S
       vendor: Sony
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       version: 320:
       configuration: ansiversion=6
                    

``` - at first this command wouldn't finish running, but after I unplugged the drive and plugged it back in again a couple of times I got this.

Also the same kind of thing happens when I open gparted. Sometimes it will get stuck trying to scan for partitions, until I unplug the external drive.

---

### Post by efflandt on 2016-12-27
What partition type is the drive using? Although, not sure how you would determine that with gparted hanging and not sure how Mac partitions by default.

---

### Post by jackwhitaker3 on 2017-01-04
Using my macbook I've tried formatting the drive using Disk Utility with Apple Partition Map and GUID but neither works. I have an older external HDD that uses Apple Partition Map and that is working fine on the Linux machine.

---

### Post by jackwhitaker3 on 2017-01-04
Ok I've found someone had a similar problem ([link]("http://askubuntu.com/questions/638291/unable-to-mount-external-usb-ssd")) and they solved it by using a powered USB hub. So I'm gonna see if I can find one and try it out..

---

### Post by DuckHook on 2017-01-05
USB 3.0 ports are supposed to output 5V @ 900mA. Many, especially on laptops, do not. They start out in a "low power mode" and then put out more power only if the device "negotiates" for it. This is done to conserve battery power, which is a high priority in laptops. Since every laptop and every USB device are built differently, the number of permutations on how they interact with each other are pretty much endless.

This is why a powered hub might help. Because it draws its power independently of your laptop, it doesn't have this fancy power-miser technology built into it. It just provides max output from the get-go, and this may be enough to get the SSD initialized so that it can be recognized.

I've run into similar problems before with both USB SSDs and HDDs. A lot of these devices rely on every mA of power that a USB bus is "supposed" to deliver. But the laptop's power-miser technology screws them up because the initial output is not enough to initialize them, which consequently prevents even the power negotiation request.

Sometimes, having the device plugged in *prior* to turning on your laptop helps. With other devices/laptops, it's the other way around: the only way the laptop recognizes the drive is if it is plugged in *after* the laptop is up and running. You might be able to find a method that works for you by experimenting.

Also, try changing cables. I've discovered that some of my cables make bad connections to the power pin in the USB port and, once replaced, solved the problem. Since yours works with your Mac, this is unlikely to be the problem, but it's worth trying.

---

