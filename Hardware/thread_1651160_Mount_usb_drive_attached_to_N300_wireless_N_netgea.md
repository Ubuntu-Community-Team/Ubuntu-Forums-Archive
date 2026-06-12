---
title: "Mount usb drive attached to N300 wireless N netgear router"
date: 2010-12-22
forum: Hardware
---

### Post by Stephen Shellard on 2010-12-22
I can currently access my USB drive attached to the USB port of my router, and can copy files to and from it etc. On the router administration interface, the device name is given as "readyshare".  When accessing via Samba the pathway smb://readyshare/usb_storage/ appears in nautilus. 

However I can not save files directly to it from an application and assume that for this to work, I would have to mount the drive.  I have been attempting to do this via an entry in fstab:  here is one failed attempt:  

//192.168.0.1/readyshare/usb_storage	   /media/readyshare  vfat    defaults        0       2

On running sudo mount -a the following error is returned:  mount: special device //192.168.0.1/readyshare/usb_storage does not exist. 



What should I do to mount this drive in fstab?

---

### Post by IcarusR on 2010-12-23
If you can copy files to & from drive then it is already mounted.

To see list of mounted drives from a terminal run

```
sudo fdisk -l
```

> On running sudo mount -a the following error is returned: //192.168.0.1/readyshare/usb_storage /media/readyshare vfat defaults 0 2


The actual error would be helpful.

---

### Post by Stephen Shellard on 2010-12-23
I see now that I did not quote  error message correctly:  it is:  

> mount: special device //192.168.0.1/readyshare/usb_storage does not exist.


Out put from ```
sudo fdisk -l
```:

> Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7b7d7b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10012    80416768   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9ac0f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1257    10096821   83  Linux
/dev/sdb2           38176       38913     5927954+   5  Extended
/dev/sdb3            1258       38175   296543835   83  Linux
/dev/sdb5           38176       38913     5927953+  82  Linux swap / Solaris

Partition table entries are not in disk order

I am not seeing my 2GB USB drive in this.

Thanks very much for your interest!

---

### Post by IcarusR on 2010-12-31
> Samba the pathway smb://readyshare/usb_storage/

Silly thought but worth a try... if smaba sees it as //readyshare/usb_storage/  try mounting that ....

```
sudo mount -t smbfs //readyshare/usb_storage/ /media/readyshare
```

Obviously the mount point /media/readyshare must exist.

---

### Post by khaidinh on 2011-01-24
I posted something in another thread that might help:

[http://ubuntuforums.org/showthread.php?p=10394497](http://ubuntuforums.org/showthread.php?p=10394497)

---

### Post by jamie.nicholson on 2011-05-18
I've got a N300 to, spent an half an hour on the docs, hope this helps some other users.

$sudo smbclient -L 192.168.1.1
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.13]

	Sharename       Type      Comment
	---------       ----      -------
	USB_Storage     Disk      read:all-no password;write:all-no password
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.13]

	Server               Comment
	---------            -------
	READYSHARE           readyshare

	Workgroup            Master
	---------            -------
	WORKGROUP            READYSHARE


Why O Why do they call the Sharename USB_Storage but it's readyshare on windows shrug

sudo apt-get install smbfs

sudo smbmount //192.168.1.1/USB_Storage /media/nas 
sudo mount -t smbfs //192.168.1.1/USB_Storage /media/nas

Haven't bothered putting it in fstab though I'm sure it will be pretty straight forward now with the correct share name.

---

### Post by schoelje on 2011-07-11
I've done the following on my Debian machine (so I suppose it'll work on other distros as well):

Test in Nautilus / Go / Location:
smb://192.168.1.1/USB_Folder

Test in Terminal:
sudo mount -t cifs //192.168.1.1/USB_Folder /media/USB_Folder -o username=routerlogin,password=routerpwd
When done:
sudo umount /media/USB_Folder

Edit fstab:
gksu gedit /etc/fstab

And copy these lines:
# Entry for NAS
//192.168.1.1/USB_Folder   /media/USB_Folder   cifs   username=routerlogin,password=routerpwd,_netdev   0 0

Reboot

Hope this will help

---

### Post by gibahca on 2012-01-24
This is awesome help listed here in this thread.

Thank you very much schoelje and jamie.nicholson
Thanks go to OP as well.

everything works perfect now with my N300.

---

### Post by LauraG on 2012-01-31
Can anyone tell me how to access this drive using Ubuntu 11.10? I am new to Linux.

---

### Post by RobCandee on 2012-06-02
I have a Netgear WNDR4500, and was able to set up Ubuntu 11.10 to access the ReadyShare USB_Storage directory with just the smbmount command listed by jamie.nicholson above.  (I did have to install smbfs.)  I decided to use /media/readyshare instead of /media/nas, so my command was 

sudo smbmount //192.168.1.1/USB_Storage /media/readyshare

The second command jamie listed, the mount command, kept giving me error(16) Device or resource busy, but I tried to list the /media/readyshare directory, and found I had access already!  I am now able, for example, to rsync to directories on the USB device attached to my WNDR4500

---

### Post by Mash909 on 2013-01-31
Thanks for the info.

Worked for me with a bit of tweaking (N300 DGN2200)

fstab:
[FONT="Courier New"]//192.168.0.1/USB_Storage /media/readyshare cifs _netdev 0 0[/FONT]

(you have to mkdir /media/readyshare yourself)

USB drive had to be formatted as FAT

---

### Post by Steve.G on 2013-08-05
I followed the great directions in this thread and everything worked perfectly, except that I can only modify files in my usb drive if I use elevated (root) access to do it.

```

steve@phoenix:~/nas$ touch foo.txt
touch: cannot touch `foo.txt': Permission denied
steve@phoenix:~/nas$ sudo !!
sudo touch foo.txt
[sudo] password for steve: 
steve@phoenix:~/nas$ 

```

---

### Post by rob-candee on 2014-03-02
Since my last post, the (deprecated) smbmount command was removed from the smbclient package. 

After another long bout of research, I found that I can use the following instead:

sudo mount -t cifs //192.168.1.1/USB_Storage /media/readyshare -o username=<myUserID>,password=<myPassword>,sec=ntlm

The mount command would not work without the username/password options, nor would it work with them unless I added the sec=ntlm option.


> **RobCandee said:**
> I have a Netgear WNDR4500, and was able to set up Ubuntu 11.10 to access the ReadyShare USB_Storage directory with just the smbmount command listed by jamie.nicholson above.  (I did have to install smbfs.)  I decided to use /media/readyshare instead of /media/nas, so my command was 

sudo smbmount //192.168.1.1/USB_Storage /media/readyshare

The second command jamie listed, the mount command, kept giving me error(16) Device or resource busy, but I tried to list the /media/readyshare directory, and found I had access already!  I am now able, for example, to rsync to directories on the USB device attached to my WNDR4500

---

### Post by Jason_Schoenbrun on 2014-10-17
> **rob-candee said:**
> Since my last post, the (deprecated) smbmount command was removed from the smbclient package. 

After another long bout of research, I found that I can use the following instead:

sudo mount -t cifs //192.168.1.1/USB_Storage /media/readyshare -o username=<myUserID>,password=<myPassword>,sec=ntlm

The mount command would not work without the username/password options, nor would it work with them unless I added the sec=ntlm option.


OMG this took me way too long to figure out - to the order of 15 hours. I'm no Linux expert, but I'm certainly no beginner either, and am pretty good at Googling to research. So thank you rob-candee for the solution that finally, actually worked!!!


sudo mount -vt cifs //10.0.0.138/usb_storage /media/windowsshare2 -o user=guest,domain=WORKGROUP,password=,sec=ntl


It did not work without those 3 options. I sincerely hope my upvote here for this solution helps someone so that my 15 hours didn't completely go to waste.

---

