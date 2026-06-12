---
title: "Where is lpia?"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by rockin_goliath on 2009-05-16
I am expecting a Dell Mini 9 to arrive soon, and I have heard that the lpia version provides significant savings in battery life. However, I can't find the installer image for Jaunty ANYWHERE. It does list an Intel Atom processor as a requirement for the Netbook remix; does that mean that the Ubuntu Netbook remix *includes* lpia packages and repositories?

Some insight into this would be appreciated.

---

### Post by Brandon Williams on 2009-05-16
The first place to look for information about running standard Ubuntu on the mini 9 is [here](http://www.ubuntumini.com). I suggest you do so before moving to 9.04.

Most people who switch to 9.04 run the i386 version. The UNR image installs for the i386 architecture, not lpia, and so the note about being for the lpia architecture is false, as far as I know. There might be some lpia-specific stuff built into the i386 kernel that makes it unnecessary to use the lpia build, but if so, I don't know what it is. However, it definitely is the case that you will end up with an i386 install using the UNR image.

If you want an lpia install, then you can use the lpia alternate install CD from [here](http://cdimage.ubuntu.com/ports/releases/jaunty/release/).

---

### Post by rockin_goliath on 2009-05-16
Thank you Brandon. I will try them both. I have been reading that the lpia version can be a little weird, so I might just play it safe and use the standard UNR image. Thanks again!

---

### Post by Brandon Williams on 2009-05-16
I use the lpia version of Jaunty, and I don't have any problems with "weirdness". A lot of people associate lpia with the Dell custom version, and there are those who don't like the Dell custom version, so it ends up seeming like there's a problem with lpia. In my experience, both the Dell custom version of ubuntu and the lpia Jaunty port are both solid, and they both have all the software 99% of people want.

It is true that Jaunty lpia is better than Intrepid or Hardy lpia, mostly because more third-party software sources are providing lpia version of software for Jaunty than the others.

---

### Post by snowpine on 2009-05-16
I tested both the lpia and i386 versions of Jaunty on my Dell Mini 9. Battery life was *identical* but the lpia version had a smaller repository and poor graphics performance (especially flash video, which is important to me). Overall I was disappointed with lpia and cannot recommend it for the Mini 9.

I am currently dual booting Debian and SliTaz on my Mini 9, both of which use an i386 kernel. In fact, Ubuntu is the *only* linux distro that offers an lpia kernel, which leads me to believe it is useless. ;)

---

### Post by Brandon Williams on 2009-05-17
> **snowpine said:**
> the lpia version had a smaller repository and poor graphics performance

If have not found either of these observations to be true in my experience with the lpia architecture port.

Perhaps there is some specific software that you use that is not in the lpia repository, but I have not yet encountered anything that is in the i386 repo but not in the lpia repo, which leads me to believe that 99% of users would be perfectly happy with the software available in the lpia repo. However, I'm also willing to admit that the specific software you weren't able to find might be something that is considered critical to a large group of users. It's hard to know without the specifics.

As for graphics performance and flash, I recognize that this assessment tends to be pretty subjective. You say it was bad for you with the lpia build, so I have to believe that there was an observable difference. For me, this has not been the case. I watch flash streams quite regularly and I don't observe any quality issues. I don't do much else that's graphically intensive, other than the occasional game of ppracer (which plays just fine), so my experience might be too limited.

---

### Post by snowpine on 2009-05-17
Just one man's experience with one computer, but I've tried about a dozen distros on my Mini 9, and Ubuntu lpia was the slowest.

(edit) I don't want to sound negative. Ubuntu lpia is quite usable, and I am not recommending that people *not* try it. I was just disappointed that the hyped battery and performance improvements were non-existent.

---

### Post by skiang on 2009-05-21
I've been using the Hardy lpia from Canonical (aka UNR 1.0.1) on my Mini 9 and like the way that everything works. I'm interested in upgrading to the Jaunty lpia but not at the cost of wiping the existing install. Does anyone see a way to get the Jaunty alternate lpia iso to install to a usb instead of the hard drive?

---

### Post by Brandon Williams on 2009-05-21
If you have two USB sticks, one for the installer image and one to install to, then you should be able to insert both, boot off the installer stick, and tell the installer to use the other stick as the destination. If you do this, you should get a high-quality, fast thumb-drive to install to in order to make sure that it will last as long as possible and provide a reasonably responsive desktop experience.

---

### Post by skiang on 2009-05-21
Tried that, but the installer seemed to be looking for an IDE or SCSI hard drive. When I pointed the installer at /dev/sdc, the opeation failed, apparently for lack of a driver. Any ideas?

---

### Post by skiang on 2009-05-21
To be clear, I should add that I also tried the Jaunty UNR image (on a usb drive) and found that it didn't recognize the sdhc card on which my /home partition is mounted. So while I'm definitely interested in upgrading to the Jaunty lpia, I'd like to be able to verify that everything works before kissing Hardy good-bye.

---

### Post by Brandon Williams on 2009-05-22
> **skiang said:**
> Tried that, but the installer seemed to be looking for an IDE or SCSI hard drive. When I pointed the installer at /dev/sdc, the opeation failed, apparently for lack of a driver. Any ideas?

It's possible that there's a problem with the USB stick you're trying to install to, I suppose. I have successfully installed Jaunty UNR to a USB stick using the Jaunty UNR installer from another USB stick. I haven't used the guided partition methods, though, so maybe there's an issue with those methods. Try it with manual partitioning. That's what I did and it worked just fine ... just like a regular install.

---

### Post by skiang on 2009-05-22
I might have confused the issue by mentioning that I had tried Jaunty UNR. Isn't there a difference between the UNR and lpia images in that the UNR is set up to run as a 'live CD' (without changing your system) while the lpia isn't? I don't know what's causing the error when I try to install the lpia image to a usb stick, but I'll look at it again. As I recall, the manual partitioning method was part of the solution to the problem of (lack of) persistence in the UNR install. Not sure how it would apply to the problem of getting the lpia installer to address the usb device, if that is indeed the problem.

---

### Post by snowpine on 2009-05-22
> **skiang said:**
> I might have confused the issue by mentioning that I had tried Jaunty UNR. Isn't there a difference between the UNR and lpia images in that the UNR is set up to run as a 'live CD' (without changing your system) while the lpia isn't? I don't know what's causing the error when I try to install the lpia image to a usb stick, but I'll look at it again. As I recall, the manual partitioning method was part of the solution to the problem of (lack of) persistence in the UNR install. Not sure how it would apply to the problem of getting the lpia installer to address the usb device, if that is indeed the problem.

UNR and LPIA are two completely different versions of Ubuntu.

UNR: [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
LPIA: [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

---

### Post by skiang on 2009-05-23
Thanks, I get it. I'm interested in upgrading from the Hardy lpia to the Jaunty lpia, as I said, but I'd like to verify that everything on the Mini 9 will work as good if not better on Jaunty lpia before wiping the current install. The tales of woe coming from a lot of upgraders to Jaunty don't give me confidence. As a test (and because I could), I tried out Jaunty UNR to see if it would play well with my Mini 9 and found that it didn't recognize the sdhc card. That gives me pause. Of course, the UNR and lpia kernels are different, as you say, and I don't know if the lpia would have the same difficulty with my sdhc card, but the point is, how can I tell? When I try to install Jaunty lpia from a usb stick to a second usb stick, the installer keeps looking for /dev/cdrom and the operation fails. Is it a problem with my USB stick? I tried it with another one, and the result is the same. So now I'm going to borrow a CD drive, burn the iso to a CD, and see if I can get it to install Jaunty lpia from the CD to a usb stick. I would love to hear
from anyone who has succeeded in doing so.

---

### Post by snowpine on 2009-05-23
> **skiang said:**
> Thanks, I get it. I'm interested in upgrading from the Hardy lpia to the Jaunty lpia, as I said, but I'd like to verify that everything on the Mini 9 will work as good if not better on Jaunty lpia before wiping the current install. The tales of woe coming from a lot of upgraders to Jaunty don't give me confidence. As a test (and because I could), I tried out Jaunty UNR to see if it would play well with my Mini 9 and found that it didn't recognize the sdhc card. That gives me pause. Of course, the UNR and lpia kernels are different, as you say, and I don't know if the lpia would have the same difficulty with my sdhc card, but the point is, how can I tell? When I try to install Jaunty lpia from a usb stick to a second usb stick, the installer keeps looking for /dev/cdrom and the operation fails. Is it a problem with my USB stick? I tried it with another one, and the result is the same. So now I'm going to borrow a CD drive, burn the iso to a CD, and see if I can get it to install Jaunty lpia from the CD to a usb stick. I would love to hear
from anyone who has succeeded in doing so.

Jaunty lpia worked okay on my Dell Mini 9. My only real complaint was that graphics performance (especially flash video) was slow. I tried lpia for a few weeks and then replaced it with an i386-based distro so I could watch mlb.com in fullscreen :).

The problem with recognizing the SD card is a known bug; I am not sure if there is a solution yet (as I have moved on to a different distro) but I am pretty sure a bug report has been filed. 

Oh and as regards the lpia alternate installer not finding the cdrom, this is going to sound crazy, but I got past that error by moving the USB stick to a different USB port. ;)

ps Dellbuntu 8.04 is specifically designed for the Dell Mini and is a stable long-term-support release. I think it is unrealistic to expect "everything on the Mini 9 will work as good if not better" with any other distro (including Jaunty lpia). I have tested many distros on my Mini 9, and all required some tweaking.

---

### Post by skiang on 2009-05-27
Here's an update for anyone interested in testing Jaunty lpia: yes, it can be done without wiping out your current system. Using the Jaunty lpia install CD, it's possible to select a usb stick as the device on which Jaunty will be installed. Having done so, I've been able to test Jaunty lpia on my Mini 9 and can report that everything seems to be working except for a 4gb sdhc card which Jaunty won't recognize. The upshot for me is that I'll probably stick with Hardy lpia for the time being, at least until they get this bug ironed out. Maybe it'll be in time for the 9.10 lpia kernel.

---

