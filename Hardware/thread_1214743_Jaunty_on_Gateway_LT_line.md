---
title: "Jaunty on Gateway LT line?"
date: 2009-07-16
forum: Hardware
---

### Post by Bateluer on 2009-07-16
I'm looking at getting one of Gateway's new LT3114u netbooks. For the price, they look much better than any other netbook on the market. 

Downside is, it comes with Vista Home Basic only. While I haven't had any major problems with Vista, I would like the option to run Ubuntu effectively. 

I searched the forum and didn't see hits on it. Its a recent model, so I'm not sure how many people have bought them yet.

---

### Post by Bateluer on 2009-07-16
I guess not many people have bought the Gateway LT series yet.

---

### Post by ELoXL on 2009-07-29
Hey whats going on folks.  I'm within my first year of still using a Linux distro, but I do have under my finger tips at the moment a Gateway LT series netbook.  I really do enjoy and I am not a fan either of Vista,but it does what its suppose to without any issues..........well............I have to load Win Vista SP2 twice due to a hang up when I installed it the first time.  

Anyways back Ubuntu.  I attempted to run Jaunty via a thumb drive and everything came up just fine.  The multi-touch mouse pad worked right out the box, but the only thing that didn't was the wi-fi adapter.  I left a review on CNet, **[http://tinyurl.com/mgsll9](http://tinyurl.com/mgsll9) , **and made the same claim that wi-fi didn't work with Jaunty on this netbook.  Someone left me a reply and recommended me to check out linuxwireless.org .  Went to the site and it appears to have a chock full of great info, but haven't downloaded any drivers yet to see if it will work.  Anyways check out the review on CNet, and there appears to be another individual leaving his own experience about the netbook as well.  Later

---

### Post by diffy on 2009-08-02
hi

for me everthing works good except the cpu frequency scaling, my cpu is always at his max speed. With that issue, i can run 3-4 hours on the battery.
Otherwise no problems with the wifi.
A another problem, there is an issue with the alsa driver and the build in micrphone doesn't work. it seems that some people have resolved the problem by installing the last version of alsa, for me it didn't work, now my sound card is not detected with the new alsa driver...

david

---

### Post by ROMEMA on 2009-08-04
for the wireless issue. linux-backports-modules-2.6.28-13-generic package might solve it. :)

---

### Post by ELoXL on 2009-08-20
Thx ROMEMA

I looked up the backport issue sometime last week and came across this nice command sudo apt-get install linux-backports-modules-jaunty .  It worked like a charm with the desktop version, but when I tried to take a stab at running UNR on it the wifi issue reared its ugly head.  Unfortunately that same sudo command I just mentioned doesn't work with UNR.  Any suggestions guys; I figured UNR and the desktop version were one in the same?

---

### Post by brhokla on 2009-08-21
I have the Gateway LT netbook and I love the little computer.  As a matter of fact, I have had zero problems running anything I need with it other than Ubuntu  Actually, Ubuntu works great on it but I can't get the wifi to work.  Other than that it runs very smooth.  I haven't had any issues with Vista on the computer either.  Not a single problem or lockup and I have been using it nonstop now for about 5-6 weeks.

---

### Post by radparker on 2009-09-06
I just picked up an LT3114u on a whim, and can't get Jaunty to load off of a USB stick or a CD. The installer dumps me into a busybox shell after whirring for a while. I see a couple of errors on the screen above the shell prompt:
Fatal: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory.
BIOS error - no PSB or ACPI _PSS objects.

Would anybody happen to have any tips on things to do to try to troubleshoot this? Thanks.

---

### Post by aaroncouch on 2009-09-07
I just bought a LT3103u and love this little lappy.

I had trouble installing ubuntu from the usb drive.  I ended up using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) . The first time I tried with 9.04 distro but got stuck with the same problem described above by radparker. The second time I tried with 8..10 I was successful.

The wirless does not work which is my next major obstacle.  If I am successful in that I will post my results here.

---

### Post by aaroncouch on 2009-09-07
success!!!!

i was able to get the wireless working with advice found here:

[http://reviews.cnet.com/laptops/gateway-lt3103u/4864-3121_7-33721171-1.html?tag=mncol;uo](http://reviews.cnet.com/laptops/gateway-lt3103u/4864-3121_7-33721171-1.html?tag=mncol;uo)

"Open your "terminal" and type: sudo apt-get install linux-backports-modules-jaunty "

once i restarted the computer the wireless worked right away!

---

### Post by fifthecho on 2009-09-10
Got wireless working, but I can't get Compiz (Desktop Effects) running.

Installed the ATI Radeon driver from APT and when X starts, I get a really funky, corrupted looking video working.

Anyone gotten Desktop Effects working on the LT3103U yet?

---

### Post by AutoStatic on 2009-09-15
I got them working with the open source Radeon driver. Worked out of the box.

---

### Post by flexgrip on 2009-09-20
My mom bought a Gateway lt3114u from Best Buy. It seems great except the vista basic that came on there needed to be removed for obvious reasons.

I made a bootable usb install from the  amd64 jaunty-alternate iso. Installed it and the only thing that didn't work was wifi. You can enable the backports repository like the others said although I just installed the needed modules.

Anyway, yeah 3d accel for the ati card that is in here worked out of the box. I am testing it now to see if it is worth keeping since we have 14 days to return it. Want to make sure it is quick enough to play h264 video through a flash player but yeah, it is much quicker with x64 jaunty.

---

### Post by AutoStatic on 2009-09-20
> **flexgrip said:**
> Anyway, yeah 3d accel for the ati card that is in here worked out of the box. I am testing it now to see if it is worth keeping since we have 14 days to return it. Want to make sure it is quick enough to play h264 video through a flash player but yeah, it is much quicker with x64 jaunty.Choppy playback according to this article: [http://www.netbooktech.com/2009/07/10/gateway-lt3103u-review/](http://www.netbooktech.com/2009/07/10/gateway-lt3103u-review/)

---

### Post by matbonucci on 2009-10-01
> **radparker said:**
> I just picked up an LT3114u on a whim, and can't get Jaunty to load off of a USB stick or a CD. The installer dumps me into a busybox shell after whirring for a while. I see a couple of errors on the screen above the shell prompt:
Fatal: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory.
BIOS error - no PSB or ACPI _PSS objects.

Would anybody happen to have any tips on things to do to try to troubleshoot this? Thanks.
yeap there is.... install ubuntu 8.04 it will give you the error message but will boot anyway and then you can upgrade to the actual ubuntu version, i did it

---

### Post by AutoStatic on 2009-10-02
9.04 Jaunty Jackalope installs just fine.
Just don't use the normal CD image, use the alternate image to create a bootable USB stick and then it will install just fine.
Installing 8.04 on this machine is not the way to solve issues like this, besides, when running 8.04 you will be devoid of a lot of functionality!

---

