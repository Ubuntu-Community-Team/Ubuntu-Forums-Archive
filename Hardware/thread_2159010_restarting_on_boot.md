---
title: "restarting on boot"
date: 2013-07-01
forum: Hardware
---

### Post by paupav on 2013-07-01
So I've installed Ubuntu on old laptop (256mb of RAM) with low resource mode (without GUI) and first boot (without GUI was fine. So when I have installed lubuntu-desktop problems started. Sometimes I get lubuntu start screen (attachment), and sometimes I just get flashing screen. I've tried NOMODESET methos ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) didn't worked.

---

### Post by sioxs on 2013-07-01
According to [lubuntu wiki]("https://wiki.ubuntu.com/Lubuntu")
> The default "Desktop" installer requires 384-800 MB of RAM (depending on  selected options.)  If you have problems, please use the "Alternate"  installer. Hope that helped
PS you can try using [openbox]("http://openbox.org/") and see how it goes

---

### Post by paupav on 2013-07-02
thanks for your reply, but I've already installed it in Low resource mode(alternate install). Problem is in boot up.

---

### Post by sudodus on 2013-07-02
It is possible to run Lubuntu with 256 MB RAM, but it is not a very nice experience. As soon as you start doing anything more than just running the operating system, it starts swapping to disk and get very slow (providing you have a swap partition and have enabled it, otherwise it crashes). If you 'hard reboot' when it crashes, it might cause corruption of the file system.

You can check and repair it. Run

```
fdisk -lu
``` and

```
cat /etc/fstab
```

to help find out which partition is the root partition. Then boot from a live disk, and run this command (the partition should be unmounted).

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter (typically a for the first drive) and y is the partition number (typically 1 for the first partition and 5 or 6 for a logical partition).


It is also important that you have enough horsepower in the CPU.

Please have a look at the first post of this thread [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

-o-

The next version, 13.10 'Saucy' is only in alpha stage and will break several times until it will be released in October. But it comes with zRAM, a method to swap to a compressed part of the RAM, and it seems it will make Lubuntu work better with low RAM computers. See this link if you want to try it.

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by paupav on 2013-07-02
i'll try older version of lubuntu. It's processor is celeron 2.0 ghz (pentium 4)

---

### Post by sudodus on 2013-07-02
Yes, with that processor and low RAM, you need a version and flavour with a small foot-print. Lubuntu 12.04 get updates till October, when 13.10 will be released. There are also 12.10 and 13.04.

You can also run the Openbox session (selected at the boot screen). That is only a window manager, no desktop environment with a panel etc. Right-click on the gray background and select terminal window to run 'all' tasks, or select the web browser. This way you will need as little memory as possible  for eye-candy, and have the most for application program.

But I suggest that you get used to Lubuntu in the regular Lubuntu session before using Openbox.

Good luck :-)

---

### Post by paupav on 2013-07-02
It seems like I get that problem with every Debian based OS's. I have tried lubuntu, wattOS microwat, slax. I get same problem with all of them. So far only puppy linux worked.

---

### Post by sudodus on 2013-07-02
Puppy and Knoppix are good choices for such old hardware and low memory. So if you are reasonably happy with Puppy and install persistence, it might be the second best alternative :-)

The best best alternative is to get more RAM (at least the double amount, 512 MB). It should be possible to get used RAM from another old computer, that is no longer used.

---

### Post by paupav on 2013-07-02
So I've tried pure debian 7 LXDE and it works :O ... also i really don't like puppy linux it is so unintuitive

---

### Post by sudodus on 2013-07-02
I'm glad you are happy with debian 7 LXDE :-)

Try Knoppix too (it is built from debian) and has good drivers for old hardware and a good set of application programs. Knoppix is not intended to be installed, only run live or live with persistence, "poor man's install" in Knoppix language.

---

