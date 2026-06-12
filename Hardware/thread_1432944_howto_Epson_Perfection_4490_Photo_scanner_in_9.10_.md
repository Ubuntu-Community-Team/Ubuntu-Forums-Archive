---
title: "howto: Epson Perfection 4490 Photo scanner in 9.10 64-bit"
date: 2010-03-18
forum: Hardware
---

### Post by dreville on 2010-03-18
Just wanted to share how I set the Epson Perfection 4490 Photo scanner in Ubuntu 9.10 Karmic Koala 64-bit

```
# uname -a
Linux absinthe 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
```

```
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

Went to SANE: [http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl)
Searched for Epson 4490.

Gave me a link to an external backend: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Fill out the 'survey' at the bottom to get the proper drive page: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

Downloaded the two deb files under 'DEB 64bit package [libltdl7] (for Ubuntu 8.10 or later)' namely:
iscan_2.24.0-4.ltdl7_amd64.deb
iscan-plugin-gt-x750_2.1.0-5_amd64.deb
(I actually downloaded all the files, I thought I would have to test each one.)

I installed the newest sane package
```
sudo aptitude install sane
```

I also installed xsane (but haven't tested, I used iscan instead)
```
sudo aptitude install xsane
```

I installed the 2 DEBs
```
sudo dpkg --install iscan_2.24.0-4.ltdl7_amd64.deb
```
```
sudo dpkg --install iscan-plugin-gt-x750_2.1.0-5_amd64.deb
```

Plug-in the usb and turn on the scanner if you haven't.

I ran:
```
sane-find-scanner
```
```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

So, the scanner was detected. I ran 'iscan' but it gave me an error
'could not send command to scanner

So I ran:
```
scanimage -L
```

The scanner made some noises. Once that once done, ran 'iscan' again. Window popped up and scanned a few images. Everything seems to work. 

The START button also works, which is for quick scanning several documents, assigns numerical suffixes to the default name for every scan. (if you check the box that says enable Start button)

Finally, I powered off the scanner, unplugged the usb, then plugged it back in, turned on the scanner. Ran 'iscan' and it still works. Ubuntu rocks! :p

---

### Post by Blue DaNoob on 2010-04-08
Thanks for pointing me to [www.avasys.jp]("http://www.avasys.jp")!

I download the 2 deb files - iscan and the plugin, ran them, and I was scanning docs in minutes! gracias!! Not as robust as the epson scan software on the mac, but excellent for office tasks. Lets me scan as JPGs, PNGs, PDFs and more.

---

### Post by dreville on 2010-04-08
> **Blue DaNoob said:**
> Thanks for pointing me to [www.avasys.jp]("http://www.avasys.jp")!

I download the 2 deb files - iscan and the plugin, ran them, and I was scanning docs in minutes! gracias!! Not as robust as the epson scan software on the mac, but excellent for office tasks. Lets me scan as JPGs, PNGs, PDFs and more.

Awesome! Glad I was able to help you out! I only scan from to time and it's been more than enough for me.

I have a Mac too and definitely the epson scan software has way more features. I have had trouble with epson mac software for printers. But anyway that's a different story.

---

### Post by carlb on 2010-04-28
For those looking for the Epson Scanner software, you can now find it on the Synaptic Package Manager.  Search for Iscan.  You must install both the application and the plugin.  Sane is also a prerequisite but the package manager should handle that for you.  I installed the 64 bit version so it is functional.

---

### Post by gfixler on 2010-07-05
It seems like none of this works anymore. I have found at least a dozen pages on how to get an Epson scanner working, and this is by far the most recent (4 months old) and the most targeted to me (9.10 64-bit here), yet it fails out pretty quickly.

I can get to the driver.pl link and see the Epkowa link, but while that links to the [http://www.avasys.jp/english/linux_e/](http://www.avasys.jp/english/linux_e/) URL, it instantly redirects to [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/), which is just the current Linux driver page that doesn't help me.

I put in my 3170's info, and it takes me to only some RPMs, and no 64-bit links. Searching their site with the search box for any of the things anyone's mentioned in any how-to online also brings up nothing. Did they *just* lock it down in the last couple of months? I think not, because I've tried to follow how-tos online here and there over the past few years, and I always come up short. There's always a brick wall at some point.

I can download the rpms, but I can't alien them into 64-bit debs, and I don't have a 32-bit machine.

---

### Post by xstine on 2011-08-25
i am running ubuntu 11, and this took care of my issue with my epson 4490- it took me and a linux-master guru to make it work, but thank you for your help!
new-buntu geek-in-training

---

### Post by dreville on 2011-08-25
> **xstine said:**
> i am running ubuntu 11, and this took care of my issue with my epson 4490- it took me and a linux-master guru to make it work, but thank you for your help!
new-buntu geek-in-training

Glad that this post still helps!

I actually just recently plugged in the same scanner on a new machine running 64-bit Ubuntu 11.04, and it just worked after I installed a scanner tool called simple-scan ('sudo apt-get install simple-scan', although I really like to use 'sudo aptitude install simple-scan' but you have to 'sudo apt-get install aptitude' first)

Worked right away if I remember correctly, no additional steps.

Ubuntu has the best forum community! You'll get all the help you need right here. :guitar:

---

### Post by Lloydb39 on 2012-07-08
Well, it was all helpful but didn't work for me. I have the 4490 running plugged into a Dell running Ubuntu 11.10. I got SANE and iscan installed and SANE sees the scanner but neither Simple Scan nor Iscan can find it.... (Yes, it is plugged in, turned on and working.)

---

### Post by dreville on 2012-07-08
> **Lloydb39 said:**
> Well, it was all helpful but didn't work for me. I have the 4490 running plugged into a Dell running Ubuntu 11.10. I got SANE and iscan installed and SANE sees the scanner but neither Simple Scan nor Iscan can find it.... (Yes, it is plugged in, turned on and working.)

This post was a while ago and was for Ubuntu 9.10. Ubuntu 11.10 should just recognize it. Just install a scanning tool.

---

### Post by Lloydb39 on 2012-07-08
> **dreville said:**
> This post was a while ago and was for Ubuntu 9.10. Ubuntu 11.10 should just recognize it. Just install a scanning tool.
I have simple scan and iscan and neither one of them can find it. Spent all morning trying to get it going but no luck. SANE sees and identifies it, but that's as far as I can get. I did your scanimage thing and it didn't budge my scanner.

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

