---
title: "HDD gpart *Warning strange partition table magic 0x0000"
date: 2013-06-22
forum: Hardware
---

### Post by PoopBaron on 2013-06-22
I have an external WD HDD that was unable to be recognized from the enclosure.  I removed and installed in my pc. It is being ready as physically there, but no recognizable filesystem can be found and after running gpart this was the message I recieved.

```

sudo gpart -vv /dev/sda

dev(/dev/sda) mss(512) chs(121601/255/63)(LBA) #s(1953520065) size(953867mb)


* Warning: strange partition table magic 0x0000.
Primary partition(1)
   type: 204(0xCC)(UNKNOWN)
   size: -7927056477100mb #s(5424113738198457652) s(-7863879035496896934--2439765297298439283)
   chs:  (143/101/28)-(908/151/33)d (658752881307977/66/20)-(996388345870595/58/5)r
   hex:  D9 65 1C 8F CC 97 E1 8C 5A E6 90 8C AE E3 DD 92 34 9D A2 EA B4 52 46 4B


Primary partition(2)
   type: 238(0xEE)(UNKNOWN)
   size: 6251289221706mb #s(517205798591550091) s(5424113738198432108-5941319536789982198)
   chs:  (1020/82/18)-(7/123/45)d (337635464562616/96/21)-(369830036525987/16/36)r
   hex:  8B 52 D2 FC EE 7B 2D 07 6C 39 A2 EA B4 52 46 4B 8B 52 D2 FC EE 7B 2D 07


Primary partition(3)
   type: 243(0xF3)(UNKNOWN)
   size: 25mb #s(52886) s(3423029787145561894-3423029787145614779)
   chs:  (361/57/18)-(315/81/3)d (213073749588892/189/8)-(213073749588896/8/36)r
   hex:  6C 39 52 69 F3 51 43 3B 26 67 64 96 74 0B 81 2F 96 CE 00 00 00 00 00 00


Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00




Begin scan...

```

It just stands on "Begin Scan..." with no other output, even after a few hours.
I have been digging in various forums, and have seen others with similar issues, but none that offer a solution to mine.  In GParted there are no flags and nothing can be done that would allow me to recover the data on this disk.  Any help is greatly appreciated.

---

### Post by ajgreeny on 2013-06-22
Did you find this post on the forum?  
[http://ubuntuforums.org/showthread.php?t=1680646](http://ubuntuforums.org/showthread.php?t=1680646)
It suggests that simply removing the LVM flag using gparted my help restore the disk to a usable state, but you say there are no flags showing, so this may be a spurious suggestion.  Do you have a windows computer available into which you can plug the disk to see if that recognises it; I am wondering if it has dynamic partitions in the disk, though I don't really understand what that is, nor what it means.

All I can suggest otherwise, unless you have data you need to restore, is that you use gparted to make a new partition table, add new partitions to the now unallocated space, and see if you can then use the disk.

---

### Post by PoopBaron on 2013-06-22
I would add a new partition but the entire volume is recognized as unallocated space.  There are no flags, and I don't have a windows partition or volume.  I am extracting files using photorec but all I am getting are gpg files.  I guess that means the drive must be encrypted?  How would I even begin the process of decrypting without a key-pair?

---

### Post by ajgreeny on 2013-06-22
Sorry; I've never used encryption so can not help you with that, nor even tell you if it is possible to get your files, but with no key, I presume it will be difficult, if not impossible.

---

