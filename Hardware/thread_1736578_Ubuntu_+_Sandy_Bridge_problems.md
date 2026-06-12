---
title: "Ubuntu + Sandy Bridge problems"
date: 2011-04-22
forum: Hardware
---

### Post by jjohnn on 2011-04-22
Hello,

(This is my first post here. I first searched threads discussing similar problems, but while I found other Sandy Bridge issues they appeared to be different from mine. My apologies if I've missed something).

I'm having some trouble with Ubuntu on a newly built computer using Sandy Bridge. The motherboard is an Asus P8H67-M Evo (Intel H67 chipset), processor is i5-2500k. I'm trying to use the processor's integrated GPU (Intel HD 3000).

On most boots, either from Live CDs (I've tried Ubuntu 11.04 beta 2, Fedora 15 beta 2, and the Ubuntu and Fedora nightlies from 4-21-2011) or from the hard drive the splash screen appears very grainy, with lots of (grainy) vertical red lines. The screen then goes black, and the computer becomes completely unresponsive.

The Fedora and Ubuntu nightly Live CDs both booted successfully at least once, but after booting from the hard drive the problem described above came back. After several reboots, the Ubuntu nightly install did come up normally from the hard drive once. I installed the x-org edgers PPA, but the problem returned at the next boot.

I'm stumped, because the symptoms I'm seeing seem different from those reported by others, and because the newer versions in the betas, nightlies, and PPA haven't fixed the issue as they have for others. It's pretty frustrating knowing that it can somtimes work fine, but only seeing that rarely and inexplicably (to me).

Has anyone seen anything similar, or know what I can do to get it working consistently?

Thank you,

John

---

### Post by jjohnn on 2011-04-22
It seems that I made a poor assumption in my original question. I just used the Ubuntu 11.04 beta 2 "alternate install" disc to install a command line-only system and it has exactly the same problems.

I'll do some new research on that basis, but I wanted to post an update here right away.

---

### Post by jjohnn on 2011-04-22
Since posting the above, I've updated the BIOS (actually UEFI I guess). That's seemed (subjectively - I haven't kept statistics) to make Live CDs / installers more reliable, but I haven't had any successful boots from the hard drive since the one mentioned in my first post here.

Based on recommendations I've found for troubleshooting, I've also tried disabling Turbo Boost, CPU throttling, "enhanced SATA" mode, and enabling ACHI mode, all without affect. 

(Just want to keep this updated, so anyone who helps knows what I've tried).

Thanks,

John

---

### Post by jjohnn on 2011-04-23
Sorry to keep replying to myself, but I have to retract some information above.

I now have a working install, command line only, of Fedora 15 on the machine. It's working perfectly well as long as I don't try to start X.

The Ubuntu 11.04 beta 2 command line only install I did had the same problem as graphical installs of either Ubuntu or Fedora. Does it use a splash screen or something? It looked like that may have been what happened but I couldn't tell for sure.

We use Ubuntu Server 10.10 at work on a couple machines and I know it doesn't have a splash screen, but I haven't used Linux on the desktop for quite a while.

Thanks again,

John

---

### Post by bnice7 on 2011-04-25
Hi John,

I have pretty much the same setup as you -- exactly the same mobo and CPU.  I'm currently running Kubuntu 10.10.  I experienced the same screen tearing that you're describing when the splash screen came up.  It was loading it with a strange resolution and with the wrong freq. @ 75hz instead of 60hz.  However once I get past the splash screen the resolution snaps back to normal and I get a KDE desktop.  I upgraded the kernel to 2.6.38 which gives me some video acceleration, but with no desktop effects and some menu distortion due to incomplete support.  Without the kernel upgrade, I still had no issues getting a KDE desktop, but just had absolutely no video acceleration.  I'm holding off until 4/28 before I upgrade to 11.04 / Natty for the final release with the hopes of having full GPU support.  

One thought that comes to mind, have you checked your core temps in BIOS?  It could be if your heat sink is not mounted properly that as soon as it tries to load X, it sends the CPU and GPU temps up through the roof.  Just a thought...

---

### Post by jjohnn on 2011-04-25
bnice7,

Thank you for the reply.

Regarding core temps, I almost thought I had a problem there at first based on readings from the BIOS. It was reporting about 55c, which is a lot higher than most people were getting. It turns out though that the BIOS mis-reports on the high side - [here's the entry about]("http://support.asus.com/faq/detail.aspx?SLanguage=en&p=1&m=P8H67-M%20EVO&s=39&hashedid=CkMiq3rrqw3yqO5H&os=&no=4BA17F89-E17A-E858-F1B3-76845BC681B0") it on Asus's site. I was able to confirm that by looking at readings from within an OS. I was relieved to find they're actually about 30-32c at idle.

I've "solved" the problem for now by borrowing an nvidia 9600GT from a friend who just upgraded to a newer card. I'm hoping to switch back to the integrated graphics in the future - I'm not a gamer, so I'd rather have the lower power/heat than the extra power, and my understanding is that Intel's open source drivers are generally of high quality. This works for now though.

Thanks,

John

---

### Post by bnice7 on 2011-04-25
Glad you got your issue fixed.  That's also why I went with the H67 chipset, so I wouldn't have to run dedicated graphics (not much of a gamer anymore).  After my build, I couldn't get any installation CDs to boot, then I noticed my core temps were reporting around 85 degrees C in BIOS.  Apparently I forgot (don't laugh) to take a piece of plastic film off of the surface of my heatsink before I installed it.  Once the plastic was removed and thermal compound was re-applied, I then got a modest 40-45 deg. C reading in BIOS.  

Another thing you might consider checking out is the display resolution X is trying to use.  I originally had an older model no-name brand HDTV I was using for a monitor, and it was trying to auto-detect some wacky unsupported resolution.  This was of course using the VGA port since this TV wasn't equipped with HDMI.  I had to manually create the correct modelines using gtf and xrandr.  When I finally got my new TV, everything was auto-detected correctly using HDMI. 

I'll keep you posted if I have any more luck with my setup.  Here's to hoping 11.04 gets all of the sandy bridge graphics woes sorted!

---

### Post by Yellow Pasque on 2011-04-25
@jjohn, it might be helpful to see your /var/log/Xorg.0.log after a failed attempt to start X (like with a LiveCD, because you have nvidia drivers on your install now).

---

### Post by mofirouz on 2011-05-05
Hello. Hope that I am not too late with this 'improvement'.

I have Core i3 2100T build (made for a NAS server), along with the latest Zotac Motherboard (Mini-ITX). 

I have the same problem with this machine. However I had a working installation of 10.10 with Xorg Edgers, and when 'upgraded' manually to 11.04, stuff started to go wrong. Realllly wrong. Anyways, wanted to do a clean install of 11.04 and this thing kept happening.

So my display was connected to the DVI connector, and black lines appeared. After tweaking around with literally everything, one thing that I notice was the lack of use of HDMI. 

I plugged the HDMI cable in, and bang display came up from the LiveDisc. I think anyone who has thing problem should try this, because the underlying problem is either the display driver in linux or bad xorg configuration.

When HDMI is plugged in, the display is thought-of as a TV and therefore those config/drivers wont be loaded. Once installed, then take care of the conf and etc (if you are like me and want to use DVI).

BTW, the HDMI WILL overscan the resolution, so you won't be able to see the top menus, but they are there.

Good luck.
Mo.

---

### Post by rickyrockrat on 2011-09-10
So, don't know if this helps anyone, but I'm running a 3.0.4 kernel with the xorg-edgers, and I've got two displays running. I occasionally have vertical lines when moving windows (on the moved window), but if the window is repainted, it is restored.

I've attached my config file for the linux kernel and my Xorg.conf to make this happen, and some brief directions on building a kernel, and adding the xorg-edgers ppa.

Here's the tar. Hope it works for you. I'm on Lucid, and it seems pretty stable so far.

[http://ubuntuforums.org/attachment.php?attachmentid=201898&stc=1&d=1315701799]("http://ubuntuforums.org/attachment.php?attachmentid=201898&stc=1&d=1315701799")

---

