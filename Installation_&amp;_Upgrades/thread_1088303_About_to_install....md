---
title: "About to install..."
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by nitroguy on 2009-03-05
I'm about to install 8.10 64bit on my DV9000 laptop. Is there anything I should know?

I've read this [http://ubuntuforums.org/showthread.php?t=512059&highlight=hp+dv9000+thread]("http://ubuntuforums.org/showthread.php?t=512059&highlight=hp+dv9000+thread") but it says it's "depreciated", and i'm not too sure what that means, but i imagine it means that it's outdated. Anything like this, but newer?

I've seen people running into issues of the system hanging until a button is pressed, at which point it will continue. anything I can do to get around this?

---

### Post by WatchingThePain on 2009-03-05
Think Positive!.

---

### Post by bubwitmaingay on 2009-03-06
You won't learn unless you fail. It's worth the risk and frustration but who knows, your's might be successful.

Set-up your BIOS first before anything. Try to enable devices there, then install Ubuntu. I think that's how this OS operates - "Show me everything and I'll work it out for you." thing.

Good luck. 8)

---

### Post by myk02k on 2009-04-30
I've been running Ubuntu on my dv9000 for over a year now.  Other than HP's dv9000 being an absolute piece of crap, Ubuntu has come a long way since Dapper Drake where there was little support for our laptops.

You should have no problems with Jaunty, but if you have an NVIDIA card like myself, you would need the restricted NVIDIA drivers to utilize the GPU to its fullest potential (take a look on youtube "Compiz-Fusion").  There were a few issues like a flickering screen that needed to be addressed, however I have found all the solutions on this board.

You may also see decreased demand on your CPU and RAM.  This is very beneficial because if your HP dv9000 likes to overheat as much as mine does, decreasing the CPU/RAM usage will decrease operating temperature drastically.  As I am currently running all the system stuff, Pidgin IM, Firefox, compiz-fusion with all its enhanced effects, and about 8 screenlets, my RAM usage is at 34% used by programs and processor about 19% in use.  Vista would demand around 34-35% RAM just after startup...AND I've been able to get the computer at an ultra-light usage when halting indexing, compiz ("metacity --replace"), and other background programs, to rates I never would even witness running XP.

Hope you have as much success w/ Ubuntu as I have.  Gluck!

---

### Post by albinootje on 2009-04-30
> **nitroguy said:**
> I'm about to install 8.10 64bit on my DV9000 laptop. 

Why don't you test the live session with Ubuntu 9.04 ?
Then you can see most things as they should be if installed on the hdd (but you can probably not test proprietary drivers and ndiswrapper in the live session if you would need those.

---

### Post by myk02k on 2009-04-30
Correct me if I'm wrong, but the Live CD does not have the restricted NVIDIA drivers.  Therefore, you will not get the same experience as you would with it fully installed.

---

### Post by albinootje on 2009-04-30
> **myk02k said:**
> Correct me if I'm wrong, but the Live CD does not have the restricted NVIDIA drivers.  Therefore, you will not get the same experience as you would with it fully installed.

Yes. I was trying to say the same thing.
But I can imagine that this could work :
1) install the extra nvidia driver during the live session
2) open a terminal, and type in the following :
```

sudo depmod -a
sudo modprobe nvidia
sudo /etc/init.d/gdm restart

```
YMMV.. but curious whether this would work without a *theoretical* reboot. 
(Theoretical, because a reboot after using the live session from the ubuntu installation cdrom loses all changes stored in RAM.)

---

### Post by upchucky on 2009-04-30
it wont survive the reboot, but there is an option for a persistent home file on a usb thumb drive, this is a bit of work tho. in any case he should be good to go since another has said he has it running on the same pc.

---

