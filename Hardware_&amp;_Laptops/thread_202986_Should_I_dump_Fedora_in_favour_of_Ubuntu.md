---
title: "Should I dump Fedora in favour of Ubuntu?"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by leo_m on 2006-06-24
I have, in the past, tried only Red Hat versions...the latest being Fedora 4.

Not one of the Fedora installations worked for me out-of-the-box.  After reading the Ubuntu posts for Ubuntu newbies, I think neither will Ubuntu (work for me out-of-the-box).  However,  I would list my main experiences with Fedora to request feedback on whether I should expect the same with Ubuntu as well...

a) Kernel support for NTFS driver disabled by default.  Solution: Recompile kernel: takes upwards of 1 hour.
b) *Very* frequent (every 4-5 months, if not less) updates to the complete package (Fedora 4 to Fedora 5 ...) and inability to update to one version from another without deleting (update process does that for you) the old version...pain unless you have all your data in a separate mounted partition (given hard-disk structures, I have limited no. of partitions, so can't/don't want to do that)...my machine is essentially a multi-boot.

Will Ubuntu 6 be able to get upgraded to Ubuntu 7 using the built in updates mechanism, or does it expect me to wipe out Ubuntu program files (in Windows parlance) before I can upgrade to Ubuntu 7 (whenever that happens)?
c) sound and video *never* worked out-of-the-box for me - I always had 2nd latest Intel chipsets etc.  This last time, however, situation was a little better in that I got ATI Radeon x700 on my laptop and drivers for that are provided by ATI (for Linux).  For sound, had to compile and install ALSA drivers.  Time taken in discovery of relevant information and then doing the needful for sound/video for the various distros has always taken a few hours...maybe I am not smart enough, but I want to spend lesser time on this kind of stuff.
d) Wireless issues...had to do everything myself - nothing out-of-the-box; search for firmware, match proper versions, do a build, install it...and that's when I was lucky enough to have good support (by Linux standards) on the Intel site.

I expect Ubuntu to have lesser issues with hardware...I need to get *productive* on my OS faster than I have been able to in the past with Fedora...the question is, will Ubuntu be less cumbersome for the hardware I have?

However, Fedora comes with lots of packages, which allow me to use my box with server-type applications, like DNS, samba server, sendmail etc. as well as a Desktop studded with user applications...Ubuntu has separate server and desktop versions, if I install Desktop version, can I incorporate server version's functionality into it without much hassle?

Lastly, Fedora's update mechanism has given up on me 'cos I did not have internet for a couple of months for Fedora auto-updater and now that I have, it cannot update *everything* (well, everything had got newer versions in the meantime...), I have to keep trying again and again and again...do I expect the same behaviour from Ubuntu if I lose touch with internet for a couple of months and then come back and run the update?

Does Ubuntu support Debian .deb packages through its update mechanism?

Do you think I should keep Fedora 4 (oh, I do not want to lose all my configuration if I upgrade to Fedora 5) or should I switch to Ubuntu in hope of having to cope with lesser no. of configuration and hardware issues?

(as I write this, my webcam and tv tuner card do not work (on Fedora) yet...and the graphics performance is far worse than in Windows...heard Ubuntu has 3D for ATI working properly though, is that true?)

And doing something as simple as disabling tapping for clicks on my laptop's touchpad has not been possible yet...

---

### Post by bscbrit on 2006-06-24
First of all, without knowing precisely what hardware you have, it is impossible to say whether ubuntu will work 'out of the box'.  A good way to find out is to run the live disk before trying a full install. :-)
Ubuntu can be updated from one version to the next online quite easily.  I wouldn't worry about not being able to update your system in the future.
If you create a separate partition for your /home directory, and you backup the contents of /etc and perhaps /var into it as well, you can easily upgrade to another version and keep the majority of your settings intact.  A problem will only occur when a new version of a program uses a completely different method for storing its settings than the old version used.  However, this is a very rare occasion nowadays and shouldn't cause you too many problems.
Yes, Ubuntu supports all deb packages using any of its usual update methods (synaptic / apt-get / Add/Remove etc).
Only you can decide whether the effort of changing OS is worth it.  Judging from your comments I would say 'yes' but it is still your decision.  
One of the major benefits of Ubuntu is the terrific support available from the large user base.  If you need help dissabling tapping for clicks then someone here will be able to help you.
Good luck.

---

### Post by leo_m on 2006-06-24
Hardware specs:
[http://www.sagernotebook.com/pages/tech_spec.html#1](http://www.sagernotebook.com/pages/tech_spec.html#1) (model NP5320)

with a LifeView-DVB-T Hybrid PCI-mini tv-tuner
and a bison cam 1.3 mp web-camera.

I am downloading Ubuntu DVD ISO and will install it - I do not think it will hurt me much anyway (even if it does not work fully as expected).  It will hopefully allow me to have a taste of Debian way of things...

---

### Post by bscbrit on 2006-06-24
Good luck.  Come back if you have any specific problems and I, or someone else on this forum, will try to help. :D

---

### Post by leo_m on 2006-06-25
Feedback in one line: fresh and exhilirating experience, I like ubuntu; cool stuff.

The installation was fast and gave me the option of continuing to use Live CD or install it on hard-disk.

No, Ubuntu does not install as much stuff as Fedora does,  but I do have an internet connection presently...

Upon beginning installation, it could not start xserver, and I was shocked for a few moments...then I rebooted in safe graphics mode and I got the same level of graphics as I got with Fedora (without ATI proprietary drivers).  Currently I have max. 1024x768 resolution but I hope when I start going to proper forums, this situtation will improve, giving me 1920x1200 resolution and full hardware acceleration support.

Sound worked out-of-the-box and I saw and heard Nelson Mandela telling about the spirit of ubuntu on the Live DVD.

Wireless worked out-of-the-box.  Ubuntu or Windows do not know the network names security keys etc. I have, beforehand, ;) (and if they knew, I would not use them), and once I provided these in proper configuration files, wireless was up.  The Networking applet in Administration menu however does not have capability to handle WPA or wpa_supplicant for wireless, and WPA is fairly largely used these days.  I am not complaining however, and I am happy the way WPA gets included in network startup/Ubuntu boot.

Upon doing a dmesg | less, I can see that my tv-tuner card is being supported and likely my webcam too.  But I need to download apps to test that. [update 20060723: neither of these is supported in any flavour of Linux for the hardware I have, and I am really getting frustrated with this - have started a new thread on this to seek help]

I just finished updating and the update was as smooth as in Windows...it even gave me tooltips, after finishing, that I need a restart of the OS!! :D  (but it means Linux has begun to ask for restarts as well!!?) I like the way it has been designed and implemented, user-friendliness and stability, the two hallmarks of Ubuntu are prominent when one uses this OS.

It took far less than it takes Windows to install and while it was installing, I was watching videos/presentations provided on the live DVD...this software is immensely likeable.  I was first impressed at the way QNX gets installed...almost instantaneously; and now I liked the way Ubuntu installed...not instantly, but pretty fast...yeah, I know it installed far less stuff than Fedora does, and that's why I would say to those who do not have a fast internet connection, to think before they take the plunge...but it does a good job of installing most software which a common person would use...I mean, a few games, office productivity software, administration tools, a multimedia player, browser etc...

The icing of the cake is, Windows takes far more time than this (to install) and then one has to (well, I always had to) install drivers many a time...with many reboots.  But Windows does not ask you to configure the system files using command line, and though Linux community makes fun of that (Windows users not being *technical* etc.), that is a strong reason behind its popularity.  Ubuntu provides you a clean unobtrusive install (atleast it did in my case), and you do not need to install drivers afterwards :D

In a nutshell, I liked Ubuntu, I am not going to remove this for some time and after some time, I may decide to keep this software for quite a long time... ;)

I was thinking of buying Vista when it would get released (that was before I installed Ubuntu); hmm....

Three cheers for Ubuntu and the spirit of ubuntu. I am hooked.

---

### Post by bscbrit on 2006-06-25
Great news - welcome to the world of Ubuntu!  See you around the forums.

---

### Post by leo_m on 2006-06-25
[update] Got 1900x1200 resolution by following directions under video and sound section of hardware support forum (for getting ATI drivers to work - that post should be sticky).

However, my earlier thought that my tv-tuner is supported is not correct, the driver module somewhat misleadingly tells that it found a generic board, but the card-type is -1 so it does not work.  Ubuntu has support for some models of Lifeview DVB series, will have to explore this further.

After that, it will be the turn of the webcam ...

The purpose of this post is finished I think, so I shall now post more specific problems/solutions as per the topic in the relevant space.

---

### Post by fakie_flip on 2006-08-07
Fedora has newer packages in its repos. Ubuntu has old software in its repos. apt-get is much faster than yum in Fedora. I see advantages and disadvantages to both. Ubuntu seems to run faster than Fedora.

---

