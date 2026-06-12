---
title: "Booting nightmare"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by pette on 2008-12-24
Hey guys,

I have Windows XP installed on a SATA drive (hd1 which is /dev/sdb) and I installed ubuntu 8.10 on hd0 (which is /dev/sda). I installed grub on /dev/sdb which is the Windows SATA disk since Windows would load automatically and bypass grub completely if I installed grub on /dev/sda.

Now when I choose "Windows XP" from the grub boot menu it gives the following error: "Error 13: "Invalid or unsupported executable format".

I searched around for a long time and I tried editing the grub instructions pertaining to loading windows to no avail. Im getting really really really frustrated with grub. I tried almost ALL variation of the following:

rootnoverify (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1 

Im starting to think it has something to do with the two drives being different: one SATA and the other PATA.
 
Anyway, your help is most appreciated guys.

Pete

---

### Post by Herman on 2008-12-24
Your (hd1), or /dev/sdb seems to be your first hard disk, according to your BIOS, since you said that if you didn't install GRUB to (hd1) your Windows would boot automatically.

I guess Windows probably thinks it's in hard drive 1 too then.
Try this,
```
title    Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader        +1 
```Error 13 would have been caused by the fact that no boot loader code exists in the boot sector you were trying to boot, which would probably have been your Ubuntu boot sector, because of the confusion over the hard disk numbering in the various softwares.

---

### Post by pette on 2008-12-24
Thank you for your reply.

I know what you mean, and I did try that and what I get is:

"Starting up ..."

and the whole computer freezes up.

Any ideas?

---

### Post by caljohnsmith on 2008-12-24
It sounds like your Windows partition boot sector might possibly need fixing; please post the output of:
```
sudo fdisk -lu
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sdb1
```
Assuming Windows is on sdb1.

P.S. Merry Christmas, Herman! :)

---

### Post by Herman on 2008-12-24
> I know what you mean, and I did try that and what I get is:

"Starting up ..."

and the whole computer freezes up.

Any ideas?Oh, okay, but it seems to be a step in the right direction, because at least now GRUB is finding the Windows boot sector, (at least I think so).

I agree with caljohnsmith, (Merry Christmas to you too, clajohnsmith :) ), it seems to me as if there might be some kind of a problem with Windows now.
Maybe it's the boot sector, although I don't know why that would be...

.... does it only say 'Starting up ...', or does it say that and also, [A Disk Read Error Occured]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Disk_Read_Error_Occured")?

I remember one time a friend of mine brought me a hard disk with Windows in it and it refused to boot, and had that error message. I tried all kinds of ideas and in the end I got it working by moving the Windows partition to the other end of the disk with GParted. I don't know why that worked, but it did.
(Then after all that, my freind decided he only wanted Ubuntu and had me delete Windows for him (LOL)).  The same hard disk is still working fine with Ubuntu in it, so I don't know what the real problem might hve been.

---

### Post by pette on 2008-12-24
Well this fixed it:

root (hd0,0)
savedefault
makeactive
chainloader (hd0,0)+1

I was amazed that making the typo of not having SPACE before the '+1' actually did it!!!

Thank you guys for ur help. This is definitely a friendly place to be.

Pete

---

### Post by Herman on 2008-12-24
> :)
Well this fixed it:
root (hd0,0)
savedefault
makeactive
chainloader (hd0,0)+1
I was amazed that making the typo of not having SPACE before the '+1' actually did it!!!
Thank you guys for ur help. This is definitely a friendly place to be. Cool! Well done pette, I would never have guessed that one! I'll have to file that info and keep it handy. (Or bookmark this thread). :)

:P Hey caljohnsmith, 
```
sudo fdisk -lu
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sdb1
```I tried that just for fun in a computer that has Windows XP in it and I got '0' (zero).
Is that the expected result?

In an NTFS partition, there's a backup of the boot sector stored in the last sector of the partition, but if it's a partition containing a FAT file system, the backup boot sector is the sixth, (I think..but I'll have to check up on that to make sure I'm right).
Anyway, the main thing I wanted to say is, another way to compare the NTFS boot sector with it's backup , is to use GRUB's cmp command.

From the fdisk -lu output, you might find out the Windows begins and sector 63 and ends at sector 24306344 or something, (it could be any number).
You can do,
```
sudo grub
``````
root (hd0)
``````
cmp 63+1 24306344+1
```If you get any output then you know there's a difference between the boot sector and it's backup, the absence of any output means the boot sector has passed the test.

Just because a boot sector isn't the same as it's backup might not necessarily be cause for alarm though, although it may be suspicious. 
Here's a link, [**[B]Not automatically fixing this**[/B]]("http://ubuntuforums.org/showthread.php?t=189238&highlight=boot+sector"), they're mainly talking about FAT32 file systems in that, but it's interesting there in post #10 where ncdave4life explains that it's just a boot sector from WIN98SE as opposed to a WIN 2000/XP boot sector that's causing the discrepancy in his case.
Some viruses, on the other hand, do like to write to the Windows boot sector.

---

### Post by caljohnsmith on 2008-12-24
Hi Herman, that hexdump command should return the starting sector of the Windows NTFS partition, because at least from the testing I've done, it seems that info is embedded in the first sector of the Windows partition starting at an offset of 28 bytes in little-endian format; I've only tested it on NTFS partitions, so I don't know if FAT32 partitions store that info in the same place. Is your Windows partition NTFS or FAT32? If it is NTFS, how about posting your partition boot sector so I can look at it. :)

---

### Post by Herman on 2008-12-24
:) Sure, here it is,
```
herman@lec-jaunty:~$ sudo dd if=/dev/sda skip=63 count=1 | hexdump -C
[sudo] password for herman: 
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  60 e2 72 01 00 00 00 00  |........`.r.....|
00000030  00 00 0c 00 00 00 00 00  30 de 17 00 00 00 00 00  |........0.......|
00000040  f6 00 00 00 01 00 00 00  94 f6 da c0 27 db c0 ac  |............'...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0209187 s, 24.5 kB/s

``` This one's NTFS.

Is that in the format you required?

---

### Post by meierfra. on 2008-12-25
Herman,

According to the hexdump you posted

```
sudo hexdump -s 28 -n 4 -e '"%d\n"'[COLOR="Red"]/dev/sda1[/COLOR]
```

should return 63. That code looks at the last 4 bytes in the second line of the boot sector 

```

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 [COLOR="Red"]3f 00 00 00[/COLOR]
```

and translates it into decimals.

If you enjoy these kind of investigation, you might try out the script caljohnsmith and I have been developing:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

This downloads the script "boot_info_script.txt" to your desktop and then runs it. It will create the file "RESULTS.txt"  on your desktop with all kinds of  booting related information.

---

### Post by Herman on 2008-12-25
Oh of course! Silly me, what was I thinking, (not very much, obviously) :oops:
NOW I'm getting the right answer, thank you, meierfra! :)

Thanks for the script too, I've noticed it being used, but I haven't had a look at it myself yet, I will now, it looks interesting. 

Regards, Herman :)

Oh, and Merry Christmas too!

---

### Post by Herman on 2008-12-27
:) Wow!

---

