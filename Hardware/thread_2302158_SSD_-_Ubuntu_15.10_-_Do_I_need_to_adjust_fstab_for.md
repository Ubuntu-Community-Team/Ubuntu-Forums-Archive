---
title: "SSD - Ubuntu 15.10 - Do I need to adjust fstab for trim etc,"
date: 2015-11-08
forum: Hardware
---

### Post by ales on 2015-11-08
Hello there,

after years I bought yesterday SSD and made a clean install. Everyithing is fine and fast. I red a lot of posts about tweaking SSD in Ubuntu. But mostly for the older version. My question is, do I need to alter, or add any paramaters to fstab to get most of SSD, or is it done by default in 15.10?

My fstab looks following:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4f3f766a-cac9-4eee-bba5-178068081939 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aaafa839-f6b7-415c-b443-8a5083e2536b none            swap    sw              0       0
```


Thanks for any links or advices.

Ales

---

### Post by oldfred on 2015-11-08
Newer ones many not need anything or much.

But I add noatime parameter, but I understand a very few apps need to know if file was accessed. Have not had any issues.
Someone posted this:
 with newer SSDs relatime a reasonable alternative to noatime and works with some apps that need timestamps like mutt
See man mount for details on relatime

```
# / was on /dev/sda3 during installation
UUID=45de38c8-6748-4634-b207-628d9aa8b42b /               ext4    noatime,errors=remount-ro 0       1

```

I also added my own cron task for trim. Was not sure the checks for SSD models in Ubuntu's version was running trim on my model or not. And was reasonably sure I could run trim on my SSD.
I used this as model for my cron script:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

       [URL="https://sites.google.com/site/easylinuxtipsproject/ssd"]https://sites.google.com/site/easylinuxtipsproject/ssd
[/URL]
 HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)[URL="https://sites.google.com/site/easylinuxtipsproject/ssd"]
[/URL]

---

### Post by ales on 2015-11-09
Thanks for the links.

Tried to use the check and that seems to show as it is not working, doesn't matter if I have nodiscard in fstab or not.

See here:
dreamwalker@dreamwalker-System-Product-Name:~$ sudo /tmp/test_trim.sh tempfile 50 /dev/sda
0+1 records in
0+1 records out
33554431 bytes (34 MB) copied, 1,69411 s, 19,8 MB/s

tempfile:
 filesystem blocksize 4096, begins at LBA 2048; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0   19712000   19777535      65536

/dev/sda:
reading sector 19712000: succeeded
f342 65a2 904b 11dc 05dd 8cf4 69a2 1714
35a7 a456 4646 ec15 4694 1dc6 19b1 8fbe
d3c4 7b5a 236b 2f63 4140 6dcc de30 747d
da35 5eaa fdc6 24a2 aea7 00d5 eaeb 1045
9594 5e10 5322 81ea f62e e4ad 0b34 7ef6
a4f8 8a7b 02b4 3d22 89f8 a739 fa85 5b07
bf6e 1ecc 457e 4433 5703 6079 6ce2 3501
8294 899c 2758 23a1 db2b 9144 e2d7 ec13
107e 2058 8d39 2aab 8680 a4d3 cd51 5f4e
73a8 f146 d798 5f62 7067 b74e 5c1a bd19
5f37 095a 8320 a1f5 e32b d3be 23b3 f8b6
6625 1bda f67d 6999 7b7e e433 aed2 6fba
7f48 8e6c edbc b97b 1be8 ef75 17d3 7aee
6aa3 1085 7800 59b5 9a26 0305 5f99 8f17
052a 2b91 2357 07f8 6d03 58f5 01ce a005
980d 4e46 b384 aede e04e 5334 db12 ab2c
c929 4b2d e9d6 d11a 8844 05b0 e389 2b36
c1ee e911 e771 db18 3380 32c5 aa9c 49fe
5023 fdbe c5cb 8dd2 22a5 5c5f e80b f88d
681c 5fb6 96ad adb2 5305 a545 c73d 615e
e8d5 25b5 6894 6e76 5603 76bb 3908 0b69
02ac 7efc e1cb 40c0 24f7 21aa 4af2 d6a1
845d 39a7 47a0 a1dc ba09 39ec 38ef 6909
1da1 7344 8776 0cd2 ccb0 ca48 40cb c1a6
444d 1aa5 487a 664d 3c72 cbb5 b8b5 983f
5a3d a314 d8d6 a0fb bcdf 58d1 83a6 87f6
b874 e9fb b0a2 64eb 5497 6d42 073f 182e
61b4 ebb7 ffc8 38fe 5c53 36b2 1bdf b245
a08a 7cc3 f8f5 b411 dc5a e3d4 3021 3445
4499 c5b0 f087 36d6 e8b1 277c 189e 2670
fc2f dd12 1ca8 c1c8 d2b0 4980 1206 2709
15f1 c0b7 cdd0 b821 e7c0 003c 3491 be5d

This is a sector of the file. It should have been successfully read
and show a bunch of random data.

Press any key to continue...

File deleted. Sleeping for 120 seconds before re-reading the sector.
If TRIM is working, you should see all 0s now.

/dev/sda:
reading sector 19712000: succeeded
f342 65a2 904b 11dc 05dd 8cf4 69a2 1714
35a7 a456 4646 ec15 4694 1dc6 19b1 8fbe
d3c4 7b5a 236b 2f63 4140 6dcc de30 747d
da35 5eaa fdc6 24a2 aea7 00d5 eaeb 1045
9594 5e10 5322 81ea f62e e4ad 0b34 7ef6
a4f8 8a7b 02b4 3d22 89f8 a739 fa85 5b07
bf6e 1ecc 457e 4433 5703 6079 6ce2 3501
8294 899c 2758 23a1 db2b 9144 e2d7 ec13
107e 2058 8d39 2aab 8680 a4d3 cd51 5f4e
73a8 f146 d798 5f62 7067 b74e 5c1a bd19
5f37 095a 8320 a1f5 e32b d3be 23b3 f8b6
6625 1bda f67d 6999 7b7e e433 aed2 6fba
7f48 8e6c edbc b97b 1be8 ef75 17d3 7aee
6aa3 1085 7800 59b5 9a26 0305 5f99 8f17
052a 2b91 2357 07f8 6d03 58f5 01ce a005
980d 4e46 b384 aede e04e 5334 db12 ab2c
c929 4b2d e9d6 d11a 8844 05b0 e389 2b36
c1ee e911 e771 db18 3380 32c5 aa9c 49fe
5023 fdbe c5cb 8dd2 22a5 5c5f e80b f88d
681c 5fb6 96ad adb2 5305 a545 c73d 615e
e8d5 25b5 6894 6e76 5603 76bb 3908 0b69
02ac 7efc e1cb 40c0 24f7 21aa 4af2 d6a1
845d 39a7 47a0 a1dc ba09 39ec 38ef 6909
1da1 7344 8776 0cd2 ccb0 ca48 40cb c1a6
444d 1aa5 487a 664d 3c72 cbb5 b8b5 983f
5a3d a314 d8d6 a0fb bcdf 58d1 83a6 87f6
b874 e9fb b0a2 64eb 5497 6d42 073f 182e
61b4 ebb7 ffc8 38fe 5c53 36b2 1bdf b245
a08a 7cc3 f8f5 b411 dc5a e3d4 3021 3445
4499 c5b0 f087 36d6 e8b1 277c 189e 2670
fc2f dd12 1ca8 c1c8 d2b0 4980 1206 2709
15f1 c0b7 cdd0 b821 e7c0 003c 3491 be5d

If the sector isn't filled with 0s, something is wrong with your
configuration. Try googling for "TRIM SSD Linux".

dreamwalker@dreamwalker-System-Product-Name:~$ ^C
dreamwalker@dreamwalker-System-Product-Name:~$ 

**So no zeros. But my disk is Kingston 240G 300V.**

dreamwalker@dreamwalker-System-Product-Name:~$ sudo hdparm -I /dev/sda | grep "TRIM supported"
[sudo] password for dreamwalker: 
	   *	Data Set Management TRIM supported (limit 1 block)
dreamwalker@dreamwalker-System-Product-Name:~$ sudo fstrim -v /
/: 203,9 GiB (218915864576 bytes) trimmed
dreamwalker@dreamwalker-System-Product-Name:~$ sudo chmod +x /etc/cron.daily/trim
dreamwalker@dreamwalker-System-Product-Name:~$ 

I also used commands to build the cron for trim, but how would I know it works I do not understand. For now system is very fast.

Ales

---

### Post by powder on 2015-11-09
FYI, Ubuntu already includes a cron job that calls fstrim once every week, so basically your SSD will be trimmed on a weekly basis by default.  It is located at /etc/cron.weekly/fstrim.

---

### Post by ales on 2015-12-02
Hello powder,

you are right I found this in that file:
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true

by default. Thanks.

A.

---

### Post by QIII on 2015-12-02
A note of caution for those who might suggest "discard" in fstab later:

Some SSDs do not support RCQ or do so poorly.  It may not be advisable to use "discard" in fstab when using one of those SSDs.

A cron job, as described, may result in less efficiency but will avoid bricking the device.  I have my cron job in daily.

---

