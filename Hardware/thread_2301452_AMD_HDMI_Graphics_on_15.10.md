---
title: "AMD HDMI Graphics on 15.10"
date: 2015-11-02
forum: Hardware
---

### Post by dldeskins on 2015-11-02
I update my system on a old computer that I am using as a media center to view online videos. The computer has built-in graphics... Radeon HD 6530D and is hooked HDMI to a 52" LG TV.  After removing the AMD proprietary drivers, I was able to get a nice picture and sound (although the software recognized the TV as a 72").  I thought that I had it, but after switching over to cable and then back (sometime later), I had no picture (no HDMI source).  After doing research online and try several things (including adjustments to Light Locker settings, installing xdm, etc), I found no solution.  

To get my picture back, without rebooting, I found that I could restart lightdm (ssh into the box)

```
sudo service lightdm restart
```

AMD has not updated their driver for 15.10.

Does anyone have a solution for this? (I don't want to install the full Gnome desktop, which I understand works).

Thanks

---

### Post by Bashing-om on 2015-11-02
dldeskins; Hello;

To this time the proprietary driver is broke in 15.10 . There are some work-a-rounds if you have the will and experience to implement.
It is expected that the fix will make it's way into the 15.10 repository, in due time after testing is completed in upstream.
see:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)
[http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588](http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588) <- work-a-round
[http://ubuntuforums.org/showthread.php?t=2300920&highlight=FGLRX](http://ubuntuforums.org/showthread.php?t=2300920&highlight=FGLRX)
[http://ubuntuforums.org/showthread.php?t=2299981&highlight=FGLRX](http://ubuntuforums.org/showthread.php?t=2299981&highlight=FGLRX)


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by dldeskins on 2015-11-02
Well, I thought that I had looked thoroughly but evidently not.

I appreciate you answer so quickly and yes, this did solve my problem.  I had to modify instructions a bit... 
1. I had to use dpkg to install the deb files
2. I had to install 3 packages before the first would install
3. The 2nd package was dependent on the 3rd, so I had to install out of order

Again, thank you!

---

### Post by Bashing-om on 2015-11-02
dldeskins; Great .

You do good work.

I am interested in knowing how the patch turns out when the fixed driver hits the 15.10 repo .
Maybe more fixing ?

[INDENT][INDENT]we will know
[INDENT][INDENT][INDENT]in the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

