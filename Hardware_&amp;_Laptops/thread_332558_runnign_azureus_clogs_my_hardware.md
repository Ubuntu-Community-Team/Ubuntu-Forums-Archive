---
title: "runnign azureus clogs my hardware"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by alt@ir on 2007-01-06
Dear all,

first of all, best wishes for this 2007, much fun and health.

My old war veteran of a PC has been suffering from a rather unusual sickness since I got to put it back in active recently.
The system works beautifully on everyday operations, although a bit slow sometimes due to its age, but I'm truly happy to be able to put it to good use again and to find an OS which will not ask for inordinate HW ressources just to be powered up.

Anyway, there is an issue that puzzles me (more than being really annoying) : whenever I leave Azureus running for several minutes, the whole system clogs :
- the mouse becomes shaggy, slow and unresponsive, almost unusable (it's like that game that makes you try to aim ur mouse after drinking more and more beer)
- there is also something wrong with the sound buffer : if gaim or amsn are running, whenever someone logs in the chime sound will sound three/x times (and not just one). If I use Rythmbox, it'll freeze if I press play. If I use Gnome Xchat, it'll freeze whenever the app tries to play a sound. Sometimes a system/application sound which should only sound once, enters a loop that takes a while to go.

Apparently, this only happens if I ever stop using the mouse while Azureus is running (like when writing a long post ;) or when watching a film).
I also have the impression that the delay for this behaviour to appear was increased when I changed the video driver on X11 to the nvidia binary one, but this is more subjective that an actual fact.

The solution ? Stopping Azureus does not change anything, stop/start of X11 neither; only a complete reboot does it, my lovin' oldie is ready to kick *** again :D .

I wonder if this has something to do with the preemptive function on the kernel, but I have gotten too lazy over the years and would not consider compiling a new kernel unless it could really do.

Anyone has any ideas ? Anyone has had this kind of issue ?

For the info, I don't think that it's specifically Ubuntu-related because I had the same issue with SUSE 10 a while ago (which made me decide to change and try Ubuntu by the way), so I did not post this on the Desktop forum. On the other hand, I've been running Debian on this machine for years, with custom-tailored compiled kernels, and never had the issue.
Also FYI, while using Debian, the mouse was on the PS/2 port. My mouse is now on the USB (1) port.

Many thanks in advance for your comments !!

-alt@ir-

P.S. by the way, the specs of my pc are ;
- 2x PIII 933MHz (because 2 is better than one!! :D )
- 512 RAM
- GPU GeForce2 MX/MX 400, 65 MB RAM
- NVIDIA X Driver  1.0-8776
- kernel : Linux 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux
- 2 HDDs, 1 DVD-RW, 1 DVD-R
- Sound card : Creative Labs SB Audigy (rev 03)

---

### Post by capitalistpiglet on 2007-01-06
what version of java are you using? I know from experience it will act funny if it isnt run on the latest version.

---

### Post by alt@ir on 2007-01-06
Hi,

java version used is :

*java version "1.5.0_06"
*Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
*Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I'd like to point out that the behaviour I describe is system-wide, not only related to the usage of one specific application (like Azureus). It's just that this behaviour starts when the Azureus has been running for a while.

cheers,
-alt@ir-

---

### Post by Extreme Coder on 2007-01-06
You really should've known that Azureus is always known for making the PC VERY slow. You could try something else, such as Deluge ([www.deluge-torrent.org](www.deluge-torrent.org)) or the BitTorrent client that comes with Ubuntu. I assure you they're much faster and don't clog the hardware ;)

---

### Post by alt@ir on 2007-01-06
Hi Extreme coder,

you're right, the pc is slower when I run it, although I barely notice because of the two CPUs : one takes all the payload of the task and there is other still free to serve the requests of other tasks (that's why 2 is better than one ;)

Anyway, while it could be Azureus, how do you explain that the system is still on its knees when I completely close the application ?
My X server just rebooted (and thus killing all the tasks run under my X session, Azureus included) and opening a new X session was so slow and painful to my ears (having the logon sound repeat in an almost endless loop), that I prefered rebooting the pc.

cheers,
-alt@ir-

---

### Post by alt@ir on 2007-01-06
well, it seems that I finally found a solution/workaround : I created an script, forcing azureus to use java 1.6 and, on top of it, I niced the azureus command.

I left for 1 hour and when coming back, everything was still OK.

I'll watch it for a week or so, but it looks promising !!

MANY thanks to all who tried to help :)

-alt@ir-

---

