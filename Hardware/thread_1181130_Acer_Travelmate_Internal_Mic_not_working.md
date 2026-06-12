---
title: "Acer Travelmate Internal Mic not working"
date: 2009-06-07
forum: Hardware
---

### Post by Azrael3000 on 2009-06-07
Hi!

So far I have got to say, Ubuntu is a real pleasure to use. When I remember my earlier attempts (years ago) in Linux the situation is so much better now.

Anyway one little thing is bothering me and that's the internal microphone in my TravelMate 8104. The speakers worked out of the box, only Skype didn't like them so much, so I installed the PulseAudio stuff ([http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)) and indeed Speakers are doing just fine everywhere.
Now my laptop has two possible input sources, the first one is a simple mic jack and the other one the built-in mic. Unfortunately I don't have an external mic so I have to rely on the built-in one. I already tried different settings (there I have a switch for Front Mic) in my volume control when capture was set to Alsa (which I updated to v1.0.20). In the PulseAudio Volume Control I only have one input device and this clearly is the mic jack (touching it with my headphones jack it gives me signals).

Now a few bits of information.
lspci | grep Audi:
```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```
Ubuntu v9.04

If you need more information, feel free to request.

Thanks in advance,
Arno

P.S: This might also be related to: [https://bugs.launchpad.net/linux/+bug/280644](https://bugs.launchpad.net/linux/+bug/280644)

[edit][COLOR="Red"]Problem solved completely[/color][/edit]

[edit][COLOR="Red"]**Karmic Koala**: [http://ubuntuforums.org/showpost.php?p=8212462&postcount=11](http://ubuntuforums.org/showpost.php?p=8212462&postcount=11)[/color][edit]

---

### Post by Azrael3000 on 2009-06-10
[IMG]http://i5.photobucket.com/albums/y167/Ginuwine692000/Bump.jpg[/IMG]

---

### Post by Azrael3000 on 2009-06-10
alright. After searching more I finally clicked the right link. Suprisingly enough it's here on the forum.

[http://ubuntuforums.org/showpost.php?p=5196325&postcount=7](http://ubuntuforums.org/showpost.php?p=5196325&postcount=7)

So don't choose the acer model but the 6stack-digout.

On my laptop this resulted in horrible Feedback if my cans weren't plugged in. To cope with that I reduced front-mic volume to 0 and mic volume to 100 (in alsamixer). Input Source has to be Front Mic.

A help for noobs (like me) press <ctrl><tab> once you are in alsamixer to see all settings.

I also followed this guide to set up PulseAudio: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
works like a charm.

The only thing that's left for me is Skype (working - see edit @ bottom of post). At the moment I can't select PulseAudio as option in Sound-In/Out or Ringing. I know that I was able to do it a few days ago and I think the problem should be solved by that. I will report back on that.

Thx to everybody (especially daimadoshi85 & markbuntu)
Arno

//Edit:
Okay Skype is now working to.
I did:
> 2. Then edit or create your asound.conf file

sudo gedit /etc/asound.conf

and add the following lines. Click save once added.

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

3. Edit libao.conf.

sudo gedit /etc/libao.conf

and add the line below

default_driver=pulse
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

and in the Skype Options I used:
Sound-in: HDA Intel (hda:intel,0)
Sound-out/Ringing: Pulse

Only sound quality remains a small issue.

---

### Post by Azrael3000 on 2009-06-12
I got one more small issue.
When mic is turned on I get a little bit of constant noise in my speakers which is a bit anoying. So I want to configure a key to mute the mic channel for which in turn I need a terminal comand.

Now using amixer I only have to controls there: master and capture. But capture actually isn't what I want to mute. Now in the graphical volume control I can switch between devices (i.e. go to HDA Intel (Alsa mixer)) where I then have loads of channels and there I can easily mute the mic.

So basically the question is, how do I access this device from comand line. I found the -D option in amixer but I couldn't find out how to get a list of the available devices (or how HDA Intel (Alsa Mixer) is called there).
Once I have an answer for that it should only be a mater of using set.

Thanks in advance,
Arno

---

### Post by theDaveTheRave on 2009-06-18
I'm guessing that [this post]("http://ubuntuforums.org/showthread.php?p=7478546#post7478546") hasn't helped resolve your problem?

David.

ps, I like your bump!

---

### Post by Azrael3000 on 2009-06-18
you got something wrong in your ctrl+v :)

---

### Post by Azrael3000 on 2009-06-19
haha nice one dave :)

anyway good time for a bump (although I won't reply before late Sunday).

Cheerio

---

### Post by theDaveTheRave on 2009-06-19
AS I said, a totaly non helpfull response.

did you ever get any joy  on your microphone or is it still outstanding?

I only ask as I had a problem with my acer, I sent it back to them for repair.

It was producing "feedback" type noise as soon as the unit was turned on, and wasn't even getting through the POST test thing.

Acer decided that it was an issue with the "un supported" os (ie ubuntu) and refused to fix it.
Surprisingly however, when I got it back it no longer made this horrid noise... but the microphone hasn't worked properly since.

I may have to invest in a USB microphone (or headset).... if I can get one that is?

So my suggestion... a little more helpfull than the original post, have you tried a live CD to see if it will work?

David

---

### Post by Azrael3000 on 2009-06-21
Dave, as I said I also get the feedback, but it's quite easy to fix:
> On my laptop this resulted in horrible Feedback if my cans weren't plugged in. To cope with that I reduced front-mic volume to 0 and mic volume to 100 (in alsamixer). Input Source has to be Front Mic.

Now the only thing that is left to do is noted here: 
[http://ubuntuforums.org/showthread.php?p=7447392#post7447392](http://ubuntuforums.org/showthread.php?p=7447392#post7447392)

But I'll probably open a new thread anyway because this one is kinda confusing.

---

### Post by Azrael3000 on 2009-06-21
Okay I could finally figure out which commands to use

when I started amixer I got PulseAudio as card, which was not what I wanted, so I used amixer -c 0 to get to my real soundcard. Now I created a file called mictoggle.sh which looks like:
```
#!/bin/sh
amixer -c 0 set 'Mic' toggle

```
copied the file into /bin and created a new shortcut in System->Preferences->Keyboard Shortcuts which uses as command
```
mictoggle.sh
```
asigning a key to that et voilá.

---

### Post by Azrael3000 on 2009-11-01
**Karmic Koala:**

It might not even be necessary to do everything I did but here is what worked for me:

edit /etc/modprobe.d/alsa-base.conf
add line
```
options snd-hda-intel model=6stack-digout
```
at the very end.

Install the following packages:
```

padevchooser
libsdl1.2debian-all
asoundconf-gtk

```

I also installed ubuntu-restricted-extras but I'm fairly certain that this is not important for the issue.

Reboot

Start Applications -> Sound & Video -> PulseAudio Device Chooser

You will see an icon appearing in your notification area (looks like a cable), click on it and choose Volume Control, tab Input Devices. I chose Port: Microphone 2 and everything worked (Skype, Record Audio).

---

### Post by tehowe on 2010-04-19
There's another solution regarding internal mic and Skype here:

[http://ubuntuforums.org/showthread.php?p=9144905#post9144905](http://ubuntuforums.org/showthread.php?p=9144905#post9144905)

Basically, install and run pavucontrol then drag one of the mic input channels (L/R) down to zero. Suddenly pulseaudio has input from the internal mic.

---

### Post by Azrael3000 on 2010-04-23
I just updated to Lucid. Since the alsa-base.conf got overwritten in the context internal mic was down again. Adding the line described above again everything seems to work out nicely.

---

### Post by clearwood on 2012-12-14
Worked for my TravelMate 8471

---

