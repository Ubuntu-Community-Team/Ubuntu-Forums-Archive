---
title: "Skype sound problem in 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Tacsi on 2009-10-31
Hi,

I have just upgraded to 9.10 and could not get Skype sounds to work. There was a similar issue also when I upgraded from 8.10 to 9.04 (or perhpas, 8.04 to 8.10, sorry, it has been awhile...). At that time browsing the forums I found that I only had to set incoming sound to hdmi and outgoing to pulse and everything worked all right.

However, with 9.10, I do not have the pulse option, rather only hdmi, bluetooth and rawbluetooth. Is pulse not part of the regular Ubuntu distribution anymore?

Could someone please help with some suggestions?

Thanks.

---

### Post by darkone24.7 on 2009-11-01
I do have pulse audio but it still doesn not work.

if I do this

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

skype works but than I don't have keyboard shortcuts for audio, I guess that's from pulse than.

the thing I'm interested in is, skype worked on 9.04 and after changing audio settings in 9.10 it wirked just fine but after reboot it just stopped, no audio at all.

on pulse audio it can produce some sound but you can't understand nothing.

---

### Post by Nittalope on 2009-11-02
Same problem. Just upgraded to 9.10 (but have the same problem with a clean install) and with skype 2.0 I've got problems reproducing sound (Acer Aspire 6530 with Ati Radeon, the internal mic never worked, neither with 9.04).
Followed [this]("http://ubuntuforums.org/showthread.php?p=8212462") instructions on the forum, but same problem, even doing "Make a test sound" the connection sound will not rt clearly. If I killall pulseaudio it rings, but then trying a test call the voice is not clear.

Then I tryed this the things in the previous post.
The connection ring out clearly, but the voice still not understandable.

[Changed] No, uninstalling pulseadio and then installing esound worked. Now the sound out is ok, I still keep my problem with the built in microphone.

Tried also to install skype 2.1, but there in sound options you can only choose pulseaudio... so I cannot switch to a usb mic.

---

### Post by vodsdarov on 2009-11-02
I had similar issue with Skype after upgrading to Karmic.

I simply uninstalled Skype:
```
sudo apt-get autoremove skype skype-common
```

Downloaded the 2.1beta version:
```
http://www.skype.com/intl/en/download/skype/linux/choose/
```

And installed the deb package, which in my case was:
```
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
```

After it, I made sure that the Mic selection under System/Preferences/Sound
was the one from my USB webcam.

Made a Skype test call and everything was perfect.

Hope it helps!

---

### Post by Nittalope on 2009-11-02
Well, after I switched to esound I found out that there were no more applet on the menu bar to manage sound (the speaker with bars showing the sound volume) and that the dedicated keys not worked anymore.
So I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=789578") and re-installed pulseaudio.
Skype (2.0) sound and general sounds works great, only remains the problem with internal mic.

I usually by pass this problem using a usb webcam as my mic, but upgrading to Skype 2.1 I cannot choose this device from Sound Settings as shows only "pulse" option. So I'll keep using the previous version.

And, by the way, I cannot find the Sound entry in System/Preferences menu! This is really strange, I am pretty sure I had it in my 9.04, now I upgraded to 9.10 and there is no more!

---

### Post by ram130 on 2009-11-03
> **Nittalope said:**
> Well, after I switched to esound I found out that there were no more applet on the menu bar to manage sound (the speaker with bars showing the sound volume) and that the dedicated keys not worked anymore.
So I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=789578") and re-installed pulseaudio.
Skype (2.0) sound and general sounds works great, only remains the problem with internal mic.

I usually by pass this problem using a usb webcam as my mic, but upgrading to Skype 2.1 I cannot choose this device from Sound Settings as shows only "pulse" option. So I'll keep using the previous version.

And, by the way, I cannot find the Sound entry in System/Preferences menu! This is really strange, I am pretty sure I had it in my 9.04, now I upgraded to 9.10 and there is no more!

That's because pulse audio is now primary for sound. I did a clean install on my system then right click on the sound icon, selected Sound Preferences then went to Input and selected PC Camera with Microphone. After that I turned the input volume all the way up and I tested my mic. Levels started moving. Then I installed skype from there site and made a call, all works fine. No problems. As for the upgrading, no problems either as I recently updated my mom's Ubuntu also. I suggest you rethink pulse, and check your setup once more.

---

### Post by doppis on 2009-11-03
I was having similar problems with pulse.  I went into synaptic and did a reinstall of pulseaudio, I made sure I had all the pulse software in the ubuntu software center installed and it worked.  Maybe when I did the install of 9.10 it missed some libraries of pulse...no clue.

---

### Post by Nittalope on 2009-11-03
I've reinstalled pulse and everything is working but my internal mic.
In sound preferences, in the input tab it shows only my Internal Audio Analog Stereo card... cannot choose Pc camera with mic... when I plug an external usb camera it appears there and that's how I use skype.

As for skype 2.1, I'll check again... ;)

Thanks!

[Edit] Skype 2.1 is working great! But still the same problem, it seems that my laptop (Acer Aspire 6530G) has not built in microphone! How can I check this thing? I have to use an external usb webcam so to have a mic... upsetting!

---

### Post by ram130 on 2009-11-03
> **Nittalope said:**
> I've reinstalled pulse and everything is working but my internal mic.
In sound preferences, in the input tab it shows only my Internal Audio Analog Stereo card... cannot choose Pc camera with mic... when I plug an external usb camera it appears there and that's how I use skype.

As for skype 2.1, I'll check again... ;)

Thanks!

I believe this is what you saw [IMG]http://www.theopensourcerer.com/wp-content/uploads/2009/10/Screenshot-Sound-Preferences.png[/IMG] 

If so I believe your internet mic is turned down and you would have to get it turn up some how. I believe someone here knows how to do with it pulse. I only know how to do it in alsa with dmixer. Correct me if I'm wrong.

---

### Post by ram130 on 2009-11-03
you can try this guide [Pulse Setup guide]("http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications")

---

### Post by hanzomon4 on 2009-11-03
Sound works in skype for me but it disconnects from pulse constantly and I can't make any calls until I kill it. I can't even do killall skype, I have to use the system monitor.

---

### Post by Nittalope on 2009-11-04
Well... yes, that's exactly what I see... 

Everything works fine, as I said, only the internal mic it's the problem, I'll have a look at this guide...

---

### Post by Nittalope on 2009-11-08
Still cannot find out a way for the mic to be recognized by the system.
Tried every pulseaudio setting (well, maybe not every... but a lot of them) but the mic never appears in my Sound Preferences / Input tab...
Is there a terminal command to check it?
This is really the only issue I've got with ubuntu (now 9.10... everything works smooth... wonderfull!)... sigh...

---

### Post by jf1991999 on 2009-11-08
I was having similar problem.  I fixed the issue with the following advice found on the skype linux forum.

well after upgrading to the new skype. I was unable to talk to anyone, the only sound device options we're pulseaudio server (local) on all 3 settings. Anytime I was in a call with someone they would hear a static sound but that was it, after using "sudo apt-get remove pulseaudio" and "sudo apt-get install esound" I can hear people and they can hear me, I can also choose the sound devices again. Honestly. pulseaudio is rubbish and you should remove support for it from skype. or at least make a seperate build for pulseaudio as a last resort.

Now people hear me clearly with skype 2.1!!!!!

---

### Post by Nittalope on 2009-11-08
Well, absolutely not true, as far as I can say.
I tried the esound choice, but nothing changed (the mic wasn't recognized). With pulseaudio everything works fine. And skype 2.1 is not an issue. Just install pulseaudio and new skype, leave pulseaudio choice in skype. Then open Sound Preferences and check the Input tab.
Just fix the volumes and that's it.
My problem is that ubuntu seems not to recognize that I've got a mic in the pc. With windows works fine, so I'm sure is not a problem of the mic.

---

### Post by betto2000 on 2009-11-08
Hello,

The problem that I have is that I can't set skype to choose my USB headseat as sound output and mic and do the ringing through the internal soundcard. At skype sound configuration I can't choose different sound devices as before for speakers, mic and ringing since the only option available is pulseaudio. At pulseaudio settings I just can set the output device as the internal sound card (that is what I need for the rest of applications) and the input device as the usb headset. With this configuration skype does all the output sound through the internal soundcard and just uses the mic of my usb headset. 

Is there a way to configure the output and input devices per application in pulseaudio ? or if there is a way I can make skype to recognize other sound devices at its sound configuration window? any help greatly appreciated.
Thanks.

---

### Post by David Oxland on 2009-11-15
I'm in a similiar state. My inputs are found OK but always found selected to "Internal Audio Analog Stereo"; when I change it to "QuickCam Communicate STX Analog Mono" then Then Skype works properly, camera, sound and all.
The problem is that it keeps reverting with every shutdown or hibernate.
I Don't know how to make these setting save.

---

### Post by aquamammal on 2009-11-15
I had a problem with the person I was skyping not being able to hear me.

I thought it was something with my hardware, but I went into the system sound preferences, and my mic was muted. 

I unmuted it, and everything was fine. It gives you a choice of internal mic on my mic on the webcam. I chose the internal one.

---

### Post by ram130 on 2009-11-15
Hmm I found that skype doesn't remember the settings 50% of the time after a reboot. Its a major bug.

---

### Post by prince81 on 2009-12-06
When you newly installed or upgraded the Ubuntu, the input sound system, in general,
may remain mute or in a very low state. So, your problem will be solved just increase
the***[COLOR=black] input sound system[/COLOR]***. To do that :

**System --> Preference --> Sound** 
Then **click on Input and increase the input volume**.
That's all and now you can check your skype test call and it will work well.

Cheers.

---

### Post by mysimbaa on 2009-12-07
> **darkone24.7 said:**
> I do have pulse audio but it still doesn not work.

if I do this

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

skype works but than I don't have keyboard shortcuts for audio, I guess that's from pulse than.

the thing I'm interested in is, skype worked on 9.04 and after changing audio settings in 9.10 it wirked just fine but after reboot it just stopped, no audio at all.

on pulse audio it can produce some sound but you can't understand nothing.


Hi thanks for the great answer,

I had a similar problem and it was solved. for your shortcut issue u have to set the sound shortcuts to master.
you go to pereference->sound->default mixer track and pick master.
hope that helps.

---

### Post by am4c130d on 2009-12-08
I am not sure going back to ESD is the right way to go - pulseaudio may not be perfect, and Ubuntu may not have done a great job at integrating it, but I believe it was written because ESD had so many issues.  

So here is how I've addressed the Skype issues I suffered after an upgrade to karmic, everything was working great except skype - which seems to have always had issues with linux, and especially since pulseaudio came along...

My issues, crackly sound, cut outs, no sound etc., appear to have been fixed by resetting the pulseaudio config

$ sudo dpkg-reconfigure --force pulseaudio

I got the following as status reports

* PulseAudio configured for per-user sessions
* PulseAudio configured for per-user sessions

And all appears to be fine now.  

I will say, experience has shown that when it comes to skype, YMMV and so may mine...

---

### Post by am4c130d on 2009-12-09
As I suspected, my fix doesn't work reliably.

The problem, as I see it, is the latency inherent in PulseAudio causes the the echo suppression in Skype to not function correctly - which is fine if you are using a headset (if not irrelevant in the first place), but totally ineffective if you are using a mic and speakers.  I've also found that giving Skype control of the mixer also forces the mic volume to zero - which also doesn't work!!

Prior to Karmic, it was possible to directly connect Skype to the mic device, and this removed the latency of PulseAudio, echo suppression worked - and everything was good.

Any ideas on how to bypass Pulse for input only - i.e. not disable the daemon completely?

---

### Post by anoop79 on 2010-01-20
You may try bypassing pulse altogether in Skype (daemon will still be running, but Skype won't use pulse) by running skype this way from a terminal:

PULSE_SERVER=127.0.0.1 /usr/bin/skype

---

### Post by wisdomlight on 2010-01-20
Hi, I am really a novice with no clue about this code stuff but in need for skype. You seem to understand what you'r talking about. would you like to explain to someone who does not even understand what a code is what to do in order to make skype work and connect me to my mum who lives abroad? please?
cheers

---

### Post by ram130 on 2010-01-21
> **wisdomlight said:**
> Hi, I am really a novice with no clue about this code stuff but in need for skype. You seem to understand what you'r talking about. would you like to explain to someone who does not even understand what a code is what to do in order to make skype work and connect me to my mum who lives abroad? please?
cheers

I'm assuming  your mom is not hearing you on skype but you hear her. Also hope you have gotten skype installed as its similar to a Windows installation.

If you do, try following this..

> **prince81 said:**
> When you newly installed or upgraded the Ubuntu, the input sound system, in general,
may remain mute or in a very low state. So, your problem will be solved just increase
the***[COLOR=black] input sound system[/COLOR]***. To do that :

**System --> Preference --> Sound** 
Then **click on Input and increase the input volume**.
That's all and now you can check your skype test call and it will work well.

Cheers.

---

