---
title: "KVM compatibility with Linux"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by kcy29581 on 2005-12-10
Hi all,

Many people have problems with KVM switches in Linux. Some like me, have mice that "jump around" on screen when trying to move the mouse around, applications just open, etc. None of these problems happen in Windows, from version 3.1 to the Vista builds today.

I would like someone to explain fully, not half-half, what this problem is all about; why does Linux have this problem? All I want is a KVM that I can use and not worry about. I have bought 2 already and have had to return them because "they do not work" which is a lie, because switching in Windows is ok.

If you can answer, please explain if using a PS/2 or USB port KVM makes a difference, if having a mains powered KVM switch makes everything work, etc.

I am having these problems with Ubuntu also...

Thanks

---

### Post by kcy29581 on 2005-12-13
nothing huh? Not another "Linux does things differently" I hope!
 
Obviously if the KVM manufacturers are breakin compatibility and Windows is fine with that, then ok, manufacturers are to blame.
But if Linux has an inherit problem with specific KVM's... then what?

---

### Post by fog on 2005-12-13
I 'm using a 4 port [Manhattan ]("http://www.dealtime.com/xPP-kvm_switches--manhattan")KVM switch for PS2, 
with USB adaptor for my Mac mini, without problem.
I'm switching between Ubuntu and Tiger, about 2 months.

---

### Post by edmetric on 2005-12-13
[QUOTE=kcy29581]Hi all,

Many people have problems with KVM switches in Linux...
I would like someone to explain fully, not half-half, what this problem is all about; why does Linux have this problem? All I want is a KVM that I can use and not worry about.[/QUOTE]

Your request for a full explanation is not possible due to a lack of documentation of hardware and software in both Linux and Windows.

I run a PS/2 Ratoc REX-210 KVM button switch with Linux (Mepis and Knoppix distros) and W2K without problems. I currently cannot boot Ubuntu on this system because it hangs. This may be a KVM/USB issue but I haven't figured it out yet. I have been looking for information which is why I picked up on your post.

Here is a white paper link to a test of the Avocent KVM with four Linux distros.

[http://www.linux-tested.com/results/kvm_advocent_svip1020.html](http://www.linux-tested.com/results/kvm_advocent_svip1020.html)

And this one, also Avocent, as guidelines for proper KVM evaluation.

[http://resources.linuxinsider.com/linuxinsider/search/viewabstract/78045/index.jsp](http://resources.linuxinsider.com/linuxinsider/search/viewabstract/78045/index.jsp)

There were several other KVM explanations so you might look around for details to help understand the problems with them and the solutions that might work for you.  :)

---

### Post by pjstadig on 2005-12-13
I have had the same problem with KVMs and Linux. We have several 4-port Belkin KVMs (not sure which model...they are the ones that switch sound sources, too...I think they are the SOHO KVMs or something), and they have problems with Linux.

RedHat Enterprise Linux R3U3 seems to play better with the KVMs. If you switch to a login terminal (Alt-Ctrl-1) and then back to X (Alt-7) it will restore the mouse.

This trick doesn't work with Ubuntu. I have just had to use VNC to control my Ubuntu boxes, but I've had trouble getting xinetd to start vncserver for me automatically ([http://ubuntuforums.org/showthread.php?t=91112)](http://ubuntuforums.org/showthread.php?t=91112)), and it's annoying to have to be logged in as a specific user and setup the Remote Desktop.

Anyway, that's everything I've found out so far. I'll probably try to get VNC running as a service, without xinetd, as a next step. VNC is more convenient anyway.


Paul

---

### Post by pjstadig on 2005-12-13
Done some more research. There is an Ubuntu [bug]("https://bugzilla.ubuntu.com/show_bug.cgi?id=7335") related to this that is marked fixed as of 2005-09-26, which I assume means this problem will go away in Dapper.

Paul

---

### Post by AndyCooll on 2005-12-14
I'm using a Belkin 4-port KVM. And although I have occasionally had the mouse dancing round it has only been on a few occasions. Most of the time the KVM works fine.

The few occurrences I've had have been when I've left a pc logged on without use (overnight for instance), the pc has gone to sleep and I've woken it, hence it used to occur mainly with my server. Since I now always make sure I log out of any session at the end of the day it seems the problem has gone away.

:cool:

---

### Post by claydoh on 2005-12-14
I use an El-Cheapo Belkin 2 port p/s2 KVM, the one with built in cabling and have had absolutely no problems at all, though I obviously it is simple and feature-lacking (the reason I bought it really)

---

### Post by kcy29581 on 2005-12-20
thanks for the replies all... shame that there's no "explanation". I'll try reading up more on the bug report mentioned earlier.

---

### Post by Rajan Varadarajan on 2005-12-21
I installed ubuntu on two machines one as a desktop and one for a server (although I installed with the GNOME GUI). Using a D-Link 2-port KVM switch for over six months with Suse Linux (recently switched to ubuntu and I like it a lot better than Suse). I experience an occasional brown out but nothing really persistent. Have been using ubuntu for about two weeks - no problems with the KVM.

Then again, a lot of things can go wrong or subtle events may happen which may impact the video.

---

### Post by rankin on 2007-02-20
I'm not sure what the problem is, but I believe the problem is that the KVM transforms the signals into pure PS2 instead of IMPS2 (wheelmouse) try to set mousetype PS2 instead of IMPS2 (or if the mouse is set to IMPS2 set it to PS2)

---

