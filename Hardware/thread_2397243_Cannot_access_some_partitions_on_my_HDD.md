---
title: "Cannot access some partitions on my HDD"
date: 2018-07-27
forum: Hardware
---

### Post by nihaljainn on 2018-07-27
Hi,

I own a Dell Inspiron 7570 notebook with 1TB HDD + 256GB SSD. It has Windows 10 installed on the SSD and I recently installed Ubuntu 16.04 LTS alongside Windows by allocating ~30GB to Ubuntu on a partition I created on the HDD.

The problem I am facing is that I am unable to access the other partitions of my HDD or any files from the SSD using Files (the default file manager on Ubuntu).

The output of sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL is

NAME   FSTYPE     SIZE MOUNTPOINT       LABEL
loop1  squashfs 192.1M /snap/eclipse/29 
sdb             238.5G                  
&#9500;&#9472;sdb4 swap       7.8G [SWAP]           
&#9500;&#9472;sdb2            128M                  
&#9500;&#9472;sdb7 ntfs       1.1G                  DELLSUPPORT
&#9500;&#9472;sdb5 ntfs       472M                  WINRETOOLS
&#9500;&#9472;sdb3          216.3G                  
&#9500;&#9472;sdb1 vfat       500M /boot/efi        ESP
&#9492;&#9472;sdb6 ntfs      12.3G                  Image
loop0  squashfs  86.9M /snap/core/4917  
sda             931.5G                  
&#9500;&#9472;sda4 ext4      28.1G /                
&#9500;&#9472;sda2          901.4G                  
&#9500;&#9472;sda3 swap       1.9G [SWAP]           
&#9492;&#9472;sda1            128M 

More specifically, I am interested in accessing sda2 whereas Files gives me access to only sda4.

I read elsewhere that quick start being activated on Windows could create this problem. I have deactivated quick start by going to the control panel on Windows and disabling it there.

I am new to Ubuntu, so please excuse me if this is a very trivial issue. Thanks :)

---

### Post by TheFu on 2018-07-27
It is a Windows problem.  Windows isn't closing the NTFS filesystems completely, so Ubuntu won't touch them.  There are 2 settings in Windows that need to be disabled. I don't remember them, but a google for "windows ntfs left open" should find answers.

Of course, if you enabled disk encryption under Windows, don't expect Ubuntu to gain access.

---

### Post by gpaunescu2 on 2018-07-27
> **nihaljainn said:**
> Hi,

I own a Dell Inspiron 7570 notebook with 1TB HDD + 256GB SSD. It has Windows 10 installed on the SSD and I recently installed Ubuntu 16.04 LTS alongside Windows by allocating ~30GB to Ubuntu on a partition I created on the HDD.

The problem I am facing is that I am unable to access the other partitions of my HDD or any files from the SSD using Files (the default file manager on Ubuntu).

The output of sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL is

NAME   FSTYPE     SIZE MOUNTPOINT       LABEL
loop1  squashfs 192.1M /snap/eclipse/29 
sdb             238.5G                  
&#9500;&#9472;sdb4 swap       7.8G [SWAP]           
&#9500;&#9472;sdb2            128M                  
&#9500;&#9472;sdb7 ntfs       1.1G                  DELLSUPPORT
&#9500;&#9472;sdb5 ntfs       472M                  WINRETOOLS
&#9500;&#9472;sdb3          216.3G                  
&#9500;&#9472;sdb1 vfat       500M /boot/efi        ESP
&#9492;&#9472;sdb6 ntfs      12.3G                  Image
loop0  squashfs  86.9M /snap/core/4917  
sda             931.5G                  
&#9500;&#9472;sda4 ext4      28.1G /                
&#9500;&#9472;sda2          901.4G                  
&#9500;&#9472;sda3 swap       1.9G [SWAP]           
&#9492;&#9472;sda1            128M 

More specifically, I am interested in accessing sda2 whereas Files gives me access to only sda4.

I read elsewhere that quick start being activated on Windows could create this problem. I have deactivated quick start by going to the control panel on Windows and disabling it there.

I am new to Ubuntu, so please excuse me if this is a very trivial issue. Thanks :)

You should disable hibernate in windows.

---

### Post by Autodave on 2018-07-27
In the BIOS, disable *fast boot.*

---

### Post by oldfred on 2018-07-27
Your list is not showing a format, neither NTFS nor ext4 for sda2.
If it is formatted, then it is the Windows fast start up/hibernation issue.
Note that Windows updates will turn fast start up back on. And Windows updates may occur in the back ground. So whenever issues mounting  a NTFS partition check if fast start up is on, or if chkdsk required.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

