---
title: "Disk IO blocking under heavy load"
date: 2016-06-17
forum: Hardware
---

### Post by xen3 on 2016-06-17
I wonder if there is anyone willing to shed some light on this.

I have never had problems with IO blocking on Linux, also not with the current PC, that I know of.

It first started happening when I used a slow SSD as cache device.

But although at first I kinda blamed the complexity of my setup, it turns out the IO blocking now also happens when the SSD is not even getting utilized, or, when the SSD is even disconnected (from a running system).

I was able to reproduce time and again a system in which basically all processes are getting IO blocked for even more than 120 seconds, causing sometimes....... messages to be output on TTYs about this.

Currently the SSD is disconnected and I also did not boot with it. The way that I produced the anomaly was by doing a DD write to a volume (on the HDD) and issueing two find -> cat processes that would simply read the entire harddisk (or at least, files) to /dev/null :p.

Then I would do something like starting a few programs or re-reading some library, and often times, KDE (this is Kubuntu) would completely hang, apparently an important GUI process depending on a disk read, but not getting it.

This is 16.04, newest kernel. Unmodified kernel.

Is there *any* reason why a system would be getting such IO blocks?

(At this point I am doing the same stress test; but presently I have not achieved the IO block yet).

I have not tested a different scheduler, it is set to cfq at least for the HDD.

The issue is that this might even happen at random or doing any file operation task, and the system can be unresponsive for 2 minutes or more. I think and I find this to be unacceptable, I want my system to be somewhat and somehow dependable.

It particularly started happening when I added that SSD, at some point.

---

### Post by weatherman2 on 2016-06-17
Have you tested the hard drive?  Sure it isn't failing?  Try GSmartControl.  Make sure you can at least run the shortest S.M.A.R.T. test, and look at the Attributes to make sure none of them are highlighted in pink or red...

---

### Post by xen3 on 2016-06-17
I actually tested the SSD using Transcend's own software. (They have something called SDD Scope Pro) (for Linux). Actually, if anything, I always suspect my motherboard than anything, because some unpleasant people once touched it to remove a harddrive and put some electrical charge on it, after which the system gave weird bugs related to south bridge malfunctioning.

In which case the only thing I could do, is remove it and replace it with another µATX motherboard I have lying around with more or about the same chipset.

Which I would rather not do, but I may have to. This second motherboard comes from a second hand computer and I consider it a bit "filthy" and it has less agreeable outputs for me (no HDMI, or toslink). It wouldn't take more than an hour though to build it in, but strangely the audio card I was using has stopped outputting a digital signal (at least under Linux) which makes it less agreeable even to change motherboard.....

The short Smart Self Tests complete without error. The longer one would take 2 hours to run. I haven't experienced any kind of data corruption and the system is completely stable apart from this.

I seriously feel like cleansing that motherboard with water and then letting it dry .... :p ;-) :/.

---

### Post by weatherman2 on 2016-06-17
The S.M.A.R.T. tests don't use almost any disk IO - the tests are run by the firmware on the drive itself.  So if you are having some sort of IO issue with the motherboard itself, it probably won't show up running S.M.A.R.T. tests.

How about booting a live USB and trying some tests with that?  That would rule out your installed OS as an issue at all.

---

### Post by xen3 on 2016-06-17
I doubt the OS will be an issue as opposed to the Live DVD, it runs the same OS, this is a fresh install.

What the Live DVD did tell me was the fact that initially only the SSD gave these blocks, but not the HDD.

For example, I was using the SDD together with the HDD as a cache, once I disconnected the cache, the problems were gone on the HDD. Since my system was running off USB (at that time, it was an installed system, not live) I had no issues with the system; only the cache (combined) volumes gave issues, and once I disconnected the SSD (cache), the HDD also did not give problems anymore.

But like yesterday or the day before, the HDD also gave blocking even though the SDD had actually been disconnected and thus was not even being used.

The only way I could "rule out the OS" was by running Windows. But the whole idea is that the thing has to work under Linux.

The HDD has been working in this computer for a while and under 14.10 (Kubuntu) there were no issues ever.

Today, no SSD connected, I am not able to reproduce currently. Might be a glitch, but I don't know.

---

