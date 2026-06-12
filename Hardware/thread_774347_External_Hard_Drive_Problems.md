---
title: "External Hard Drive Problems"
date: 2008-04-29
forum: Hardware
---

### Post by illusionweaver on 2008-04-29
I just put Ubuntu 8.04 on my laptop. Everythings working surprisingly well and going very smoothly, except for my external hard drive. It's a 1 TB WD My Book and I can't get write privileges for the drive on Ubuntu (I have them under Windows). I've tried going into the properties of the drive and changing permissions but when I do I get:

> Sorry, couldn't change the permissions of "My Book": Error setting permissions: Read-only file system

When I try and put files on the drive, I get this error message:

> Error opening file '/media/My Book/Granite.mp3': Read-only file system

---

### Post by Cannaregio on 2008-04-29
> **illusionweaver said:**
>  I've tried going into the properties of the drive and changing permissions but

[COLOR="Blue"]How[/COLOR] did you do it?
Is your harddisk ext3 or raiser (or is it NTFS?)
Did you use the terminal (supposed your harddisk is GNU/Linux formatted and is called "bigharddisk")? Don't use nautilus for permissions!

```
cd /media/bigharddisk
```
and then, once there 
```
sudo chmod 777 -R foldername
```

and so on... try to see if you can change permissions for a single folder...

---

### Post by illusionweaver on 2008-04-29
I tried your code and it executed, but I still can't write in the folders I changed permissions on.

Here's an example of the output:
> chmod: changing permissions of `Music/Orange Box/09 Guard Down.mp3': Read-only file system

---

### Post by woppy71 on 2008-04-29
[SIZE="3"]I had a similar problem with my external hard drive, but I found that if you type the following at the console, to start Nautilus in root mode:[/SIZE]

```
gksudo nautilus
```
[SIZE="3"]
Navigate to the folder that represents your hard drive, you should find that you can now change the access permissions as appropriate.

This worked for me, hope it does for you! :[/SIZE])

---

### Post by illusionweaver on 2008-04-29
I tried your solution and it didn't work. I've looked at the permissions again and it seems that root doesn't have permission to write either.

---

### Post by chrisccoulson on 2008-05-12
The filesystem is read only, so chmod'ing and chown'ing won't work. You need to find out why it is read only. My suspicion is that it has filesystem errors and you need to run dosfsck (assuming it is a vfat partition)

Are you still having problems? If so, do this in a terminal:
```
tail -f /var/log/syslog
```
...then connect the external drive, monitor and post the terminal output here.

---

### Post by dascheer on 2008-05-12
hey im having the same problem with my vfat-formatted external hard drive.  i tried doing the above solutions with no results.  i entered "tail -f /var/log/syslog" in the command line and this is what i got:

May 12 18:37:31 loveshak kernel: [  558.691051] FAT: Filesystem panic (dev sdb1)
May 12 18:37:31 loveshak kernel: [  558.691059]     fat_get_cluster: invalid cluster chain (i_pos 0)
May 12 18:37:31 loveshak kernel: [  558.693456] FAT: Filesystem panic (dev sdb1)
May 12 18:37:31 loveshak kernel: [  558.693460]     fat_get_cluster: invalid cluster chain (i_pos 0)
May 12 18:37:31 loveshak kernel: [  556.895444] FAT: Filesystem panic (dev sdb1)
May 12 18:37:31 loveshak kernel: [  556.895452]     fat_get_cluster: invalid cluster chain (i_pos 0)
May 12 18:37:31 loveshak kernel: [  556.897736] FAT: Filesystem panic (dev sdb1)
May 12 18:37:31 loveshak kernel: [  556.897740]     fat_get_cluster: invalid cluster chain (i_pos 0)
May 12 18:38:17 loveshak kernel: [  603.202415] nautilus[6812]: segfault at a0000018 eip b76e32d6 esp bf8ebdd0 error 4
May 12 18:38:49 loveshak dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 12 18:38:52 loveshak dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 12 18:38:56 loveshak dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 12 18:39:01 loveshak /USR/SBIN/CRON[7058]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May 12 18:39:07 loveshak dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 12 18:39:19 loveshak dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May 12 18:39:20 loveshak dhclient: No DHCPOFFERS received.
May 12 18:39:20 loveshak dhclient: No working leases in persistent database - sleeping.

---

### Post by chrisccoulson on 2008-05-12
Yes, the above solutions won't work as your filesystem is broken. **Making sure the volume is unmounted first**, do the following in a terminal:
```
sudo dosfsck -a -v /dev/sdb1
```
...where /dev/sdb1 is your broken vfat volume.

---

### Post by Stephyslefthand on 2009-07-20
QUOTE=woppy71;4837519][SIZE="3"]I had a similar problem with my external hard drive, but I found that if you type the following at the console, to start Nautilus in root mode:[/SIZE]

```
gksudo nautilus
```
[SIZE="3"]
Navigate to the folder that represents your hard drive, you should find that you can now change the access permissions as appropriate.

This worked for me, hope it does for you! :[/SIZE])[/QUOTE]

Thank you! This worked like a charm! :mrgreen: ive been all over looking for this! :D  God Bless America and Ubuntu!:D\\:D/

Stephanie

---

