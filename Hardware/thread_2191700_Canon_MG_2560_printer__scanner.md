---
title: "Canon MG 2560 printer / scanner"
date: 2013-12-04
forum: Hardware
---

### Post by june-y on 2013-12-04
Hello people,

I have purchased a Canon All in one printer and scanner. MG 2560...

It works well when it prints, howeve I have downloaded and installed the drivers for Linux from Canon and I cant get the scanner to work. XSane does not see it and when I used Sudo sane-find-scanner it returned this result

  	 	 	 	   [B]# sane-find-scanner will now attempt to detect your scanner. If the
[/B]
**  # result is different from what you expected, first make sure your**
**  # scanner is powered up and properly connected to your computer.**
**  # No SCSI scanners found. If you expected something different, make sure that**
**  # you have loaded a kernel SCSI driver for your SCSI adapter.**
**found USB scanner (vendor=0x04a9 [Canon], product=0x176d [MG2500 series]) at libusb:001:008**
**  # Your USB scanner was (probably) detected. It may or may not be supported by**
**  # SANE. Try scanimage -L and read the backend's manpage.**
**  # Not checking for parallel port scanners.**
**  # Most Scanners connected to the parallel port or other proprietary ports**
[B]  # can't be detected by this program.


[/B]I dont know what else to do. I have been working on this issue for 2 hours now with no result. I plug it into Windows 7 and it works within minutes when the drivers are installed howeve Ubuntu is letting me down again.

What do I need to do in order for this to work I dont want to have to go back to Windows 7, and Im reluctant to use Ubuntu all the time when issues like this arise and no one can sort it out.

Thanx for your help in advance.

June

---

### Post by mörgæs on 2013-12-04
A golden rule is always to use software newer than the hardware. If you read the system requirements on the Canon [web site]("http://support-au.canon.com.au/P/search?model=PIXMA+MG2560&menu=download&filter=0&tagname=g_os&g_os=Linux") you will notice that the drivers are validated for 13.04. 

I would suggest that you begin with a fresh install of 13.10.

---

