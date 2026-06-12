---
title: "Does any Linux distro work with the Llano AMD APU?"
date: 2012-01-27
forum: Hardware
---

### Post by jrmcc999 on 2012-01-27
Hello,

I have a Samsung laptop with the 64 Bit AMD A6-3420M APU / Radeon graphics quad core. I have tried several popular distributions, and they ALL result in a blank screen very soon in the installation sequence.  Operations continue, but there is no video. In fact, none of the live CDs will even boot fully, with the exception of Ubuntu Precise.  I have tried to install Precise to the hard drive, but it eventually dies during file copying, sometimes going back to the live desktop with no error message.  I know these APUs have been a challenge, but I've seen benchmarks where Linux has been used with them.  The Samsung model number is 305E5A-A03.  Thanks in advance.

---

### Post by 2F4U on 2012-01-28
Phoronix says they got Ubuntu working without changes on an A8 CPU:

[http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1)

However, there is a bug logged against Oneiric which pretty much describe the symptoms you are facing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)

It seems as if some fixed went into the Precise kernel, which is possibly the reason why you can boot it. One proposed workarounds from the bug is to install 11.04 along with the proprietary graphics driver and then upgrade to 11.10.

---

### Post by jackharvest on 2012-01-31
Any more word on what distros work on the Llano AMD CPU? Have an a8-3500 here with the Radeon 6620. Also hitting black screen during install.

Hunting for anything that will install. Seriously. Mint and Ubuntu fail.

---

### Post by crackout12 on 2012-02-03
Every distro works, but you should use the fglrx workaround.

Install Ubuntu with the alternate installation method. (Found [here]("http://www.ubuntu.com/download/ubuntu/alternative-download").)

Then boot into recovery mode, or either connect to HDMI display if possible.

*Note that HDMI might go in very low resolutions, such as 640x480.

Get this commands into a terminal (in HDMI), or in the root prompt (in recovery mode).

```
sudo apt-get update
sudo apt-get install fglrx
```

*ALSO NOTE, you might be able to make the normal install on low resolution using the HDMI method, but Ubiquity is very difficult to use since not all buttons can be seen.

Linux Mint should work to, but I am not sure about this.

Good luck!

By the way, the is a very promising bug work here, a developer is trying to make a kernel working with our APU, you should check out from time to time to see if this bug is solved yet or not.

[BUG]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777")

---

### Post by nacho3 on 2012-06-15
I had the same no signal screen problem whith ubuntu 11.10 and 12.04, but with ubuntu 10.10 no problems at all.
It´s working perfectly in my AMD APU 3850, internet conection, video and sound.
Hope someone can fix this bug, i`d like to try 12.04.

---

### Post by HanDez on 2012-07-09
See my post using this link :

 [http://ubuntuforums.org/showthread.php?t=1968155&page=5](http://ubuntuforums.org/showthread.php?t=1968155&page=5)

If it works for you come back and quote and "^ bump" my post please!

:popcorn:

---

### Post by zupercheese on 2012-08-26
so i have had the exact same problem with my computer for a while what i ended up doing was installing ubuntu 10.04 then installing all the updates available. then I installed [the graphics drivers from amd's website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx"). I then performed an upgrade to 12.04 from within the update manager and all was working fine figured i'd share my experience with everyone having this problem.

Also this is my first forum post so i apologize if i screwed up some etiquette or something.

---

### Post by evanrevans on 2012-11-02
The easiest method for me while installing Linux Mint Maya was to slap an old video card in, go through the install, 
```

sudo apt-get update
sudo apt-get install fglrx
```
,restart, shut down, remove video card and hook VGA cable back up my mobo's VGA port.
I can now run linux as my daily driver!

My Gigabyte GA-A55M-DS2 motherboard doesn't have an HDMI port and while researching "linux llano support" I would always find this thread, so I figured I'd post up.

Thank you linux community.

---

### Post by crazyness003 on 2012-11-02
I have an A8 3850 with Radeon HD 6550D
Some bizarre behavior I have includes weird Plymouth displays and seemingly incorrect CPU temperature readings.

Installation, however went like a breeze (relatively speaking).

UNRELATED TO TOPIC BUT INCLUDED ANYWAY. SORRY:

The VESA stock vid drivers worked fine for a bit but then stopped sensing my VGA connected monitor (dual-monitor. One DVI one VGA). I was forced to install proprietary drivers via jokey (Additional Drivers). That's when (see attachment one) started happening to Plymouth during bootup and shutdown. Even switching to different consoles (alt+F5) during startup yielded corrupt display.
Thar's when I opted to purge that install and go for the updated drivers from the AMD website. I'm using the fglrx 12.11 beta drivers(even though I notice no real difference) Same thing is happening to Plymouth. So, in essence, things are broke. For real.

As for my temp sensing, I think the senors are cheating. It simply reflects CPU usage and scales it to a temp. Either that, or my CPU is running SUPER COOL, which is highly unlikely. See for yourself (attachment two and three). These Screenshots were taken during a small battery of burn-in tests which ran all 4 of my cores at 100%. See [this]("http://www.roylongbottom.org.uk/linux%20burn-in%20apps.htm#anchorStart") for more details.
For comparison, BIOS looks WAY more realistic (and scary). (See attachment four)

After reading [URL="http://www.mjmwired.net/kernel/Documentation/hwmon/k10temp"] this, it almost appears like the KERNEL driver "k10temp" is the culprit since it kind of explains what's happening with temp sensing. Time to file a bug?

---

