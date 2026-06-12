---
title: "Installing cpudyn may have disabled I/O?"
date: 2009-05-01
forum: Hardware
---

### Post by mobrien118 on 2009-05-01
Hello,

I have a recently installed ubuntu system that was working fine.

I just installed cpudyn on it (i'm not even sure if this is the right module for it, p4-3.0GHz+multi-threading) but once I did, I rebooted and it is NOT RESPONDING TO THE MOUSE or KEYBOARD!

So, i figured I would just SSL into it and do some exploring, but the network indicator icon in the top is showing the red X (either disabled or disconnected, I'm not sure which).

Other than that, it appears to be a normally functioning system :-) I have the system monitor widget installed in a sidebar and all of the indicators are moving as if it's working, I just have no way to get in and talk to it!

Any ideas on anything I can do?

Thanks,

--mobrien118

---

### Post by mobrien118 on 2009-05-02
OK,

So, if I go ahead and make an assumption that 'cpudyn' is what caused this issue (BTW, these things still work in the BIOS and LiveCD so I know it's not hardware failure), is there any way for me to get into the package system and remove the CpyDyn package without actually booting into the system? Like maybe use a livecd?

Is this a use case for chroot? (Not sure because I've never used it b4).

Maybe I could LiveCD in and just remove the file that tells cpudyn to oad (from init.d, iis that where it is started from?)

Just some ideas, anyone have anything solid/comnments/questions?

I am surprised I haven't received any responses yet! I would think this would be a very interesting case! If Dr. Gregory House were a ubuntu user, he would jump on this case :-)

Thanks very much!

--mobrien118

---

### Post by omko on 2009-05-02
I have got the same problem today, after installing some updates
I'm using a usb keyboard and mouse now to access ubuntu
cpudyn is not installed here btw
but I'm still searching for a solution !

---

### Post by mobrien118 on 2009-05-02
OK, so maybe it is not caused by the installation of that package, or maybe it is caused by a dependency of that package that is also a dependency of some other package you installed as well.

You are using a 32-bit install, right?

Did you install anything or change anything recently that may have triggered this event for you?

Omko! It's good to know that I'm not alone at least!

I'm trying a few things to get into the system from the liveCD right now, but a further complication is that I have RAID installed, and mdadm, etc isn't present on the LiveCD so I'm trying to configure it on my own. We'll see what happens!

Fortunately, I don't care if I lose this system. I just created it 2 days ago, but there is a Windows Virtualized Guest OS on a raw RAID partition that I'd rather not lose. We'll see!

--mobrien118

---

### Post by omko on 2009-05-02
yes it's 32 bit
all what I did is installing the updates, I want to know what's the updates I 've installed, so that I can figure out what's the source of the problem
the updates have corrupted my sound drivers, but I've fixed them
but the keyboard and mouse is my big problem now
I suggest you use usb mouse and keyboards ( if some are available ) for you, that will make things easier for u than trying to solve the problem from liveCD

---

### Post by mobrien118 on 2009-05-02
> **omko said:**
> yes it's 32 bit
all what I did is installing the updates, I want to know what's the updates I 've installed, so that I can figure out what's the source of the problem
the updates have corrupted my sound drivers, but I've fixed them
but the keyboard and mouse is my big problem now
I suggest you use usb mouse and keyboards ( if some are available ) for you, that will make things easier for u than trying to solve the problem from liveCD

Hmmm... I'm using a USB mouse, but that's not working. The keyboard is PS2, and I don't have a USB mouse...

Is your network working?

---

### Post by omko on 2009-05-02
yes , no problem at all with my wireless network

---

### Post by mobrien118 on 2009-05-02
> **omko said:**
> yes , no problem at all with my wireless network

NM on this issue for me. I busted my RAID config so I'm just re-installing. I don't think I hurt my Windows partition (crosses fingers).

Sorry, I won't be able to work along with you anymore since I broke it.

--mobrien118

---

### Post by mobrien118 on 2009-05-02
OK, I'm back!

I just did a fresh install on the same partition, formatting it, and I still have no keyboard or mouse! This is too weird!

NOTE: It works in the livecd!!!


WTF?!?!?

---

### Post by mobrien118 on 2009-05-03
OK,

So everything works in the LiveCD, the keyboard and network work in Safe Mode when booting into the new clean installation. But when I boot into the clean installation in normal mode, I get the login window, but I can't type or move the mouse, and even though I installed SSH (while in safe mode + net) I can't SSH, or even ping the machine.

I feel like hardware failure should be ruled out by the fact that the hardware works in everything except for regular mode.

What is really strange is that it worked perfectly when I first installed it 3 days ago, then after a reboot after installing cpudyn, it stopped working and now, even after a completely fresh install, it doesn't work.

Baffling!!!!!

Also, is there any way to change the thread title? It doesn't really apply to the problem anymore, I don't think...

--mobrien118

P.S. I don't know that this makes any difference, but the Ubuntu system is installed on a 3-disk striped RAID0 "partition". /boot/ is on it's own tradidional partition, though.

---

