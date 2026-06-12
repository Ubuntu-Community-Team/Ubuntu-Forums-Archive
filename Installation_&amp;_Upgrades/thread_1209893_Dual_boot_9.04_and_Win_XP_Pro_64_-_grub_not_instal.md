---
title: "Dual boot 9.04 and Win XP Pro 64 - grub not installed"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by svenskmand on 2009-07-10
Hey everybody,

I just installed Win Xp pro 64 on my new machine and then wanted to install Ubuntu 9.04 64 bit in dual boot - as I have done so many times before with win xp home 32 and Ubuntu - but this time after the install was complete and grub was about to be installed I got the error that grub could not be installed to hd0.

When I installed Ubuntu I chose manual install - as I use to do - to make a ext3 partition (located first on the free space) mounted at / and a swap partition (located last on the free space).

I have searched these forums and the net and tried various guides e.g. [this]("http://ubuntuforums.org/archive/index.php/t-24113.html") and [this]("http://ubuntuforums.org/showthread.php?t=224351") but with no luck :(.

Anybody have some ideas? Is because I installed win xp pro 64 instead of the usual win xp home 32, or what? I don not get it :(

---

### Post by merlinus on 2009-07-10
Why not install 9.04 64-bit?

---

### Post by svenskmand on 2009-07-10
> **merlinus said:**
> Why not install 9.04 64-bit?

I did (my mistake that I did not write it :) ) The above post is now edited :)

---

### Post by merlinus on 2009-07-10
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by svenskmand on 2009-07-10
As grub is not installed I am not able to boot Ubuntu so I cannot do what you ask. But when booting the live cd I can perform the first command which gives
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c154c15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       97906   786429913+   7  HPFS/NTFS
/dev/sda2           97907      175874   626277960    7  HPFS/NTFS
/dev/sda3          175875      182401    52428127+   5  Extended
/dev/sda5          175875      176384     4096543+  82  Linux swap / Solaris
/dev/sda6          176385      182401    48331521   83  Linux
ubuntu@ubuntu:~$

```

the second command cannot be run from the live cd.

As you can see my layout is
```

--------------------------------------
| Windows | Documents | Swap | Linux |
--------------------------------------

```

---

### Post by merlinus on 2009-07-10
You should be able to mount your ubuntu partition by clicking on it in nautilus.

If so, then you can try to install grub:

```
sudo grub
root (hd0,5)
setup (hd0)
quit
```

and restart to see if the menu comes up.

---

### Post by svenskmand on 2009-07-10
Ahh, ok. I can see that the file does not exist :(, that is I mounted /media/disk (my ubuntu partition), and here /media/disk/boot/grub/menu.lst does not exist :(

---

### Post by svenskmand on 2009-07-10
ok, this goes wrong here
```
sudo grub
root (hd0,5)

```
I get
```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,5)
root (hd0,5)

Error 18: Selected cylinder exceeds maximum supported by BIOS
grub>

```
I do not get this last part, I can see the whole disk in my BIOS and in windows, so that error 18 is a little misleading.

---

### Post by merlinus on 2009-07-10
Info on grub error 18 and possible workarounds on this page:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

Scroll down about 3/4.

---

### Post by svenskmand on 2009-07-10
I have a Asus M4N82 Deluxe motherboard, and it should should support 1.5 TB disks (I can see it correctly in the BIOS and in windows), don't you agree?

As I can see from you [[COLOR="Red"]link[/COLOR]]("http://members.iinet.net.au/~herman546/p15.html") I should make a special boot partition with mount-point /boot right? But it appears to me that the error only occurs with legacy hardware, and I have just bought this system :S, or what?

I wil give it a try, using the Super Grub Disk mentioned in you link.

---

### Post by merlinus on 2009-07-10
In theory, it should work fine.  But since it is not, it might not hurt to try the separate /boot partition.

You also might try mounting your ubuntu partition again, and trying:

```
sudo grub-install --root-directory=/media/disk 
```Another option is to try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

