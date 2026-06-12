---
title: "Random locks on Lenovo Thinkpad T420 with 10.10"
date: 2011-10-11
forum: Hardware
---

### Post by lads on 2011-10-11
Dear all,

I've been using Ubuntu since the 8.10 version as my main operating system, first at home and more recently at work. During this time I used Ubuntu on different computers with different hardware configurations without trouble. I have Ubuntu on a flash drive that has booted and worked properly on many different hardware setups.

At the beginning of September I started a new job and was provided with a Lenovo Thinkpad T420 with Ubuntu 10.10 64bit on it. For the first time using Ubuntu is starting to become a challenge. Randomly Ubuntu locks, the mouse moves around but no graphical input reacts to it; no keyboard combination works, Ctrl+Alt+F1, Ctrl+Alt+Del, what ever, there's no response; Fn function keys are also non responsive; if some mp3 is playing the music goes on (ironically) though it goes silent once the track ends. The only option is to force a shutdown with the power button.

The programs I use the most are Eclipse, Lotus Notes and Firefox. These locks seem to happen more when using Firefox, though with other programs they happen too, there's no real pattern I've been able to identify, sometimes it even locks when I'm just reading stuff, without any input. There's no time pattern either, it can go for 3 or 4 days without a lock and suddenly have a burst, this morning I had to reboot three times in an hour.

Browsing the internet I found some references to a possible incompatibility with the video card; since I don't have great needs of that sort I turned it off at the BIOS, though no real results can be reported, the locks go on. There are some references to an issue with the kernel, but the solutions presented show a road that I'm not very comfortable with and don't really grasp.

So, what's your advice on this matter? Is there a particular solution to this problem? How risky is it to start tampering with the kernel?

Thank you,

Luís

---

### Post by lads on 2011-10-12
Hello again,

The ThinkPad Wiki has a [small page about this issue]("http://www.thinkwiki.org/wiki/System_randomly_freezes_and_requires_hard_reset"), blaming it on Intel's Turbo Boost. It advises the disabling of this functionality as so the Intel Flash Cache Logic Chip. Question is: how can that be made with Ubuntu?

Thank you, 

Luís

---

### Post by lads on 2011-10-14
There's [a thread going on at Lunchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/792849") for a few months on this issue. The only solution reported is a replacement of the kernel for version 3.0.

One of the programs I use the most is Lotus Notes, which the IT department tells me doesn't work on newer versions of the kernel. Though the latest release of Ubuntu ships on this kernel version, I haven't been able to upgrade. Is there someone out there using the latest release of Ubuntu on the T420 ThinkPad? Does it solve the hard lock issue?

Thank you,

Luís

---

### Post by lads on 2011-11-03
Just to close down this thread: the upgrade to Ubuntu 11.10 almost eliminated the hard lock issues (one lock in 15 days). The problem is that it also [eliminated Lotus Notes from my hard drive]("http://ubuntuforums.org/showthread.php?t=1864573").

---

