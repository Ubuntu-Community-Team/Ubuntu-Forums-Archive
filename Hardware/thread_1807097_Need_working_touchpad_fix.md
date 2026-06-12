---
title: "Need working touchpad fix"
date: 2011-07-18
forum: Hardware
---

### Post by dougalkerr on 2011-07-18
I don't know what it is about this latest Ubuntu release but, there seems to be a lot of people with the same problem I have - no working touchpad.
I am trying to help someone out and away from Windows because of the problems she has had with the system crashing, it seems to have been a combination of hard drive and memory problems.
So I installed Xubuntu 11.04but, couldn't get the touchpad to work. I dabbled with a few files after seeing the problems others were having but, still no joy so I thought I would install Ubuntu 11.04 although it is basically the same system I know. No luck, we still have no working touchpad.
The device is seen by Ubuntu as a SynPS/2 Synaptics TouchPad.
I have edited the xorg.conf.d/50-synaptics.conf file to make sure the driver is not being loaded twice and added parameters to enable the buttons but, still nothing. I have followed a couple of blogs of supposed fixes even following a blog from one of the driver developers for Ubuntu but, still nothing.
The system works fine with a mouse but, what good is that when the lady carries her laptop around to use on her lap.
I am pulling my hair out as I had convinced her away from Windows but, now it is looking like I may have to eat my words and reinstall the damned thing. Oh bother... I just tried Ubuntu 10.10 and still no touchpad. how far back do I need to go to get a working pad. I did read somewhere about people being able to use theirs when they downgraded to a previous version.
If anyone has any ideas, the machine is an Acer 3660 with a Synaptics TouchPad which has a working touchpad when in Windows.
Thanks for looking.

---

### Post by dougalkerr on 2011-07-19
Boy do I feel like a jerk... I was looking at the Acer support for someone with the same problem on an Acer running Windows 7. Guess what - the touchpad was not switched on!!!

Apparently (and I have verified this) you only have to hit Fn+F7 and hey presto, a working touchpad again.

How come nobody here suggested such a simple thing may have been overlooked.

I have searched through quite a few posts and blogs and not one mentions actually switching the touchpad on.

Oh well, we certainly live and LEARN.

---

