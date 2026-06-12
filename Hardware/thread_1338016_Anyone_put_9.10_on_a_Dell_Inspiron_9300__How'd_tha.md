---
title: "Anyone put 9.10 on a Dell Inspiron 9300?  How'd that go for you?"
date: 2009-11-26
forum: Hardware
---

### Post by aaronchall on 2009-11-26
I tried it on a live cd, everything seems to work ok, but just wondering if anyone else has tried it with an Inspiron 9300 from Dell?  My biggest problem with 9.4 was getting the bass speaker to work with the treble speakers, and they seem to have this worked out a little better in 9.10, but they don't move smoothly with each other.  

Anyways, Dell Inspiron 9300, how's it working?

Aaron

---

### Post by aaronchall on 2009-11-27
> **aaronchall said:**
> I tried it on a live cd, everything seems to work ok, but just wondering if anyone else has tried it with an Inspiron 9300 from Dell?  My biggest problem with 9.4 was getting the bass speaker to work with the treble speakers, and they seem to have this worked out a little better in 9.10, but they don't move smoothly with each other.  

Anyways, Dell Inspiron 9300, how's it working?

Aaron
 

Bump, bump, bump bump bump...
Bump, baddabump bump, bump... bump, bump!

---

### Post by captainbliss on 2009-11-28
Typing this message on a Dell 9300 w/ Karmic...

Install and update went smoothly, early days (installed this morning) and so far, so good (I can't comment on battery life, though; I took the battery out years ago and use it a mock desktop.)

RE your sound issues: (quoting from from [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9400))

**Solution:** Open /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf and change the LFE, Master and Hardware Master elements. Change 'volume = merge' to 'volume = ignore'. Now run alsamixer from a terminal and set Master and LFE to 100%. Volume hotkeys will now control PCM volume only, which is what you'll want.

This worked for me with one small change - alsamixer didn't have a channel called LFE, so I set Master Mono to 100% instead - it all seems to work

xxx

---

### Post by aaronchall on 2009-11-29
Thanks, I'll try that, I want to make friends with others with Ubuntu on 9300, so if anyone comes across this thread with a 9300, feel free to friend me, and let's keep in touch, so maybe we can help each other with future issues...

But alas, this tip didn't work for me... maybe I've already changed a config that would have allowed it to work, but I don't remember what it was... oy...

---

### Post by captainbliss on 2009-11-29
RE: sound:

What's under [Element Master Mono] in /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf?

Try 

switch=mute
volume=ignore

along with the changes suggested for the 9400 (previous post)?

Dunno if that'll help?

xxx

---

### Post by aaronchall on 2009-11-29
Changed it, saved it, not working, reboot?  

Here's what I do know/recall: LFE stands for Low Frequency Effects.  Master Mono controls the bass speaker, so LFE applies here.  PCM I have no idea what that means, but it apparently controls all output.  

OK, got it working properly.

So, I didn't reboot.  I opened Sound Preferences under the System-Preferences-Sound menu.  Under the Output tab, I selected Connector: Analog Output/Amplifier. (Previously had Analog Output (LFE) /Amplifier...)

Confirmed it's working by tweaking the terminal alsamixer and observing effects.

But everything is working satisfactorily now.  

Aaron

---

### Post by aaronchall on 2009-11-29
Well, now that I have it fixed, I feel like I have lost my sense of purpose... So, how's your Dell 9300 doing for you?  Has anyone found a utility to let you check out the reported temperatures from the various sensors in the laptop?

Aaron

---

### Post by ke3ju on 2009-12-02
Everything works well for me with 9.10 on my 9300, except the video is too slow.  I have the nVidia driver installed, but I still can't even watch a Hulu video at full screen (1920 x 1280) without it being too choppy to watch.  An nVidia with 256 megs should let me do that.  I'm going back to XP I'm afraid.

I remember dealing with that bass speaker thing in 9.04...what a beach...

Kind Regards,
Ed

---

### Post by aaronchall on 2009-12-04
Too bad you're making your platform decisions based on hulu, there is hulu desktop for linux, but I don't know if that would solve your problem, because I'm not using it.  I might give it a whirl for the sake of others on the 9300... So check back here for updates, but I'm not expecting anything big.  

Honestly, while I use hulu sometimes, I'm also doing other things with my computer, and I don't WANT full screen, and I'd rather just have the lower resolution going on in the corner of my screen.

Aaron

---

### Post by ke3ju on 2009-12-04
> **aaronchall said:**
> I have a friend who works for the Red Cross, and she had an ancient computer with Win2000 and an Internet Explorer 6.  She "accidentally" upgraded to 8, "broke" her computer, and got a "new" one with Win2000 and IE 6 (I think).  

Would someone please tell the American Red Cross about Ubuntu?

Aaron

The problem is, then they need a Guru to support it...

BTW, went back to XP on my 9300, the video is fast as h&ll compared to Karmic.  You'd think by now they'd have nVidia licked in Linux...

---

### Post by aaronchall on 2009-12-04
I posted that quote on a different thread, and updated my post.

---

### Post by ke3ju on 2009-12-04
> **aaronchall said:**
> I posted that quote on a different thread, and updated my post.

Weird...

---

### Post by Globespy on 2010-01-04
I have a Dell E1705 (9400) and cannot get sound to work in Ubuntu 9.10.
It runs the Sigmatel STAC 9200 C-Major HD Audio.

The sound works but it's only coming from the LFE (Sub) channel speaker underneath the laptop.  The left and right speakers are not working.
I've tried a bunch of help pages in this forum but can't seem to fix the issue.
TRied modifying the alsa config and can't seem to get any fix that way either.

When I type alsamixer in a terminal I can see that I only have the LFE channel, not LEFT, RIGHT, CENTER etc.  

Any ideas??  Driving me nuts!

---

