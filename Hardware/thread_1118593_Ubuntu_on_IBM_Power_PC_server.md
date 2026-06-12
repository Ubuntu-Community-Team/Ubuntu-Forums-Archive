---
title: "Ubuntu on IBM Power PC server ???"
date: 2009-04-07
forum: Hardware
---

### Post by avatar21 on 2009-04-07
I wonder anyone ask this before ...
 
Do Ubuntu support following hardware specifications?
Q1) Hardware?
A1) IBM RS/6000 7025 F50 (with IBM PowerPC 604e 332 MHz processor)
Q2) Brand? 
A2) IBM
Q3) Model?
A3) IBM RS/6000
Q4) Explanation?
A4) try to install, some how did not boot into Live CD (hang on the broken OS)
 
As I see there's only a 32-bit x86 binary CD image ... 
 
Any help/ advice will be highly appreciated.
 
 
Thanks & Regards,
Avatar Ng

---

### Post by henriquemeira on 2009-07-27
Hello, do you got it works?

I've an IBM 7025-F50 server and I would like to try Ubuntu in this old machine.

I found these images:

[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

I think the correct is : Mac (PowerPC) and IBM-PPC (POWER5) server install CD [[http://cdimage.ubuntu.com/ports/releases/jaunty/release/ubuntu-9.04-server-powerpc.iso]](http://cdimage.ubuntu.com/ports/releases/jaunty/release/ubuntu-9.04-server-powerpc.iso]).

Can somebody help me?

---

### Post by henriquemeira on 2009-10-17
Well, I got it! Finally!!!

A little tutorial to help who want turn on IBM RS/6000 F50 7025 with Linux.

Note: I don't got it with Ubuntu, just with Debian 4.0. Good news: after installation, you can upgrade to Lenny 5.0.


Steps:

1. Download and burn a CD from this image: [http://ftp.uni-augsburg.de/pub/tuxppc/debian-bootcds/ppc64/Debian-boot-64.iso](http://ftp.uni-augsburg.de/pub/tuxppc/debian-bootcds/ppc64/Debian-boot-64.iso)

2. Do boot from CD. Type "auto" for starting boot. 

3. Follow installation steps normally.

4. That's it! Now you have Linux. Have fun!

5. Optional: Upgrade from Etch 4.0 to Lenny 5.0. Just follow this tutorial: [http://www.debianadmin.com/howto-upgrade-from-debian-etch-40-to-lenny-50.html](http://www.debianadmin.com/howto-upgrade-from-debian-etch-40-to-lenny-50.html)

Done!

henrique.

---

### Post by JeffMGrant on 2010-02-22
Henri, when you installed Debian on your F50, did it have SMP support only use one of the 604e cpus?  Mine has 4 604e cpus but will only see 1 of them with SUSE.  My plan was to install Ubuntu, but that failed, so now I'm willing to try Debian, but only if it has SMP support.  Thanks!

Jeff

---

### Post by barbaGNU on 2010-05-06
do you have succesfully booted with that one ??

Plz, can you provide a working 604e modern kernel (2.4.32.x or newer) config?

---

### Post by OldManRiver on 2011-05-22
All,

henriquemeira replied to my post at:

[http://ubuntuforums.org/showthread.php?t=1133527&page=4](http://ubuntuforums.org/showthread.php?t=1133527&page=4)

I have the additional problem that the B50's I'm working with did not have a video card but using Null Modem Terminal cable on COM 1.

Therefore since I added the VIC and boot, my CD can not be interactive, but must find and load the video card firt before any prompts are issued.

Any suggestions on that?

Also the download recommended is 64 Bit so what about i386 or i586?

OMR

---

