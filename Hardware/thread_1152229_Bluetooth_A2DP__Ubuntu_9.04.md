---
title: "Bluetooth A2DP / Ubuntu 9.04"
date: 2009-05-07
forum: Hardware
---

### Post by unforgiven512 on 2009-05-07
I am having a very hard time getting A2DP bluetooth headphones to work under Ubuntu 9.04.

I've followed multiple guides, and I have had zero success in getting my headphones working.

I have all the bluez-* packages installed, including bluez-alsa.

I've attempted the "toggle.sh" method. Failed attempt.

I actually managed to lose my regular sound this morning.

Any help would be appreciated.

Thanks,
UNFORGiVEN512

Edit: Oh, hey, this is my first post. Hello everyone!

-- I made my account a couple years ago, didn't realize I never posted.

---

### Post by iddy on 2009-05-11
New also, and having similar issues.
Problem is I'm too new and even having trouble installing/compiling the bluetooth-alsa, really don't get the instructions on this page(link below), any help for me to reach the step above will be much appreciated :)

[http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)

Other people have managed to get the bluetooth-alsa package working by following the linux-savy instructions on that page, so it may work for you unforgiven?

---

### Post by Mikebo on 2009-05-11
a2dp is working perfectly for me. This is what i did:
- upgraded pulseaudio to the newest version from this ppa [https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/~themuso/+archive/ppa")
- installed blueman instead of bluez-gnome [https://launchpad.net/~blueman/+archive/ppa]("https://launchpad.net/~blueman/+archive/ppa")

I don't have to use any scripts and that sort of nonsense, I simply connect to my hifi with blueman and then in pulse audio volume control(sudo apt-get install pavucontrol) choose which audio stream should be played back through a2dp.

---

### Post by iddy on 2009-05-11
Hey Mikebo, thanks for that, i'm installing some other stuff, but i've added the sources.list entries and will let you know how i get on :)

EDIT:
I've installed the new version of pulseaudio and blueman, and run the line sudo apt-get.. Lappy will now connect to stereo, but when i change sound preferences to pulseaudio sound server (for music and movies) test returns nothing. Also, there is no option to change master to pulseaudio, only HDA Intel and an OSS Mixer.

Neither pulseaudio device chooser or volume control work -both just sit in bottom panel "Starting.."

Thanks for helping me make it connect! Thats one step, just need to configure it now, and chance on some help with that plz??

---

### Post by unforgiven512 on 2009-05-11
See, the problem is not getting it bonded. I have it bonded with my PC.

Also, I do not use PulseAudio (I am using xubuntu), so therefore I am using ALSA.

I still can not manage to send audio to the headphones rather than the internal speakers.

I installed blueman and I attempted using that. I clicked "Connect A2DP Service", it reported to be connected, no luck.

Any ideas?

EDIT: I might reinstall back to ubuntu or possibly kubuntu. I'm getting really frustrated with xubuntu, it seems poorly integrated.

---

### Post by iddy on 2009-05-11
Hmm, i read that in order to get it too work with alsa (here: [http://ubuntuforums.org/showthread.php?t=75677](http://ubuntuforums.org/showthread.php?t=75677)) you need the bluetooth-alsa not the bluez-alsa thing.. probly worth a moment of your time to read that page..
Because the pulseaudio doesn't work too happily, i might try getting the alsa to work too.. 
That link i posted earlier ([http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)) would someone mind taking a look at it, then letting me know exactly how to download and build, or at least fill in the gaps for me ;) so I can test out these alsa ones..

---

### Post by unforgiven512 on 2009-05-13
Ok, mikebo, I followed your instructions (I am back on regular ubuntu)

I have had no success.

My headphones will not show up as an audio device for pulseaudio or alsa.

Not sure why.

I even enabled the pulseaudio plugin in blueman.

Any ideas?

---

### Post by Mikebo on 2009-05-13
I really don't know why it isn't working for you guys. I've attached screenshots of synaptic with all bluetooth and pulseaudio packages that i have installed on my system, take a look, maybe there is something you're missing.

[Here]("http://fosswire.com/post/2008/10/better-bluetooth-audio/") is a good guide on how to get a2dp working with pulseaudio, although you shouldn't have to create that .asoundrc file, blueman is supposed to take care of it for you.

Good luck

---

### Post by unforgiven512 on 2009-05-14
I've finally got it working.

I installed package "pulseaudio-plugin-bluetooth" as well as "python-bluez". I believe the former is more important.

Now just to figure out how to get pause/play, track advance/back to work...

---

### Post by Surfrock66 on 2009-05-14
What if I can't install pulseaudio-plugin-bluetooth because I get this error:

> E: /var/cache/apt/archives/pulseaudio-module-bluetooth_1%3a0.9.15-1ubuntu2~ppa1_i386.deb: trying to overwrite `/usr/lib/pulseaudio/pulse/proximity-helper', which is also in package pulseaudio

EDIT: NM, Solved that.

I have all of the packages installed, my headphones are connected via bluetooth and I am successfully using pulseaudio through my laptop's speakers, however in Pulse Audio Volume Control I see no A2dp device anywhere.

Using the guide Mikebo posted, I tried running this line: 

> pactl load-module module-alsa-sink device="bluetooth"

But got this in response:

> Failure: Module initalization failed

Any ideas?

---

### Post by DanaG on 2009-05-15
Interestingly enough, once I found a sane (as in, not totally lacking in any sort of settings) utility for bluetooth pairing, and combined it with PulseAudio 0.9.15 from a PPA, I finally got working bluetooth audio in Linux... the first time it's ever worked for me.

Utility you need: "Blueman"
[https://launchpad.net/~blueman/+archive/ppa](https://launchpad.net/~blueman/+archive/ppa)


PulseAudio 0.9.15:
[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)
(Note that this new version has a Flat Volumes feature, that I personally find very confusing; disable that feature in daemon.conf if you wish.)

---

### Post by lavadisco on 2009-05-15
I installed the new PulseAudio stuff and Blueman, and for the first time ever I can pair with my bluetooth audio receiver. However, now when I try to open the PulseAudio Volume Control, I get this error:

```
Connection failed: Connection refused
```

Anybody know why this is happening? I feel like I am so close to finally getting this to work!

---

### Post by unforgiven512 on 2009-05-15
I had A2DP working for a short period of time.

I accidentally connected in headset (SCO) mode, and it crashed PulseAudio.

Now every time I turn my headphones on, it connects in both A2DP mode as well as SCO (headset) mode, crashing PulseAudio.

Gah. One step forward, two steps back.

I am contemplating just reformatting and reinstalling, starting fresh. It's very frustrating.

If I do decide to do that, I will let you know my results.

BTW: When PulseAudio crashes, I get the "Connection Refused" error.
Audacious stops playing, and crashes as well.

---

### Post by lavadisco on 2009-05-15
I figured out why I was getting the "connection refused" errors. I hadn't upgraded all the PulseAudio packages. Now that I've done that, the PulseAudio Volume Control works now.

Now I'm connected to my bluetooth audio receiver, but I can't figure out how to send the audio out the bluetooth adapter and not the speakers. There doesn't seem to be an option for it in the PA Volume Control, and nothing is listed in the PA Device Chooser either. I can specify "other" for source and sink, but what the heck do I put in there?

---

### Post by DanaG on 2009-05-15
When I tried it (Motorola H350, or something like that, with only mono mode), I had to connect to it in blueman and then right-click to get the "connect to service" thingy.  Once I did that, I was able to see the device on the "Configuration" tab in pulseaudio volume control.  If that's not working, try running PulseAudio in a console; you may get some sort of useful output.

Edit: it's H700, not H350.  Whatever.

---

### Post by unforgiven512 on 2009-05-15
Ok, I am running a clean install of Ubuntu 9.04.

I am going to attempt to get my bluetooth headphones working once more.

I will post detailed instructions on how I managed to get them to work (provided I do get them to work) once I get them working.

EDIT:

My attempt has failed. Here are the steps I followed, from when I actually *did* have it working.

> 
A2DP Experience

CLEAN INSTALLATION!
-------------------

1. added repositories to synaptic
-- [https://launchpad.net/~blueman/+archive/ppa](https://launchpad.net/~blueman/+archive/ppa)
-- [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)
2. reload repositories
3. mark all upgrades/install
4. select blueman, pulseaudio-module-bluetooth, python-bluez, pavucontrol,(audacious), (ubuntu-restricted-extras), install
5. reboot
6. enable pulseaudio plugin in blueman
7. put headset in pairing mode, search/add/bond
8. setup/connect A2DP service

FAILURE:
Headset connected in both headset mode and a2dp mode, crashing pulseaudio.


I also installed bluez-btsco and bluez-compat in hopes that would make a difference, to no avail

---

### Post by lavadisco on 2009-05-16
Dang. Well, thanks for trying. This is a function that should work right out of the box.

Bugs me most when friends come over and I try to be mr snobby linux guy, but if want to play music via bluetooth I have to boot into Windows XP to do it. Kind of kills the whole mojo. :p

EDIT: Wouldn't you know it - after trying all this stuff, suddenly audio is gone in Flash/Firefox, a problem I just spent two weeks fixing. What I did to fix it before now doesn't work. I have Linux fatigue.

---

### Post by Mikebo on 2009-05-16
Once you connect to your device it should be listed in pavucontol under output devices (which is pretty obvious). Then in the playback tab you should see all active audio streams, now you just need to click the dropdown arrow and choose your device (see the screenshot).

To get AVRCP working (play,pause etc.) see the guide i've linked in my previous post.

---

### Post by Surfrock66 on 2009-05-16
> **Mikebo said:**
> Once you connect to your device it should be listed in pavucontol under output devices (which is pretty obvious). Then in the playback tab you should see all active audio streams, now you just need to click the dropdown arrow and choose your device (see the screenshot).

To get AVRCP working (play,pause etc.) see the guide i've linked in my previous post.

It's not listed in PUAvControl, and I've been following the guides as best as I can, is there some sort of output that would be helpful to figure out why?

---

### Post by Mikebo on 2009-05-16
> **Surfrock66 said:**
> It's not listed in PUAvControl, and I've been following the guides as best as I can, is there some sort of output that would be helpful to figure out why?

If you can connect to your device with blueman and it doesn't show up in pavucontrol then maybe it's a bug in blueman (could be pulseaudio). Try asking for some help here [http://blueman-project.org/forum]("http://blueman-project.org/forum/")/

For all i know a2dp feature in pulseaudio and blueman is pretty new and it might not work for everyone yet.

One more thing. I think this was enabled by default, but maybe it wasn't. Right click on blueman icon > About > Plugins and see if pulseaudio plugin is checked.

---

### Post by unforgiven512 on 2009-05-16
See, the problem is i *had* it working, and then I accidentally hit the "call" button on the headset, connecting the "headset/sco" service, crashing PulseAudio completely. Since then I've reinstalled from a clean installation of Ubuntu, and I have been unable to recreate it working again. PulseAudio simply crashes every time, because headset/sco connects.

Ugh.

---

### Post by iddy on 2009-05-17
Damn.. I came on here thismorning, and followed the steps here ( [http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/) ) after a bit of playing with pavu and putting "PulseAudio Soundserver" as my sound output thing for events and music&movies (system>preferences>sound) it worked :)

But this was only after I updated the system, which I noticed had a pulseaudio update in the mix.. Which allowed me to use PulseAudio Volume Control :)

Basically the steps I took are:

Install Blueman
Install Pavucontrol
Create home\myname\.asoundrc (follow link above for the instructions on this)
logged out/in
pactl load-module module-alsa-sink device="bluetooth"
selected the blank output device (in PulseAudio volume control) as default

ty to everyone who helped me reach this point, anyone with q's I'm happy to try an help :)

In response to the sco problem, I'm not sure what this is.. the only thing I could suggest is unpairing, removing their record in blueman and re-pairing the headphones again..

---

### Post by Mikebo on 2009-05-17
> **unforgiven512 said:**
> See, the problem is i *had* it working, and then I accidentally hit the "call" button on the headset, connecting the "headset/sco" service, crashing PulseAudio completely. Since then I've reinstalled from a clean installation of Ubuntu, and I have been unable to recreate it working again. PulseAudio simply crashes every time, because headset/sco connects.

Ugh.

My hifi only supports a2dp and i didn't have any problems with it so far. But i also have motorola s805 headphones which support a2dp as well as sco, so i thought since most of you seem to have problems with this particular type of hardware i should give it a try (i didn't use it before). All i can say is that it was NO FUN AT ALL.

It will often crash my system when i try to connect, and even when if manage to connect it will only play mono (sco that is). I guess we should seek help on the blueman forum. What do you think?

---

### Post by unforgiven512 on 2009-05-17
I have no idea. It's very frustrating.

Something else I have noticed.

PulseAudio 0.9.15 seems to be very unstable. Just in general. Sometimes, using audacious, it will just crash and I will have to stop playback, wait about 30 seconds, then restart playback.

Perhaps in the next version we may get more stability?

Also, [https://bugs.launchpad.net/blueman/+bug/350479](https://bugs.launchpad.net/blueman/+bug/350479) might be a good place to post some of our issues.

---

### Post by Psimon on 2009-05-17
I'm not a techie, so I've no idea why this works or whether it will help anyone, but I have Bluetooth working stably, so I thought I'd explain how I did it:

1. Add these repositories to synaptic
-- [https://launchpad.net/~blueman/+archive/ppa](https://launchpad.net/~blueman/+archive/ppa)
-- [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)
2. Reload repositories
3. Mark all upgrades/install
4. select blueman, pulseaudio-module-bluetooth, python-bluez, pavucontrol, etc.
5. Download this Bluez 4.37 package: [https://edge.launchpad.net/ubuntu/karmic/i386/bluez/4.37-0ubuntu1](https://edge.launchpad.net/ubuntu/karmic/i386/bluez/4.37-0ubuntu1) and install.
6. Log out and in again
7. Create the .asound file as described using the Model number of the bluetooth receiver (in my case the first line is HWS-BTA2WA - this is a Sony made Bluetooth receiver which has phono output jacks) so my .asound file looks like this:

pcm.HWS-BTA2WA {
  type bluetooth
  device XX:XX:XX:XX:XX:XX
  profile "auto"
}

I found the device Mac address using the** hcitool scan** command.

8. Switch your audio settings to "PulseAudio" in your system Sound settings, including Sound Capture. 
9. I use Exaile to play music with the Bluetooth plugin which can be installed from Exaile's plugin menu. Configure Exaile to use pulseaudio and Start playing music.
9. Activate the receiver, and then go through the Blueman set up dialogue - this went smoothly for me.
10. Open the PulseAudio Volume Control and go to the Playback tab and left click on the exaile python output to select the bluetooth device.

This got the audio streaming to my Bluetooth receiver.

I also managed to get Realplayer streaming to the receiver by selecting it to run using OSS instead of ALSA under Preferences.

One thing that is annoying for me: my bluetooth transmitter is an very how power Aircable with a range of 10 km, but I have to do the above set up with** the receiver placed very close to the transmitter**, for the "Connect to A2DP" step in Blueman to work - if I initially try to connect it with the receiver connected to the stereo in an upstairs room it fails. So I have to do a lot of running up and down stairs, which doesn't exactly make it convenient.

---

### Post by lavadisco on 2009-05-17
I went to "about->plugins", and PulseAudio was not checked. I checked it, and nothing changed. Still no A2DP, no bluetooth output in PulseAudio volume control. I have a couple of questions:

- What is this "RTP Multicast Sink" that I see in the PA volume control?

- Blueman seems to automatically power down my bluetooth receiver after only a few minutes of inactivity. Anybody know how I can prevent this?

---

### Post by Psimon on 2009-05-18
Just read this thread a bit more carefully. Check you have upgraded Bluez to 4.37 via the link in my above post. It seems this version contains bug fixes, but it's not in backports yet.

---

### Post by lavadisco on 2009-05-18
> **Psimon said:**
> Just read this thread a bit more carefully. Check you have upgraded Bluez to 4.37 via the link in my above post. It seems this version contains bug fixes, but it's not in backports yet.

My understanding was that an installation of Blueman precluded the need for Bluez. Is this not the case?

---

### Post by Psimon on 2009-05-18
> **lavadisco said:**
> My understanding was that an installation of Blueman precluded the need for Bluez. Is this not the case?

I'm not certain as I can't access my Ubuntu box at the moment, but I think Blueman replaced bluez-gnome when I installed it, but I got the impression that it's an alternative controller for Bluez. It certainly seemed that upgrading the Bluez package was what fixed it for me.

---

### Post by Mikebo on 2009-05-18
Here is a ppa with recent bluez 4.39 which you can try [https://launchpad.net/~bmillemathias/+archive/ppa]("https://launchpad.net/~bmillemathias/+archive/ppa")

---

### Post by lavadisco on 2009-05-18
> **Mikebo said:**
> Here is a ppa with recent bluez 4.39 which you can try [https://launchpad.net/~bmillemathias/+archive/ppa]("https://launchpad.net/~bmillemathias/+archive/ppa")

Thanks! Does anybody have any idea if installing Bluez will actually prevent Blueman from working correctly?

---

### Post by forevertheuni on 2009-05-23
I tried with a Motorolla H350, a Motorolla H500 and a Nokia BT-500.
The H350 doesn't connect right.
The other two connect right with blueman. The audio service connects right. I shows in pavucontrol. When I move any stream to it I have no audio at all. Any hints for me?

---

### Post by mkde on 2009-05-30
For what it's worth, the instructions in this thread helped me to finally get AD2P working in Ubuntu for the first time *ever*.

---

### Post by jerich007 on 2009-06-03
Finally got this working for me.  After following Mikebo's instructions, I still couldn't start PulseAudio volume control, it would fail to start as it did for others here.  I did a 'apt-get upgrade pulseaudio' followed by 'apt-get install pavucontrol' and it fixed things for me.  Selected my Motorola S9 as the output device in pavucontrol and was good to go!

Thanks to the gurus here!
- J

---

### Post by hibliss on 2009-06-20
> **iddy said:**
> Damn.. I came on here thismorning, and followed the steps here ( [http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/) ) after a bit of playing with pavu and putting "PulseAudio Soundserver" as my sound output thing for events and music&movies (system>preferences>sound) it worked :)

But this was only after I updated the system, which I noticed had a pulseaudio update in the mix.. Which allowed me to use PulseAudio Volume Control :)

Basically the steps I took are:

Install Blueman
Install Pavucontrol
Create home\myname\.asoundrc (follow link above for the instructions on this)
logged out/in
pactl load-module module-alsa-sink device="bluetooth"
selected the blank output device (in PulseAudio volume control) as default

ty to everyone who helped me reach this point, anyone with q's I'm happy to try an help :)

In response to the sco problem, I'm not sure what this is.. the only thing I could suggest is unpairing, removing their record in blueman and re-pairing the headphones again..


This post helped me a lot. Thanks. I was almost there with the other advice in the thread, but this summarised it nicely.

How can I make this command run at boot time?

```
pactl load-module module-alsa-sink device="bluetooth"
```

Edit, after using this for less than a few hours, I have noticed some serious bugs. This may just be with my bluetooth chipset on my Eee, but the range is terrible compared to Windows and the sound skips/slows down/speeds up ad lot. I am sure it is related to the linux driver. I find that it gets worse when I am heavily using the WiFi, which is a lot.

I am using Jabra BT620s bluetooth headphones with a Broadcom BT253 chipset if anyone is wondering. 

Has anyone else experienced this? Works fine in Windows of course.

---

### Post by shaunbarlow on 2009-07-29
Thanks to all for the info.
I've got it all working perfectly.

There was a small bit of confusion when for a few restarts bluetooth wouldn't turn on and blueman wouldn't open the devices dialog but after reinstalling every package that looked remotely related to bluetooth and a2dp, then restarting it all worked.

What I'd like to know from anyone who has something to add is how a feature could be implemented that automatically connects to any available "favourite" a2dp device when the computer has some audio to play?

Thanks again.
Cheerio,
Shaun

---

### Post by xyepblra on 2009-08-15
Guys, I cannot run pavucontrol, the alert says: "Connection failed: Connection refused". What's that?

I am trying to connect Motorola S805 bluetooth stereo headphones to my Jaunty, so if there is a complete solution for that, please share it with me (and probably the others who buy a device without investigating first whether it is supported by the system or not).

---

### Post by xyepblra on 2009-08-15
> **Mikebo said:**
> a2dp is working perfectly for me. This is what i did:
- upgraded pulseaudio to the newest version from this ppa [https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/~themuso/+archive/ppa")
- installed blueman instead of bluez-gnome [https://launchpad.net/~blueman/+archive/ppa]("https://launchpad.net/~blueman/+archive/ppa")

I don't have to use any scripts and that sort of nonsense, I simply connect to my hifi with blueman and then in pulse audio volume control(sudo apt-get install pavucontrol) choose which audio stream should be played back through a2dp.I did everything you mentioned here and have only managed the play/pause button and previous/next slide wheel of my Motorola S805 BT stereo headphones to work so far.
I cannot manage the pavucontrol to display the bluetooth option for streaming the sound. And, the most important, I have lost the sound in the speakers of my laptop.

Please help me to fix the mess.

---

### Post by xyepblra on 2009-08-15
> **xyepblra said:**
> Guys, I cannot run pavucontrol, the alert says: "Connection failed: Connection refused". What's that?
Alright, here comes the news update:
[LIST=1]
[*]Good news is pavucontrol works;
[*]Bad news is this time play/pause button on the headphones is not working any more.
[/LIST]
Surprise has happened to me during the process of setting the connection between my laptop and headphones over Bluetooth: the increment of the volume adjust has got fixed. I wrote about that problem in a couple of threads. I will be double happy keeping this new setting after fixing the headphones' binding via Bluetooth.

---

### Post by xyepblra on 2009-08-17
Well, after modifying ~/.asoundrc and changing
```
pcm.bluetooth {
        type bluetooth
        device 00:33:44:DD:EE:FF
        profile &#8220;auto&#8221;
}
```with
```
pcm.btheadset {
        type bluetooth
        device 00:33:44:DD:EE:FF
        profile &#8220;auto&#8221;
}
```(key change is bluetooth -> btheadset) I have managed executing ```
aplay -D btheadset -f s16_le /usr/share/sounds/ubuntu/stereo/dialog-question.wav
```successfully on fifth attempt.
I have regained the control over tracks played in Phythmbox through the buttons and wheels of the headset. When I stream something different to /usr/share/sounds/ubuntu/stereo/dialog-question.wav, nothing happens for five to six attempts, and then I hear noise in the headphones. Good thing about that, the sound volume is adjustable with the headphones controls.
The overall result is, I cannot stream the sound to Bluetooth device, because that connection is not shown in the "Move Stream" menu of the pavucontrol. Should I re-install pavucontrol?

---

### Post by rablack on 2009-08-23
Hi All,

After following the instructions throughout this thread, I have successfully gotten a2dp working with my Motorola DC800 audio gateway and sound is coming out of my speakers. However, I also have some Motorola HT820 headphones, which no longer work.

Before I installed Blueman and PulseAudio 0.9.15, I was able to use the manual method of editing the .asndrc file, running pactl and then setting the default sink to whatever I needed. It was cumbersome but worked.

Now when I turn on my headphones Blueman sees them and automatically connects, setting up the necessary PulseAudio modules, as it does with the audio gateway. However, it seems to also connect the headset profile at the same time, plus another a2dp connection. Using at the PA volume control, I can transfer an audio stream from sat Rhythmbox to any of these sinks and I can see the relevant volume bar moving. The only one that produces sound from the headphones is the headset profile one, which as you can imagine sounds terrible. It is as though Blueman is keeping both connection to the headset and a2dp open and the headphones are taking the headset connection in priority.

Does anyone have any suggestions?

Thanks,

Richard

---

### Post by Kryzzalid on 2009-09-04
Hi,

I pretty have the same problem with my headphone Philips SHB6100. I use Blueman and Ubuntu 9.04. Blueman "connects" to the headset via the laptop broadcom integrated bluetooth card. But there is just the connecting bip and then some noise for 5s and then it stops. After that, nothing at all. I also noticed that during the 5s noise the computer's sound doesnt work anymore. When i connect my headset the syslog writes that:

Sep  4 17:38:31 Akatsuki bluetoothd[7610]: link_key_request (sba=00:10:C6:8D:24:E7, dba=00:0C:78:4F:D2:CE)
Sep  4 17:38:32 Akatsuki last message repeated 2 times
Sep  4 17:38:32 Akatsuki bluetoothd[7610]: Can't open input device: No such file or directory (2)
Sep  4 17:38:32 Akatsuki bluetoothd[7610]: AVRCP: failed to init uinput for 00:0C:78:4F:D2:CE

I've tried lot of thing i found from forums and blueman has so far the best results. I have also an USB bluetooth adapter which was with the headset. But i have no idea how to get it work. lsusb gives that:

Bus 001 Device 003: ID 152e:2507 LG (HLDS) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 002 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Also the headset works well with my cellphone w850i.

Thank you:)

---

### Post by bfree2run on 2009-09-12
OK Guys, I am a beginer in ubuntu, but i think i have the solution for you all, It is very very easy..even a baby can do it:D..to find it , it a killer.  it has been tested on 3 different  bluetooth devices.. here are the steps i took. I only tested for music with Audacious, and it works great.
1. Install Blueman cuz that's all you need, forget about pulse audio or modifying anything and other crap.
2.Pair your headphones with Blueman, Click Connect A2DP Service(if it gives you ''Failed'' message one afteer another, try restarting your computer, then try again)
3. open Audacious on the''Current output plugin'' select Alsa Output PLugin
4.click on Output PLugin Preferencies
5. On the '' Audio Device write '' bluetooth ''   (without '') , and that's it.. restart your computer it you have any trouble and try again.. it shoul work pretty good.
I my self have some problem with the volum, turning it down or up(works only from application(in my case Audacious).
 It should work with every player/application, if you only select/write bluetooth in it settings. HAVE FUN.

All my thanks goes to BUTY for this treat. He's a real Budy.(thanks for the Dell's man)
Remember..DONT HATE ROMANIANS!!, 98% of us are good guys.:D ...PEACE & GOD/ALAH/BUDA..etc BLESS US ALL.

---

### Post by bfree2run on 2009-09-12
Just tested  it  with mplayer too, works great...:)..have fun

---

### Post by Kryzzalid on 2009-09-14
Seriously, thank you:) i got the bluetooth headphone to work with Audacity:) But would you have an idea how i could get it work with skype??

---

### Post by bfree2run on 2009-09-14
one min. let me check..

---

### Post by bfree2run on 2009-09-14
You might need to enable Headset service insted of the A2DP(advanced audio) service..it just a ques :D

---

### Post by mordecai83 on 2009-09-15
hello there, 

finally got my bluetooth headset working with blueman. Works great with audacity however with mplayer i do get sound but i get an error that keeps repeating itself about the mixer. So my question is: in mplayer i selected alsa as my driver, then configured its device settings to " bluetooth ". but what do i put in Mixer and Mixer channel??? And is there any way to get it working with vlc?

with kind regards,
Mordecai

EDIT: Nevermind. I was able to get pulseaudio to work with my headset. Everything works great now. No need to configure individual applications.

---

### Post by bfree2run on 2009-09-16
Perhaps you can share with us, how did you made it work.:P

---

### Post by mordecai83 on 2009-09-17
Seemed like i cheered too soon. I followed the instructions on page 1 and it worked. pulseaudio was sending audio trough my headset and i was extremely happy. UNTIL i restarted. Now i cannot turn on a2dp mode in blueman. Blueman starts acting weird and my headset turns itself off. I did some fiddling around and it seems the pulseaudio-module-bluetooth package is the culprit. If i uninstall it and then restart pulseaudio i can turn on a2dp in blueman without a problem. But this is no use as without the module i cannot tell pulseaudio to send audio to my headset. Reinstalling the module gives the same problem. I guess the module is either not loading right in pulseaudio or is conflicting with something else. My noobish *** can't figure it out. I cannot tell you enough how this sucks, i thought i could finally use my headset and it worked great, sound was really good. 

Has anyone had the same problem and ifso do you know about a workaround? Maybe there is a way to install the newest pulseaudio on jaunty? (i saw 9.17 is out) any help is appreciated!!

---

### Post by bfree2run on 2009-09-17
I have found that Bluesoleil has a Linux version, the windows version works great..hope the linux version works as good.It has all you need..it automatically switch betwin cable/bluetooth when device is stoped, it also creates a sound card(with all the options. so the sound volume will work , but i cant make it work..i've installed acording to their site..

[http://www.bluesoleil.com/products/Default.aspx?TID=11](http://www.bluesoleil.com/products/Default.aspx?TID=11)

but nothing hapends. It a great prg...i hope i'l make it work...I'l keep you posted

---

### Post by bfree2run on 2009-09-17
If any of you made it work, please let us know...:)

---

### Post by Riptie on 2009-09-17
> **bfree2run said:**
> I have found that Bluesoleil has a Linux version, the windows version works great..hope the linux version works as good.It has all you need..it automatically switch betwin cable/bluetooth when device is stoped, it also creates a sound card(with all the options. so the sound volume will work , but i cant make it work..i've installed acording to their site..
 
[http://www.bluesoleil.com/products/Default.aspx?TID=11](http://www.bluesoleil.com/products/Default.aspx?TID=11)
 
but nothing hapends. It a great prg...i hope i'l make it work...I'l keep you posted
 
I get the same......NOTHING.. The program installs without any problem but when you click on it to start nothing
HUH...
 
EDIT  :   O i got something alright..... after I installed this I got my rythmbox starting when I click on anything...
Please HELP ME

---

### Post by bfree2run on 2009-09-18
Try remove rythmbox and install it again, from add remove programs

---

### Post by xyepblra on 2009-09-19
> **bfree2run said:**
> Try remove rythmbox and install it again, from add remove programsbfree2run, are you recommending this because you had the same problem and this solution worked for you or it's just a general idea? I tried your solution to fix my problem, which can be basically described as losing the sound in the earphones after updating blueman and some other applications. Strange thing is, headset is paired to laptop pretty well, at least I can toggle playlist items and pause them. Are there any solutions for the problem excluding uninstallation of applications that can result in screwing the sound completely?

---

### Post by bfree2run on 2009-09-19
I belive you have 3 choices
1. you remove rithmbox, and reinstall it
2. you remove blueman, and reinstall it again
3. i dont know this one yet :), like i've said i'm a begginer in ubuntu.
 
It a general ideea.

---

### Post by nickolasemp on 2009-10-05
I know I don;t contribute much to the discussion, but I installed blueman and pulseaudio .15 and everything works fine. Though I do need to resync everytime I reboot.

Granted, it took me a while to understand how things work but now everything is great! The only thing I had to do was to delay+ the movie I was watching in smplayer.

---

### Post by xyepblra on 2009-10-05
> **bfree2run said:**
> I belive you have 3 choices
1. you remove rithmbox, and reinstall it
2. you remove blueman, and reinstall it again
3. i dont know this one yet :), like i've said i'm a begginer in ubuntu.
 
It a general ideea.
Apparently I have had 4 choices. The 4th one was unpairing the Bluetooth device, restarting the system, searching and pairing the Bluetooth device back again, running the ```
pactl load-module module-alsa-sink device="bluetooth"
``` command in terminal, choosing the Bluetooth device as a default output device in the **pavucontrol** and finally enjoying the music without disturbing people around.
Well, what I shouldn't have been doing was running pavucontrol command in terminal during the music playback (I did in order to copy the pactl command).
Thank God it is easy to fix back, just repeat the last 2 steps.

---

### Post by dc2447 on 2009-10-08
I can pair using blueman, and can connect to the  a2dp service but I get no sound via the BT headphones, plus pavucontrol shows no bluetooth outout device

---

### Post by Kryzzalid on 2009-10-09
I got the BT headset for A2DP working with blueman, bluez and ALSA. Well, I only tried with Audacious. Anyway, here is what i did:

i wrote in ~/.asoundrc:

pcm.headset {
type bluetooth
device XX:XX:XX:XX:XX  #(write your own headset address found with the command hcitool scan)
profile "auto"
}

bluez-alsa is also required.

I paired and connected the BT headset with blueman. And then in Audacious I choose ALSA Output plugin and in the its configuration i wrote headset in the audio device box. But again this only works with ALSA.

---

### Post by xyepblra on 2009-10-14
Well, what I have done last time didn't last long. What happens now is after playing one track in Rhythmbox there is no bluetooth in the **pavucontrol**. So I have to close Rhythmbox, then run **pactl load-module module-alsa-sink device="bluetooth"** again, then **pavucontrol**, and then re-open Rhythmbox to listen to just one track again. Any ideas of remedy?

---

### Post by VitaLiNux on 2009-11-06
[SIZE=7]You're superb, Mikebo! Thank you for all of your tips!! :p[/SIZE] Please! Please! Please! If you're lost like I was with this A2DP issue, FOLLOW ALL OF THE STEPS AS MIKEBO SUGGESTED. DO NOT FORGET TO FOLLOW THE LINKS HE SHOWED. YOU'LL FIND THEM VERY USEFUL. TESTED USING JAUNTY.):P

---

### Post by VitaLiNux on 2009-11-06
> **VitaLiNux said:**
> [SIZE=7]You're superb, Mikebo! Thank you for all of your tips!! :p[/SIZE] Please! Please! Please! If you're lost like I was with this A2DP issue, FOLLOW ALL OF THE STEPS AS MIKEBO SUGGESTED. DO NOT FORGET TO FOLLOW THE LINKS HE SHOWED. YOU'LL FIND THEM VERY USEFUL. TESTED USING JAUNTY.):P

Here's what I did:

[SIZE=6]What Mikebo said:[/SIZE]

> 
a2dp is working perfectly for me. This is what i did:

- upgraded pulseaudio to the newest version from this ppa [https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")
- installed blueman instead of bluez-gnome [https://launchpad.net/~blueman/+archive/ppa]("https://launchpad.net/%7Eblueman/+archive/ppa")

I don't have to use any scripts and that sort of nonsense, I simply connect to my hifi with blueman and then in pulse audio volume control(sudo apt-get install pavucontrol) choose which audio stream should be played back through a2dp.

I really don't know why it isn't working for you guys. I've attached screenshots of synaptic with all bluetooth and pulseaudio packages that i have installed on my system, take a look, maybe there is something you're missing.

@ [http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/) is a good guide on how to get a2dp working with pulseaudio, although you shouldn't have to create that .asoundrc file, blueman is supposed to take care of it for you.[SIZE=6]DEVICES THAT I USED:
[SIZE=2][COLOR=Blue]-Generic usb bluetooth dongle[showed by the [COLOR=Red]lsusb[/COLOR] command as [COLOR=Red]KY-BT100 Bluetooth[/COLOR]] (it has always worked out-of-the-box since Ubuntu 7.10)

-[COLOR=Red]Nokia BH-501[/COLOR] A2DP enabled headset.
[/COLOR][/SIZE][/SIZE]
[SIZE=7][COLOR=Black]WHAT I DID:[/COLOR][/SIZE]
[COLOR=Red]1- ADDED THE PPAs:[/COLOR]
FROM 
[https://launchpad.net/~blueman/+archive/ppa]("https://launchpad.net/%7Eblueman/+archive/ppa")
 and 
[https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")

[COLOR=Red]2-INSTALLED[/COLOR]
 blueman
pavucontrol

Then

[COLOR=Red]3- [/COLOR]I followed the instructions @ [http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/) [COLOR=Red]FOLLOW THOSE TIPS CAREFULLY, UNTIL YOU HAVE FOUND OUT WHAT WORKS FOR YOU![/COLOR]

Even though I don't know whether that made any difference, I did create and edited the .asoundrc file, because I couldn't find it in my /home folder.

As a side note, I created a launcher on my desktop to load the ALSA module with the following command [this is the only way that I could see the volume controls for my bluetooth device with Pulse Audio Volume Control (or pavucontrol, for short)]: ([COLOR=Red]pactl load-module module-alsa-sink device="bluetooth" [/COLOR]) , without the parenthesis, of course :lolflag:
[SIZE=5]The trick is TO [COLOR=Red]NEVER GIVE UP[/COLOR]!!!

[SIZE=6]GOOD LUCK TO ALL! ):P[/SIZE]
[/SIZE]

---

### Post by GAMaus on 2009-11-28
Works for me like this:

Ubuntu 9.10
Motorola HT820 Bluetooth Headset/Headphones
Old MSI Bluetooth Stick

I have done this on both my Laptop and Desktop PC and it works.
So chances are good it will work for You too.

In Advance: Sorry for my english, i'm form Germany.

Following Packages are installed via Synaptic:

blueman    1.10-3ubuntu1 (graphical Bluetooth manager)
bluetooth  4.51-0ubuntu2 (Bluetooth support)
libgnome-Bluetooth7   2.28.1-0ubuntu2 (Gnome BT Tools - support library)
gnome-bluetooth   2.28.1-0ubuntu2  (Gnome BT Tools)
pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4  (Bluetooth module for Pulseaudio sound server)
bluez   4.51-0ubuntu2  (BT Tools and deamons)
libbluetooth3   4.51-0ubuntu2  (Library to use the Bluez Linux BT Stack)
bluez-btsco   1:0.50-0ubuntu3  (Bluez BT SCO tool)
bluez-gstreamer   4.51-0ubuntu2  (BT GStreamer support)
bluez-alsa   4.51-0ubuntu2  (BT audio support)

restart

connect and bond your Headset via the Blueman-applet

connect the a2dp-service:
[[img]http://www.picture-hoster.de/bild.php/2,4293,bildschirmfotobluetoothgeraete3DAZ7.png[/img]](http://www.picture-hoster.de/archiv.php?bild=4293&bild_name=bildschirmfotobluetoothgeraete3DAZ7.png)

right-click the Volume-applet (Speaker) in your taskbar.
choose Properties. In the opened window choose Output -> choose your Headset:

[[img]http://www.picture-hoster.de/bild.php/2,4294,bildschirmfotoaudioeinstellungenAKZO9.png[/img]](http://www.picture-hoster.de/archiv.php?bild=4294&bild_name=bildschirmfotoaudioeinstellungenAKZO9.png)


Now you should hear nice high def Stereo-Sound (You should open a player, of course ;) ).

Note: The Stop/Play buttons on my Headset don't work, maybe someone can tell me how to get them to work.

/edit: 
Got the buttons working.
just add uinput at the end of your /etc/modules file.

---

### Post by vertago1 on 2010-02-22
I was able to get it my headset to work by the following:

First one of the times I put my headset in pair mode, kbluetooth popped up the pairing dialog for entering the 4 digit pin. After entering the pin it was able to connect.

To get pulseaudio to recognize it I had to:

> 
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover


I also installed pavucontrol for changing the headset between duplex and high-quality audio modes.

I tried to get the buttons to work by modprobing uinput but haven't had any luck yet.

---

### Post by VitaLiNux on 2010-02-27
> **vertago1 said:**
> I was able to get it my headset to work by the following:

First one of the times I put my headset in pair mode, kbluetooth popped up the pairing dialog for entering the 4 digit pin. After entering the pin it was able to connect.

To get pulseaudio to recognize it I had to:



I also installed pavucontrol for changing the headset between duplex and high-quality audio modes.

[COLOR=Red]I tried to get the buttons to work[/COLOR] by modprobing uinput but haven't had any luck yet.
Which buttons do you mean? Have you had any complete success on that?

---

### Post by vertago1 on 2010-02-27
> **VitaLiNux said:**
> Which buttons do you mean? Have you had any complete success on that?

well my headset has media buttons and a call button ( play/pause, back forward, call). Still no luck

---

### Post by VitaLiNux on 2010-04-15
> **GAMaus said:**
> 

Note: The Stop/Play buttons on my Headset don't work, maybe someone can tell me how to get them to work.

/edit: 
Got the buttons working.
just[COLOR=Red] add[/COLOR][SIZE=5] uinput [/SIZE]at the end of your[COLOR=Blue] /etc/modules[/COLOR] file.

Hey, you rock, GAMaus! I did as you suggested and [SIZE=7]it did work flawlessly!:guitar: :KS:KS:KS:KS:KS[/SIZE] Maybe if vertago1 or others that have an A2DP bluetooth headset like mine (originally I had Nokia BH-501, this model doesn't have multimedia keys, but I upgraded to a Nokia BH-503 which does have these buttons and GaMaus' fix did the trick for me:popcorn:

Man, What'd we do without this beautiful community, where we share fixes and new ideas? Awesome! After I made the official jump on September 2007 on the Linux Bandwagon I have to say I feel no regrets at all!

---

### Post by HyperHacker on 2010-06-18
Alright, I got A2DP working almost perfectly with Pulse so far on 10.04. All I had to do was:
> **Kryzzalid said:**
> i wrote in ~/.asoundrc:

pcm.headset {
type bluetooth
device XX:XX:XX:XX:XX  #(write your own headset address found with the command hcitool scan)
profile "auto"
}The profile line was the trick; once I did that, it worked.
I did also add the PIN in /var/lib/bluetooth as described a bit earlier in the thread, but I'm not sure if that was actually necessary.
(Mine is also a Nokia BH-503.)

However there are some minor issues:

1) When I first connect the headset, it's turned off in pavucontrol. Any time I change its profile, it goes to full volume, even though the slider still shows 30% as it was before. Poking the slider corrects it.

2) The buttons on the headset don't work. I did "sudo modprobe uinput" and nothing seems to have happened. Haven't tried rebooting.
What's odd about this is the volume buttons do respond, but only in HSP mode. In A2DP mode, they seem to adjust the volume on the headset, rather than on the PC - pavucontrol shows no change. (Maybe this is normal behaviour for A2DP?)

3) Seems to be a problem with xfce4-mixer-plugin: no PulseAudio controls are listed, which means the headset volume can't be adjusted from that button (using the scroll wheel) like other cards can. Is there perhaps a PA-friendly version of this plugin, that maybe shows one button per output device in the notification area?

Regardless of those issues, the sound seems to be working great after these tweaks. (Let's see for how long, though? :p)

---

### Post by Doublehelix22 on 2010-07-20
> **GAMaus said:**
> Works for me like this:

Ubuntu 9.10
Motorola HT820 Bluetooth Headset/Headphones
Old MSI Bluetooth Stick


[COLOR=Blue]
Thanks so much for this- I used it to improve abysmal sound quality on my bluetooth speaker and it's definitely helped[/COLOR] :KS

---

