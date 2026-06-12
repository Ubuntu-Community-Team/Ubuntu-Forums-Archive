---
title: "Setup a new drive with dd partition creation"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2009-05-31
Greets

I have successfully dd'd and created my root to a second drive that I have set-up for testing new kernels and such.

In this fdisk of my system, /dev/sda8 is also now /dev/sdb1. Also, /dev/sda6 is a separate /home partition. 

 ```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dc84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609      121601   971876272+   5  Extended
/dev/sda5             609         851     1951866   82  Linux swap / Solaris
/dev/sda6             852        5714    39062016   83  Linux
/dev/sda7           14737      121601   858393081   83  Linux
/dev/sda8            5715       14736    72469183+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000132c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9594    77063773+  83  Linux
/dev/sdb2            9595       19187    77055772+  83  Linux
/dev/sdb3           19188       20186     8024467+  83  Linux
/dev/sdb4           20187       60801   326239987+  83  Linux

```

All I want to do is create grub entries for the same Ubuntu kernels on that 2nd drive as boot options from my existing grub. I also keep them pointing to /dev/sda6 as /home (I believe that will still be the case once booted to them, but I am not totally sure)

I suspect that I may have to alter some mount points on the new disk once I do get into it and probably have to config the menu.lst in a different set-up

I know that I could also dd my /home directory to that new disk and just boot from the 2nd (bios level), but I am trying to get handles on what you can do with grub,dd,backups,restores and different levels of kernels. 

Any and all wisdom is appreciated and profoundly valued.

---

### Post by logos34 on 2009-05-31
Like you say, you'll need to edit menu.lst (and fstab)--in this case with new UUIDs for the image of /.

You need to actually assign a new one to sdb1 to differentiate it from sda8, because dd essentially make a clone of the partition, right down to the uuid.

generate new UUID:

> sudo tune2fs -U random /dev/sdb1

Create a mountpoint for sdb1 and mount it:

> sudo mkdir /media/wherever

sudo mount -t ext3 /dev/sdb1 /media/wherever

Now find and copy the new UUID you made for sdb1:

> sudo blkid

and edit menu.lst and fstab:

> gkudo gedit /media/wherever/etc/fstab


Do the same for /media/wherever/boot/grub/menu.lst, replacing existing uuid in 'kopt', 'groot' and 'kernel' lines.

Now copy first entry to your menu.lst on sda8 so you can boot sdb1.  (the only diff between the entries is the UUID)...It should be using symlink format, i.e. '/vmlinuz' and '/initrd.img' (no trailing kernel vers. #'s '-2.6.x.x')

never tried this with common /home, though, so not sure how that will work out

that's how I'd do it

---

### Post by VastOne on 2009-05-31
> **logos34 said:**
> Like you say, you'll need to edit menu.lst (and fstab)--in this case with new UUIDs for the image of /.

You need to actually assign a new one to sdb1 to differentiate it from sda8, because dd essentially make a clone of the partition, right down to the uuid.

generate new UUID:



Create a mountpoint for sdb1 and mount it:



Now find and copy the new UUID you made for sdb1:



and edit menu.lst and fstab:




Do the same for /media/wherever/boot/grub/menu.lst, replacing existing uuid in 'kopt', 'groot' and 'kernel' lines.

Now copy first entry to your menu.lst on sda8 so you can boot sdb1.  (the only diff between the entries is the UUID)...It should be using symlink format, i.e. '/vmlinuz' and '/initrd.img' (no trailing kernel vers. #'s '-2.6.x.x')

never tried this with common /home, though, so not sure how that will work out

that's how I'd do it

Logos34

Thanks for the quick and very informative response....

Couple of quick questions:  

1 - Here

```
# / was on /dev/sda1 during installation
UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=62a065f5-12f3-45b4-9d5b-ea688ab9dd54 /home           ext4    relatime        0       2
# /media/storage was on /dev/sda7 during installation
UUID=90717cea-057d-40f3-933f-e6be006437eb /media/storage  ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=1e69e4f4-2339-493b-a693-3bd0c6cda8e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Does fstab look exclusivity (only) at UUID? It appears it does and I just want confirmation. For that matter does any code at this level look only at UUID?

Second - This is the list that I will take from menu.lst on sdb1 to sda8.

```
title		Ubuntu 9.04, kernel 2.6.29.4-candela
uuid		b3dbacc7-9635-4e63-adcb-3ceddba5c318
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.29.4-candela
quiet
```

```
title		Ubuntu 9.04, kernel 2.6.29.4-candela
uuid		b3dbacc7-9635-4e63-adcb-3ceddba5c318
kernel		/boot/vmlinuz root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro quiet splash vga=771 
initrd		/boot/initrd.img
quiet
```

Is that how it should look?

---

### Post by logos34 on 2009-05-31
> **VastOne said:**
> Does fstab look exclusivity (only) at UUID? It appears it does and I just want confirmation. For that matter does any code at this level look only at UUID?

Yes.  (Used to be different). At boot the system will look and mount the partition with that exact UUID.


> title		Ubuntu 9.04, kernel 2.6.29.4-candela
uuid		b3dbacc7-9635-4e63-adcb-3ceddba5c318
kernel		/boot/vmlinuz root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro quiet splash vga=771 
initrd		/boot/initrd.img
quiet

Is that how it should look?

yep. The reason for the symlink format is it's a 'set it 'n forget' type thing--you won't have any problems booting the newest kernel if you should ever update it.  In fact, you could use it for both sda8 and sdb1 entry.  More about it [here]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink").

---

### Post by VastOne on 2009-05-31
> **logos34 said:**
> Yes.  (Used to be different). At boot the system will look and mount the partition with that exact UUID.




yep. The reason for the symlink format is it's a 'set it 'n forget' type thing--you won't have any problems booting the newest kernel if you should ever update it.  In fact, you could use it for both sda8 and sdb1 entry.  More about it [here]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink").

logos34

Again, my gratis for your tremendous help! :D

I had to put back in the complete line instead of the symlink.  I got an error 15  file not found when I booted but when I put the complete lines of:

```
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro  single
initrd		/boot/initrd.img-2.6.29.4-candela
```

It worked.  I will investigate this more using the site you gave me.

Thank you!

Edit

I see the reason, found it at the website you gave on grub page.  I need to take out the /boot section and it should read:

```
kernel		/vmlinuz root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro  single
initrd		/initrd.img
```

---

### Post by logos34 on 2009-05-31
> **VastOne said:**
> 
I see the reason, found it at the website you gave on grub page.  I need to take out the /boot section and it should read:

```
kernel		/vmlinuz root=UUID=b3dbacc7-9635-4e63-adcb-3ceddba5c318 ro  single
initrd		/initrd.img
```


exactly.  sorry I missed that the first time

---

### Post by VastOne on 2009-05-31
> **logos34 said:**
> exactly.  sorry I missed that the first time

No worries....

So even if you have multiple kernels on your setup, if you put those changes it will still pickup the correct kernel? I mean if I chose my second kernel, 2.6.28-12 in grub, it will automagically use that kernel if I have all of them point to the same /vmlinuz and /initrd.img?

On another note...On your taglines I see you are an OGG Vorbis fan, do you know of a conversion program that will handle 9000 .wma files?

Edit

I see that the /root versions of vmlinuz and initrd.img will point only to the latest kernel

---

### Post by logos34 on 2009-05-31
> **VastOne said:**
> So even if you have multiple kernels on your setup, if you put those changes it will still pickup the correct kernel? I mean if I chose my second kernel, 2.6.28-12 in grub, it will automagically use that kernel if I have all of them point to the same /vmlinuz and /initrd.img?

yes, becquse it's looking for the symbolic links 'vmlinuz' and 'initrd.img' in the / directory *of the specified partition (UUID)*.  Normally, only the first (latest) kernel entry should use that format.  But your case is special because you also want to be able to boot sdb1.  Does that clarify? As you added, they point by default to the latest kernel.

> On another note...On your taglines I see you are an OGG Vorbis fan, do you know of a conversion program that will handle 9000 .wma files?

hmm, only 9000, eh? I'd probably use ffmpeg with a bash script for batch conversion.  I have a few scripts, but mostly for lossless (m4a/alac, flac, ape) to lossy (ogg, mp3, m4a/aac).  Lemme double check...

EDIT: transcoding lossy-to-lossy is a last resort (like when your portable player doesn't support that format).  It degrades the sound.  Most ubuntu media players on the desktop will playback wma, just a matter of getting the right codecs (ubuntu-restricted-extras, w32codecs)...some like amarok (using xine engine) support it natively. So unless you have a compelling reason, leave them wma

---

### Post by VastOne on 2009-05-31
> **logos34 said:**
> yes, becquse it's looking for the symbolic links 'vmlinuz' and 'initrd.img' in the / directory *of the specified partition (UUID)*.  Normally, only the first (latest) kernel entry should use that format.  But your case is special because you also want to be able to boot sdb1.  Does that clarify? As you added, they point by default to the latest kernel.



hmm, only 9000, eh? I'd probably use ffmpeg with a bash script for batch conversion.  I have a few scripts, but mostly for lossless (m4a/alac, flac, ape) to lossy (ogg, mp3, m4a/aac).  Lemme double check...

EDIT: transcoding lossy-to-lossy is a last resort (like when your portable player doesn't support that format).  It degrades the sound.  Most ubuntu media players on the desktop will playback wma, just a matter of getting the right codecs (ubuntu-restricted-extras, w32codecs)...some like amarok (using xine engine) support it natively. So unless you have a compelling reason, leave them wma

Figured as much...

A final note on this dd process.  I have been using apps such as remastersys as a backup and restore process, but what I just accomplished is what I would consider as the absolute best in getting it done.  I notice one of your taglines is about parted magic that uses many these tools.  What do you personally choose as your own backup and restore methodology?

---

### Post by logos34 on 2009-05-31
I use Partimage (on the Parted Magic cd) to make a backup image of / once a week.  (clonezilla would be my other choice, if I needed ext4 support.)

For /home files I just use tar (tar.gz) periodically

---

