---
title: "Acer Aspire One microphones don't work after suspension, after being on battery power"
date: 2012-04-22
forum: Hardware
---

### Post by chuckbot on 2012-04-22
Hello all! I've been an *ubuntu fan for a while, and I just got a new laptop (Acer Aspire One) on which I am running Lubuntu 11.10. 

The only problem is the microphone inputs (which is a big problem since my computer is my telephone).  I don't think I've gotten the analog line-in to work at all. The built-in mic is functional but cantankerous: It will work, until the computer is unplugged, at which point it only registers a hiss when I test it with arecord/aplay. Function does not return when it is plugged back in; it requires a reboot or two to get the it working again. Suspending the computer causes a similar loss of function. Additionally, running Pavucontrol often seems to crash the microphone. 

I've googled around and not seen any issues quite like mine - I've done a bit of mucking around with alsa and its config file, but don't really know what I'm doing and haven't had any success. 

If anyone can help me out, I'd greatly appreciate it - my friends are getting annoyed both with me and with linux because I keep calling them, not realizing that the mic is dead. At least one has suggested that I return to whinedoze :(

Thanks for reading! <3

---

### Post by marinara on 2012-04-22
i feel your pain

---

### Post by chuckbot on 2012-04-22
You have a similar issue, or just general solidarity? :)

---

### Post by chuckbot on 2012-04-23
bump?

---

### Post by marinara on 2012-04-24
i have an audio driver that should work with a normal microphone, but refuses to do so

---

### Post by chuckbot on 2012-04-25
further testing reveals that it is not being unplugged per se which causes the issue, but being started unplugged, or woken from suspension unplugged.

HALP

---

### Post by decktrio on 2012-04-25
Hey, I happen to have an Acer Aspire One, too. I have a D250.

I'm going to try and set some time aside, later on tonight to try and replicate this. Either way, have you looked to see if someone else reported that bug, or have you reported it yourself? You might want to check out [this help.ubuntu search page]("https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=acer+aspire+one+microphone&sa=Search").

Some resources:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
[https://help.ubuntu.com/community/AspireOneDiscussion](https://help.ubuntu.com/community/AspireOneDiscussion)

---

### Post by decktrio on 2012-04-25
I'm using the default for Lubuntu 11.10 (PulseAudio), but since 12.04 comes out tomorrow, and I plan to do a fresh install soon, I went ahead and...

[LIST]
[*][COLOR=#000000][FONT=Arial]Switched from Lubuntu 11.10&#8217;s default PulseAudio, over to ALSA[/FONT][/COLOR]
[LIST]
[*][[COLOR=#1155cc][FONT=Arial]_http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/_[/FONT][/COLOR]]("http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/")
[*][COLOR=#000000][FONT=Arial]the tutorial from 2yrs ago still works fine[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I also installed [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**alsamixergui**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] and [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**libfltk1.1**[/FONT][/COLOR]
[/LIST]
 
[*][COLOR=#000000][FONT=Arial]I went to my terminal and started up xfce4-mixer[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]I left the default sound card &#8220;HDA Intel (Alsa mixer)&#8221;[/FONT][/COLOR]
[LIST]
[*][[COLOR=#1155cc][FONT=Arial]_http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.24_v1.0.25#HDA_Intel_driver_[/FONT][/COLOR]]("http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.24_v1.0.25#HDA_Intel_driver")
[*][COLOR=#000000][FONT=Arial]I saw that three other options were present:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]Playback: Internal Audio Analog Stereo (PulseAudio Mixer)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Capture: Monitor of Internal Audio Analog Stereo (PulseAudio Mixer)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Capture: Internal Audio Analog Stereo (PulseAudio Mixer)[/FONT][/COLOR]
[/LIST]
 
[/LIST]
 
[*][COLOR=#000000][FONT=Arial]I clicked on &#8216;Select Controls&#8217; and selected all of the controls[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]In the Options tab, &#8216;Auto-Mute Mode&#8217; was Enabled by default.[/FONT][/COLOR]
[/LIST]
 
[/LIST]
 Have you tried changing Auto-Mute Mode from enabled to disabled? I don't know if that will help you*, or if you've already done that, it's just something that I thought of.

*EDIT: It probably won't help ( [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Controls.txt#12](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Controls.txt#12) ), but it's still worth a shot.

---

### Post by chuckbot on 2012-04-25
I'll look through this; thanks :)

---

### Post by chuckbot on 2012-05-05
I tried this and it just seemed to kill my sound completely.

---

### Post by chuckbot on 2012-06-22
bump

no srsly. this is cramping my style. 

i am currently a walking windows advert.

halp.

---

### Post by chuckbot on 2012-07-05
my girlfriend tried to call me, but silly me! I'd briefly unplugged my computer 2 hours ago! She's probably going to break up with me now. Or something.

---

### Post by chuckbot on 2012-07-31
i tried installing kubuntu desktop and using that instead but no fixy. :(

---

