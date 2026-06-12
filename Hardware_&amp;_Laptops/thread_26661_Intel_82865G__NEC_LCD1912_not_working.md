---
title: "Intel 82865G / NEC LCD1912 not working"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by mariuss on 2005-04-13
Hi,

I just installed Ubuntu Hoary next to Windows XP on a DELL machine using the Intel 82865G Graphics Controller and a NEC LCD1912 monitor.

The only resolution supported after install is 640x480@60Hz, it is unsuable :-(

I also tried Knoppix 3.81 and it starts in the same impossible resolution.

I searched these forums for a solution, no luck so far. I run dpkg-reconfigure xserver-org several times, made no difference.

Here are some error messages from Xorg.0.log:
> mode clock 100000MHz exceeds DDC maximum 140MHz
> Not using mode "1280x1024" (no mode for this name)
both errors show up several times, for all resolution except 640x480

I checked the xorg.conf file and it seems OK. The only issue I could see is the fact that it has modes only up to 24bit depth and the video card is using 32 under Windows. But this does not seem to be the issue.

Any clues?

Thanks,
Marius

---

### Post by heimo on 2005-04-13
Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

---

### Post by mariuss on 2005-04-14
Thanks for the help.

It turned out to be a problem with the monitor, apparently it was not detected properly. In the xorg.conf file I had to add a couple of lines to the monitor section (HorizSync and VertRefresh), now it looks like:
```
Section "Monitor"
	Identifier	"NEC LCD1912"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-85
EndSection
```

---

### Post by giorg on 2005-05-19
[QUOTE=mariuss]Hi,

I just installed Ubuntu Hoary next to Windows XP on a DELL machine using the Intel 82865G Graphics Controller and a NEC LCD1912 monitor.
[/QUOTE]

I'm sorry,
but did you use any driver? As far as I know, there still is no driver for his graphic card...  ](*,) I use it with a Nec 1701 and I've got no problem going to 1280x1024, but no acceleration... I can post my xorg.conf if you need it...

---

### Post by mariuss on 2005-05-19
My understanding is that Ubuntu does have the right driver and it was installed properly in my case. My problems were just with the monitor.

Sorry, I cannot help you more than this...

Marius

---

### Post by mariuss on 2005-06-08
A friend of mine has an NEC LCD1712 and he had very similar problems with Ubuntu. He also installed Fedora Core 3 and that distro did recognize his monitor properly.

Just a note for other people having similar issues.

---

