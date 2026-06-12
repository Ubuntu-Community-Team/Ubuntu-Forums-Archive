---
title: "No sound in Ubuntu 7.10"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by gerat on 2007-10-20
After upgrading to 7.10 from 7.04, there is no sound. Sound card is Intel ICH3 82801CA AC'97.
With 7.04 it was working great just after installing the OS (no configuration needed).
Don't know how to solve this problem. 

The computer is Compaq 2710UA, P-3, 256mb, 20GB HD.

---

### Post by ldesilva on 2007-10-20
start a terminal and type alsamixer
check and ensure that the no devices is "mute". i have fix my problem by enabling "surround"

---

### Post by peatrap on 2007-10-20
I have a sound blaster live card and the audio would fail to work even when I was using 7.04. I rebooted several times and it started working but ever  once in a while it still fails, The problem has moved to 7.10, requires several reboots to start the audio, when you get it working use suspend instead of shutting down. Hope this helps.

---

### Post by gerat on 2007-10-21
Well, already tried it (alsamixer) - nothing...silence. Starting with LiveCD 7.04 - everything OK. Starting with LiveCD 7.10 - silence.
Any ideas ?!?

---

### Post by flyking on 2007-10-21
I'm having the same problem-no sound at all with 7.10.  "No Sound" is a show stopper and very disappointing since everything else in Gutsy seems to be working great.

I hope this problem can be resolved soon.

---

### Post by DivingWind on 2007-10-22
I also have no sound! Dont know where to start...

---

### Post by lonald on 2007-10-22
Sound works in Ubuntu 7.04, but not in 7.10 on my Compaq Presario 2700 Laptop.

Ubuntu 7.10's Device Manager says that my Audio Controler is:
	Vendor: Intel Corporation
	Device: 82801CA/CAM AC'97 Audio Controller
	Status: Status
	Bus Type: PCI

Most of the Audio Controller's sub component's names start off:
Intel 82801CA-ICH3

Here's a screen shot:
[http://www.lonniebest.com/Image/ScreenShot/AudioController.png]("http://www.lonniebest.com/Image/ScreenShot/AudioController.png")

---

### Post by dinub1 on 2007-10-22
> **gerat said:**
> Well, already tried it (alsamixer) - nothing...silence. Starting with LiveCD 7.04 - everything OK. Starting with LiveCD 7.10 - silence.
Any ideas ?!?

Keep 7.04 then :)

---

### Post by lonald on 2007-10-22
Interesting. When I plug my headphones in, I can hear sound.

I've fooled with every lever in Volume control to make sure that it was not muted and had volume, but the only way I've been able to hear sound is with head phones.

I didn't experience this behavior in 7.04, but do now in 7.10.

---

### Post by dinub1 on 2007-10-22
> **lonald said:**
> Interesting. When I plug my headphones in, I can hear sound.

I've fooled with every lever in Volume control to make sure that it was not muted and had volume, but the only way I've been able to hear sound is with head phones.

I didn't experience this behavior in 7.04, but do now in 7.10.

Sounds weird. Anyway if 7.04 works better for you (in regards to sound) why not return to it?

---

### Post by ed67 on 2007-10-22
I'm having the same problem.  I had it with 7.04 at first too but then after a couple weeks there was an update which fixed the problem.  Hopefully that will happen now too.

How do I go back to 7.04?  A complete reinstall?

Thanks,
Eric

---

### Post by kimusabi on 2007-10-22
[i] That's your best bet. Downgrading is always risky. 

/Kim [/i]

---

### Post by lonald on 2007-10-22
> **dinub1 said:**
> if 7.04 works better for you (in regards to sound) why not return to it?

Because, I don't want 7.04 to be last edition of Ubuntu that works for me.

Backwards compatibility was broken for my machine and I suppose for many others. This is likely an easy fix for the right person; some developer may say "Oh, I forgot to add that driver in the 7.10 release" or "I bet changing X is what caused this unintended ramification".

---

### Post by fresnofred on 2007-10-22
This may not help you but on my pc i was not getting any sound so went to the alsamixer, or volume control, and unmuted all still no sounds.  I noticed that in "file", change device, there were 3 sound cards listed.  Tried each one and unmuted all still no results.  THENNN!!
I noticed after playing around with all the plugins on my sound card, still no results.  But then I remembered that i had a sound card, a sis or realtek, that came integrated with my motherboard.  I plugged the speaker wire into this one and MAGIC!!, SOUND!!.  So, if u have a pc with an installed sound card and one built into the motherboard, try the motherboard one.  Interestingly, when i switched devices in the volume control, i still go sound.

---

### Post by cwrann on 2007-10-22
> **fresnofred said:**
> This may not help you but on my pc i was not getting any sound so went to the alsamixer, or volume control, and unmuted all still no sounds.  I noticed that in "file", change device, there were 3 sound cards listed.  Tried each one and unmuted all still no results.  THENNN!!
I noticed after playing around with all the plugins on my sound card, still no results.  But then I remembered that i had a sound card, a sis or realtek, that came integrated with my motherboard.  I plugged the speaker wire into this one and MAGIC!!, SOUND!!.  So, if u have a pc with an installed sound card and one built into the motherboard, try the motherboard one.  Interestingly, when i switched devices in the volume control, i still go sound.

Thats a nice band-aid but don't you want to utilize your sound card?

---

### Post by scalcave on 2007-10-22
> **lonald said:**
> Interesting. When I plug my headphones in, I can hear sound.

I've fooled with every lever in Volume control to make sure that it was not muted and had volume, but the only way I've been able to hear sound is with head phones.

I didn't experience this behavior in 7.04, but do now in 7.10.


After reading this post I decided to try my head phones too. I discovered the same thing, but the volume was faint.  I figured out that if I lowered the left pcm, the volume increased. I was going to reinstall Feisty, but this allows me a little more patients for it to get fixedt!

---

### Post by tommcd on 2007-10-22
For people who don't have sound:
1) If you upgraded from fiesty to gutsy and lost sound, then I would do a clean install of gutsy. Upgrades can go awry sometimes. Perhaps try the live CD first to see if you get sound.
2) Work your way through this:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dinub1 on 2007-10-23
> **ed67 said:**
> I'm having the same problem.  I had it with 7.04 at first too but then after a couple weeks there was an update which fixed the problem.  Hopefully that will happen now too.

How do I go back to 7.04?  A complete reinstall?

Thanks,
Eric

Yes. I beleive that you need to do a complete reinstall. There is no downgrading. However you can back up important files then wipe out the partition and install using free space. You may need to do that before reinstalling Ubuntu 7.04

---

### Post by dinub1 on 2007-10-23
Soinds very weird. No speakers but phones yes...

---

### Post by ubutnujonny on 2007-10-23
You know, I have had the same problem in the past. Whenever I did a fresh install of Ubuntu the sound would disappear. It's been so long since I installed it I can't remember what I did. But I think the answer is rebooting it a couple of times, and then it should be good to go.

Ubuntu Beryl......Well thats another story and a pain in the ***!

---

### Post by the yawner on 2007-10-23
If you upgraded to 7.10, please try the following on the terminal:

*asoundconf list* - this should list all your sound card devices

then:

*asoundconf set-default-card <device>* - where device is the card of your choice which was listed with the previous command.

Hope that helps.

---

### Post by marcocec on 2007-10-23
The terminal outputs say : Names of available sound card is SB
What shell I do now??

---

### Post by marcocec on 2007-10-23
When I try to associate the only one device I have got on the list, the following message appears:
"Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences".  What should I do==???

---

### Post by Ric_ on 2007-10-23
I had this problem on a Thinkpad T43p.

Before the problem if i had the laptop docked and pluged the headphones into the docking station i could hear sound through the headphones and the laptop speakers. The solution was to plug the headphones into the laptop.

something must of been fixed!

Now when in the docking station i have to use the socket in the docking station!

Hope that helps some people.

---

### Post by lonald on 2007-10-23
I started a bug thread at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013")

This behavior seems to be caused by changes made to alsa-driver.

---

### Post by The_Transporter on 2007-10-23
I agree, I think this is a bug in the system.  

I have reinstalled 3-4 times now and only when I do anything with multimedia plugins things mess up.
I did manage to get one of my installs working with sound after not having sound.  But couldn't find the post that had the instructions.

---

### Post by the yawner on 2007-10-24
> **marcocec said:**
> The terminal outputs say : Names of available sound card is SB
What shell I do now??
On the terminal, just type: asoundconf set-default-card SB

> **marcocec said:**
> When I try to associate the only one device I have got on the list, the following message appears:
"Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences".  What should I do==???
Are you running the command as root (via sudo)? You may run the command as it is. However, you mentioned that only one card is on the list and it was not automatically set as default. Odd.

---

### Post by flyking on 2007-10-24
Finally I have sound in 7.10.  After removing my new sound card and installing my old sound card sound works fine.

I'm liking Gutsy allot.

---

### Post by DRDarkeNY on 2008-04-10
> **ldesilva said:**
> start a terminal and type alsamixer
check and ensure that the no devices is "mute". i have fix my problem by enabling "surround"

I was having the same problem w/Ubuntu 7.04 and the 7.10 upgrade. It was driving me nuts, and I'd tried everything suggested - including something that got rid of the Ubuntu desktop in the process!

But by going ALL the way through the alsamixer (it's several screens accessed by your Right Arrow key) and shoving EVERY possible slider up to 72, I got my sound to work finally! Yay!

---

