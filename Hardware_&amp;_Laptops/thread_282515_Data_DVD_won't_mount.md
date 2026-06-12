---
title: "Data DVD won't mount"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by Robgould on 2006-10-22
Before I instaled Ubuntu (Edgy) I made a data DVD backing up all of my files.  I did this from WinXP using Nero.  

The install of Ubuntu went fine and everything seems ok except when I put the DVD in I get an error that the Drive can't be mounted.  I copied what I get from the terminal here.  

I hope someone can help me.

```

rgould@rgould-laptop:~$ sudo mount /dev/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rgould@rgould-laptop:~$ dmsg | tail
bash: dmsg: command not found
rgould@rgould-laptop:~$ dmesg | tail
[17179613.604000] Bluetooth: HCI socket layer initialized
[17179613.616000] ath0: no IPv6 routers present
[17179613.896000] Bluetooth: L2CAP ver 2.8
[17179613.896000] Bluetooth: L2CAP socket layer initialized
[17179614.260000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179614.428000] Bluetooth: RFCOMM socket layer initialized
[17179614.428000] Bluetooth: RFCOMM TTY layer initialized
[17179614.428000] Bluetooth: RFCOMM ver 1.7
[17179753.108000] Unable to identify CD-ROM format.
[17190624.980000] Unable to identify CD-ROM format.


```

---

### Post by taurus on 2006-10-22
Try something like

```

sudo mkdir /media/cdrom
sudo mount -t iso9660 /dev/hdc /media/cdrom

```

---

### Post by Robgould on 2006-10-23
Thank you for the reply.  Unfotunately it did not work.  Just to make sure, I took the DVD to work today.  It works fine on WinXP.

Here are the results:

```

rgould@rgould-laptop:~$ sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists
rgould@rgould-laptop:~$ sudo mount -t iso9660 /dev/hdc /media/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rgould@rgould-laptop:~$ dmesg | tail
[17179606.816000] Bluetooth: L2CAP ver 2.8
[17179606.816000] Bluetooth: L2CAP socket layer initialized
[17179606.944000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179606.968000] Bluetooth: RFCOMM socket layer initialized
[17179606.968000] Bluetooth: RFCOMM TTY layer initialized
[17179606.968000] Bluetooth: RFCOMM ver 1.7
[17179617.380000] ath0: no IPv6 routers present
[17180457.748000] Unable to identify CD-ROM format.
[17180462.804000] Unable to identify CD-ROM format.
[17180570.164000] Unable to identify CD-ROM format.

```

---

### Post by Jvaldezjr on 2006-10-25
I had this problem too, and I think I just resolved it.

In my /etc/fstab file I had:
```

DEVICE           MOUNT POINT        FS TYPE         OPTIONS
/dev/hdc        /media/dvd          iso9660,udf   ...more options...     
/dev/hdd        /media/cdrom        iso9660       ...more options...

```

Under FS Type I changed those to "auto" instead of listing out the file system type.  Then I was able to insert a data DVD and mount it.

You can also try [this wiki]("http://wiki.freegeek.org/index.php/Enabling_a_DVD-ROM") for more information.

---

### Post by Robgould on 2006-10-25
Thank you very much.  That worked for me too.  Just changed it to "auto" and I am off and running!

---

### Post by joselin on 2006-11-03
Does not work for me. If i type auto as fstype only let me read cdroms.
If i type udf,iso9660 i can read cdroms and dvds, but i can't burn dvds in any case.

When i insert an empty dvd i receive the following:
```
[17302466.300000] cdrom: This disc doesn't have any tracks I recognize!
```

Any help will be appreciated.

---

### Post by Angellis_ater on 2006-12-04
I am receiving the same error - anyone?

---

