---
title: "TROUBLESHOOTING: If system boots only into memtest... (Karmic Installation)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by fcn on 2009-11-08
Yesterday I tried to install Karmic from another partition using [this instructions]("https://help.ubuntu.com/community/Installation/FromLinux"). After installation finished and reboot, it suddenly started memtest. I didn't understand why, and I didn't know much about new GRUB. I was really scared :) I have to thank to  drs305 from #grub channel on irc://freenode.net for their help.

Now, If you stuck there too, remember the first rule: Be cool, we'll fix it.

* Press ESC to exit memtest.
* After BIOS screen, keep SHIFT key pressed. GRUB menu should be there. If you can see the appropriate entry to boot, try it. It may work.
* In my situation, there were only two entries and both were memtest. So there was not any appropriate choice. So I pressed c for a GRUB2 command line. There should come the GRUB shell.

```
sh:grub> _
```Perhaps I should talk about my partitions right now. 

```
/dev/sda1 : Primary, VFAT.
/dev/sda3 : Primary, ext3. My installation disk area (~760MB)
/dev/sda2 : Extended
   |__ /dev/sda5 : swap.
   |__ /dev/sda6 : ext4. My main installation area (20GB)
```If you don't remember your partitions, this may help you have an idea about them:

```
sh:grub> ls
```My problem was that: linux-image-2.4.31-14-generic package did not installed properly. Because of this, there was not a vmlinuz kernel in /boot directory, and because of there was not a kernel file, grub-install couldn't add anything to list. Now what can I do? I tried to boot into my new disk using casper kernel, to reinstall linux-image-2.4.31-14-generic to solve problem.

```
sh:grub> set root=(hd0,3)            REMEMBER: /dev/sda3 was hd0,2 in GRUB but this changed in GRUB2. Now it is hd0,3 for sda3.
sh:grub> linux /casper/vmlinuz root=/dev/sda6 rw
sh:grub> initrd /casper/initrd.lz
sh:grub> boot
```Now it should boot into your newly installed system using LiveCD's kernel. From now on, there is no much things to do left. First open a terminal and then:

```
fcn@ubuntu-laptop:~$ sudo apt-get clean
fcn@ubuntu-laptop:~$ sudo apt-get update
fcn@ubuntu-laptop:~$ sudo apt-get install --reinstall linux-image-2.4.31-14-generic
```After installing new kernel, you must reconfigure your GRUB2. So:

```
fcn@ubuntu-laptop:~$ grub-install /dev/sda
fcn@ubuntu-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
fcn@ubuntu-laptop:~$ sudo shutdown -r now
```Have a good day with your new Karmic :)

---

### Post by andrewkk on 2009-11-10
Any idea why this happens? Is there a bug report for it on Launchpad?

---

### Post by Xnyper on 2009-12-05
Thanks, worked like a charm!

Also, I believe that
```
$ sudo apt-get install --reinstall linux-image-2.**4**.31-14-generic
```
should be
```
$ sudo apt-get install --reinstall linux-image-2.**6**.31-14-generic
```

---

### Post by aextance on 2009-12-07
Oh yes! Thanks so much FCN! I've been struggling with this all day, and my work has suffered accordingly. I was trying to do a clean install of Karmic, but I have no CD burner. The odd thing was, after the first attempt GRUB2 kept all of my legacy kernels, but not Koala. 

I think if I'd have tried this method at that point I would have quite a straightforward import of my data, but now I've basically wiped everything and will have to reimport from backups. At least its working now though!

While it's nicer to have a startup straight from GRUB2 rather than going through GRUB, and I'm excited to have actually got a clean Karmic install, frustratingly, it doesn't appear to have solved the minor problem that I undertook all this rigmarole to sort out (which you can find out about at the link below).

[http://ubuntuforums.org/showthread.php?p=8422246](http://ubuntuforums.org/showthread.php?p=8422246)

---

### Post by presence1960 on 2009-12-07
Did you notice instruction # 9?

**_9. Reboot and keep those fingers crossed. _**

Right there that tells me there is likely to be some sort of problem with using that method. But if you aren't able to boot a CD/USB you may have no other choice.

---

### Post by sgiandubh on 2009-12-14
Thank you, fcn! Your solution worked for me.

---

