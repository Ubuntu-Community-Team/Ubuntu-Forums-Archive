---
title: "Hard Drive failure after being in Windows."
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by Theely on 2006-01-29
Ok here is the quick story. My friends computer recently got mauled by what we think was a virus. Either that or this hard drive in question is just biting the dust. I don't think its the later because its a pretty new drive. Only about 4 months old.

Anyways. The BIOS detects the drive and knows the size WD:200GB. The problem comes when its time to write to the disk when formatting or trying to create a partition on it.

When trying to install an OS on it, WinXP or Linux(Ubuntu, Mandriva, or Fedora) and error will occur staying that there was a red error (Blue screen of crypic non-understanding on WinXP, and "error on the superblock" from Ubuntu).

So, I install Ubuntu on a spare 30GB drive then after the system is up and running and shutdown and hook up the 200GB drive. Once again, BIOS detects it and Ubuntu can see it buts about as far as I can go. During the book up process I get a series of odd messages (Which I'll post in a second with all the other info) and when I goto Disk Management it can see the drive as /dev/hdb which is correct but once again thats are far as it will go. Can't access it in any form and "fdisk -l" does not sure it.

So does it sound like the drive is just shot?
Also are there any super-powered linux programs to help maybe try to zero out this drive or something?

My next post will now show the results of fdisks and the boot up errors.

---

### Post by Theely on 2006-01-29
Results of "fdisk -l"
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

```

Screen shot of Disk Management (It can see the drive)
[[IMG]http://img52.imageshack.us/img52/5912/screenshot9lp.th.png[/IMG]](http://img52.imageshack.us/my.php?image=screenshot9lp.png)

---

### Post by blackant on 2006-01-29
Maybe you can try to get the disk management ultility from the disk manufacturer and run to detect any error on the disk...

btw, your background looks cool. :P
Where did you get it?

---

### Post by Theely on 2006-01-29
I guess I could try to find something. A year ago when I was looking at the Western Digital site I don't think I found any Linux utilities though. Hopefully times have changed.

As for the background! I got that the Ubuntu Art site. From the Wiki I believe :mrgreen: 

Here is a full un-cluttered shot of it.
[[IMG]http://img98.imageshack.us/img98/442/screenshot9lt.th.png[/IMG]](http://img98.imageshack.us/my.php?image=screenshot9lt.png)


Also, I did just check the Western Digital site and they have nothing for Linux. No support at all besides jumper configs and how to hook it up to your computer hehe.

---

### Post by blackant on 2006-01-30
Check this page out.
They should be able to boot up from floppy disk or cdrom, then you can check your drive. ;)

[http://support.wdc.com/download/index.asp?cxml=n&pid=999&swid=2](http://support.wdc.com/download/index.asp?cxml=n&pid=999&swid=2)

---

### Post by Theely on 2006-01-30
I did try that site. See the problem is that there is no longer an OS on the 200GB HDD. Maybe half of the drive has some of the XP OS still on it but over all the drive seems dead.

Only the BIOS and a disk managment utility can see the drive (and get all the correct info from it), but you just can't do anything to it.

Edit: Also here is the results of a "sudo fdisk /dev/hdb"
```

michael@ubuntu:/$ sudo fdisk /dev/hdb

Unable to read /dev/hdb

```

Just a straight up attemp to mount the HDD
```

michael@ubuntu:/$ sudo mount -t ext3 /dev/hdb /mnt/second_hdd
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I had a feeling that one wouldn't work in the first place since I'm no longer sure how the drive is formatted.
It was in Windows but several attemps to format it since then has left it with who knows what.
Had a failed format via WinXP and Ubuntu (during a "fresh" install of both) but freezing up anywhere between 10% and 40% completed.
Now it won't even try to format it.

---

### Post by Horndog on 2006-01-30
Most times a virus will write itself to the boot sector. To completely get rid if it you have to do a low level format. If the virus did not destroy the boot sector your lucky. You will have to find a tool to do [this.]("http://www.google.com/search?hs=4sy&hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=low+level+format+tool&btnG=Search")

---

### Post by Theely on 2006-01-30
Thanks for the input. I starting looking for some LLF utilities and I found one that says I need to have an x86 processor. Athlon 64 is not a x86 correct? What do they call the 64 processors anyways? Just 64-bit?

---

### Post by Theely on 2006-02-01
I fixed the HDD using the shred utility that comes with Linux systems. Didn't even know it existed until then.

I just shredded /dev/hdb and the drive was fixed after that.

Thanks

---

### Post by blackant on 2006-02-02
[QUOTE=Theely]I fixed the HDD using the shred utility that comes with Linux systems. Didn't even know it existed until then.

I just shredded /dev/hdb and the drive was fixed after that.

Thanks[/QUOTE]
hehehe.. guess it did a full format.
glad that you solve your problem. ;)

---

