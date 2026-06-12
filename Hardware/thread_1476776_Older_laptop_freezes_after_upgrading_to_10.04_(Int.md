---
title: "Older laptop freezes after upgrading to 10.04 (Intel video issue)"
date: 2010-05-08
forum: Hardware
---

### Post by Mike BFD on 2010-05-08
There's probably more about the problem in this forum, seems like I saw something of the sort, just couldn't find "a very same case".

On an old Asus A3N laptop, I could start Karmic only with older kernel (2.6.28-18.) and rolled-back video driver (that well-known xserver-xorg-video-intel-2.4), otherwise the system froze on boot (Ubuntu logo -> black screen, only "brutal hard shutdown" possible)
After upgrading to Lucid beta1, everything worked OK (probably no changes were made to video driver/kernel used - or the changes made were "positive"). Same with beta2 and rc, respectively.

However, after the final release I decided to make a "brand-new" installation - ant that was a fatal mistake: the black screen freeze on boot is back.
Installing Karmic and network update doesn't help, either: when updating, Lucid wipes ver2.4 intel driver with no option to keep it.
In Lucid, a "driver rollback" is impossible: when I try to do it, an error message appears:
```
The following packages have unmet dependencies:
  xserver-xorg-video-intel-2.4: Depends: xserver-xorg-core (>= 2:1.5.99.901) but it is not going to be installed
E: Broken packages
```Well, of course I do have xserver-xorg-core installed (version 2:1.7.6-2 which looks "=>" than 2:1.5.99.901) but...

Please does anybody know a working solution? Now it's possible to boot only in failsafe mode which is pretty "minimalistic" (even a dock or Avant window navigator don't look/work properly).

Would highly appreciate any good advice!

---

### Post by mikewhatever on 2010-05-08
Probably related to this [http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

---

### Post by Mike BFD on 2010-05-08
> **mikewhatever said:**
> Probably related to this [http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)
Thanks but...

Well, "Workaround F" is just my case as I have exactly
```
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
```

I followed the instructions carefully - with no result.
It tries to boot, lets me log in, then - flickering for a minute and message "Ubuntu is running in low-graphics mode".
In fact, it's the same "failsafe" mode I turned on manually without doing anything...

Any further ideas folks?..

---

### Post by mikewhatever on 2010-05-08
Does it say Workaround F works 100%? No. On the other hand:
> Switching to -vesa has been found to 100% stop the freezes. However, this regresses a lot of functionality: No 3D hw acceleration, no accelerated video, no HD resolutions, poor external monitor support. Probably other issues too.



---

### Post by Mike BFD on 2010-05-08
> **mikewhatever said:**
> Does it say Workaround F works 100%? No.
It says,
"This way X now works flawlessly without any crashes  at least for those with:
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)"
(c)
I'm definitely "one of those with..."
[SIZE=2]
[/SIZE][SIZE=2]However, I'm not complaining but just informing))[/SIZE]

To enable vesa driver, is it enough to modify xorg.conf like
Section "Device"
    Identifier    "Configured Video Device"
            Driver          "vesa"
EndSection
???

---

### Post by dino99 on 2010-05-08
[http://ubuntuforums.org/showthread.php?t=1470685&page=2](http://ubuntuforums.org/showthread.php?t=1470685&page=2)

look at #11 (same config as yours), #12 for solutions

---

### Post by Mike BFD on 2010-05-08
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1470685&page=2](http://ubuntuforums.org/showthread.php?t=1470685&page=2)

look at #11 (same config as yours), #12 for solutions
Thank you.

Results:

- An error message
```

sudo install xserver-xorg-video-intel
install: missing destination file operand after `xserver-xorg-video-intel'
```

- Installing a new kernel (2.6.33) - no visible changes, everything is as it was

---

### Post by Mike BFD on 2010-05-09
Please does anybody know where to check if the developers team is going  to repair this? Maybe there's a bug report with some "official  comments"?..

---

### Post by octavsly on 2010-05-26
> **Mike BFD said:**
> Please does anybody know where to check if the developers team is going  to repair this? Maybe there's a bug report with some "official  comments"?..

I have exactly the same Intel chipset. I have solved the freeze by using a newer kernel.

To upgrade the kernel do the following (32 bit):
```

wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb

```

This is solution #16 from [http://ubuntuforums.org/showthread.php?t=1470685&page=2](http://ubuntuforums.org/showthread.php?t=1470685&page=2)

Of course, you need to boot into a failsafe mode. To achieve this press escape in GRUB menu (before booting) then select a failsafe kernel mode then terminal+network)

---

