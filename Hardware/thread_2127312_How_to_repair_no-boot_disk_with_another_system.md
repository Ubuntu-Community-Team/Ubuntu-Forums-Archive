---
title: "How to repair no-boot disk with another system"
date: 2013-03-19
forum: Hardware
---

### Post by coolecho on 2013-03-19
Hello,

I have an Ubuntu 12.04 system that doesn't come up all the way. It just pauses in middle of boot with the Ubuntu background color. Can I possibly repair this by placing the sata drive from it into another system (Ubuntu 10.04) and run a file system check on it?

Thanks,

---

### Post by papibe on 2013-03-19
Hi coolecho.

The easiest way would be to use the Ubuntu installation media as a LIVE CD/USB, and make the repairs there.

Let us know if you need more help with that.
Regards.

---

### Post by coolecho on 2013-03-20
OK great. I've read somewhere about repair options from the live CD. I will give it a try. Thanks.

---

### Post by coolecho on 2013-03-21
Hello,

The boot repair did not work. It still just sits forever with the Ubuntu color and never comes up. I did try the boot repair. I tried to boot the CD, and select try ubuntu. I then inserted a USB stick to try to backup stuff in home folder. I launched nautilus as root and browsed to where the old home folder is and it's empty. I guess there's a permission problem. can the drive be temporarily installed into another Ubuntu system and retreive the files that way?

Thanks,

---

### Post by papibe on 2013-03-21
If you separated /home on its own partition, you may be looking into a the wrong disk or partition.

If you have a relative modern Nvidia card, it may a graphic issue that could be fix by setting special boot options (read [here]("http://askubuntu.com/questions/140640/nvidia-drivers-and-kernel-update-problems-nomodeset")).

Let us know how it goes.
Regards.

---

### Post by coolecho on 2013-03-21
Hi,

Yes it was in a separate partition. There was only a few downloaded packages in there which I can re-download. I am re-installing Ubuntu 12.04 since I'm short on time. If there's a blog on how to recover data off partitions by putting the drive into another Ununtu system I'd appreciate it if you could let me know.

Thanks

---

### Post by papibe on 2013-03-21
From another Linux it is pretty simple. 

Connect the drive, boot normally, then open nautilus and go to 'Computer'. The available partitions will be available, and can be mounted double clicking on them.

Let us know how it goes.
Regards.

---

### Post by coolecho on 2013-03-21
Wow I reinstalled Ubuntu 12.04 to fix the incomplete boot issue, and now it has a very bad desktop with the taskbar in the middle of the screen. Can't access any icons either! I have a MSI 990FXA-GD80V2 AM3+ AMD 990FX, and a MSI R6450-MD1GD3/LP Radeon HD 6450 Video. This system worked great with Ubuntu 12.04 for about 2 months.

Update: It turned out to be the ACER monitor. I put a Samsung monitor on and it works OK.

---

