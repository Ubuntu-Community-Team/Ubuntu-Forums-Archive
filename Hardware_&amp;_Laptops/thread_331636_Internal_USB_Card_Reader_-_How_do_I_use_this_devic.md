---
title: "Internal USB Card Reader - How do I use this device?"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by reichelberger on 2007-01-04
Hello,

I have a PCUSA model CR-IN12XU-1 3.5" Internal Card Reader with USB.  This is a 13-1 card reader.  It worked in Windows XP Pro, then when I installed Ubuntu Dapper I could not use it.  I have since upgraded to Edgy and still cannot use the device.

](*,)

The USB port works for jump drives, but the SD Memory Card slot does not.  I am at my wits end trying to figure this out.  Any assistance would be helpful.

Note:  I hope to perform a clean install of Kubuntu Edgy in the near future.  Amongst other things I want to repartition my drive and add a new drive.

The following is my /etc/mtab:
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

The following is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=c9cc30f4-530c-4858-abfa-e785ac468bca / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=0b0133af-ea28-4460-bcb1-73d3cea02039 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Any help would be greatly appreciated!

Thanks!
Rick

---

### Post by WirelessMike on 2007-02-16
I'm experiencing the exact same issue.  Furthermore--  I can confirm that my [Linkskey internal usb card reader]("http://www.linkskey.com/detail.php?Productid=167&ProductName=LKA-CR15B") worked up through some kernel "upgrade" in dapper, after which, it is no longer detected.  As you observed, the attached usb terminal on the interface still functions perfectly, but the latest (k)ubuntu kernels fail at mounting cards.

To confirm the hardware works, I can mount cards in WinXP Pro with no problems.

Perhaps the issue will be resolved with the upcoming Feisty Fawn?  I'm a little disappointed it was never addressed in Etchy, so I'm not very optimistic.

Unfortunately, I can offer no fix for this (outside of installing Debian, instead, which my friend can confirm works fine).  At least I can confirm that you are not the only one with this issue.

---

### Post by WirelessMike on 2007-03-07
If you're on Edgy, perform an upgrade (there is a recent kernel upgrade).  Mine just started working again afterwards.

---

### Post by reichelberger on 2007-03-08
Thanks Mike!
 
Can you tell me what version of the kernal you now have?   I will try this tonight.
 
I have a system that started as a Dapper install of Ubuntu.  I then upgraded to Edgy.  I have since upgraded to kubuntu, but am still on Edgy (I prefer the KDE environment to Gnome).
 
I plan to do a clean install when Fiesty Fawn is released, is Feisty likely to have the new kernal as well?
 
Thanks,
Rick

---

### Post by WirelessMike on 2007-03-13
Sorry...

I have an update and bad news.  For a few days, it worked.  I did (as I usually do in my ignorance) a couple updates since the kernel (-11) update and now it doesn't work again.

Just like before, it works perfectly in Windows, but now not in Kubuntu...  again...

I'm sorry, but my experience with this so far does not lead me to believe that the issue will be resolved in Feisty.

---

