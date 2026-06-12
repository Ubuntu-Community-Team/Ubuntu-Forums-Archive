---
title: "[SOLVED] multiple sound cards and pulseaudio issue"
date: 2008-09-24
forum: Hardware
---

### Post by sakuramboo on 2008-09-24
I have two sound cards (ATI SB700/SB800 Azalia and Creative Audigy Platinum). Both are detected perfectly. The issue comes when I try to use either of them. If I go to the sound settings in the system preferences, I select the Audigy to be the default, I need to put everything to ALSA, but then I get errors about how it can only use 1 audio program at a time. If i put everything to pulseaudio, all the levels moves as if there is sound, but there is non and the front face panel doesn't work.

If I put the default to the Azalia and put everything to pulseaudio, everything seems to work, except for when I reboot, sometimes the Audigy becomes the default device and I need to manually change it every time, and even after changing it, some programs are still trying to use the Audigy device.

I have gone into the Pulseaudio device manager and selected the Azalia to be default and they are checked.

I have tried to get some help on IRC, I was told to add emu10k1 to /etc/modules, but after doing that, I got no sound at all.

---

### Post by markbuntu on 2008-09-24
You are very close to getting this to work. Congratulations!

For getting the rest of the way you can look at my guide to multiple sound cards here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

You can also look through my other guide here about getting all your sound applications to share the sound cards and then you can use as many applications as you care to with either card or with both.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sakuramboo on 2008-09-28
Thanks for the reply, but, because of time constraints, I had to remove the sound card and go back to the on-board sound card.

Unfortunately, now, not all programs will use the sound card and those that don't use it right, upon closing, locks up the program and I have to kill -9 them to terminate them.

I reverted everything back to the way it was before I started messing with this, but I am not sure what I am missing to have this problem still plague me.

Any idea on where to look to fix this or at least figure out whats causing it?

I double and triple checked to make sure that the Azalia is the default device.

---

### Post by markbuntu on 2008-09-28
You should still look in the second link I posted above, it has solutions to that problem,

---

### Post by sakuramboo on 2008-09-28
That is the thing, I have looked at both links and my problem isn't listed.

It's not that I get no sound, I do, Audacious, Moc Player, Mplayer, Youtube videos all work fine. But, there are a few games that get no sound, Regnum, Abuse, Spring and probably some I haven't tested yet.

Before I messed around with this, everything worked, now, after messing with the sound cards, those three games get no sound and when I try to close the program, it locks and I have to force kill them.

---

### Post by markbuntu on 2008-09-28
There is a section Multiple Application Sound Sharing. The first part will help you set your sound to the defaults you started with. The rest will get your applications to share sound properly. 

Once you get that working, if you still have a problem with those games, come back here and we will try to help you. If you just slow down a little and take some time to read things, you will learn and understand how sound in ubuntu works and be able to fix the problems yourself.

---

### Post by sakuramboo on 2008-09-29
Well, like I said, I get sound. Sound works, but after messing with the modules, select games don't and will only close with a kill -9.

I have read all the links from what you gave me and the links within those links. This is why it is a real head scratcher for me. Everything seems to work just fine, except for the games. And even weirder is, not all games are affected. Savage 2 works perfectly, but I have been testing all the other games I have and everyone seems to suffer the same problem. No sound and have to be closed with kill -9.

It's not a sound card sharing issue because I can run Moc Player, Mplayer, youtube videos all at the same time without any issues. I do have one error message in /var/log/messages.

Sep 29 16:23:28 sakuramboo-desktop kernel: [  419.385074] hda-intel: Invalid position buffer, using LPIB read method instead.

But, I am not sure if that is a problem or not.

---

### Post by markbuntu on 2008-09-29
What sound servers are these games trying to use?
If it is OSS, you can launch them with aoss or padsp before the application name. Otherwise, if they are trying use portaudio or something else you can try pasuspender.
If you can, set them to use ALSA or OSS.

Are you playing these through wine?
If so, you need to look here:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

But you have probably tried that already.

---

### Post by sakuramboo on 2008-09-29
I believe that all the games are using ALSA, but I am not 100% sure. I just tried to run Abuse with padsp as well as pasuspender and same thing happened.

As for WINE, I do not use it, I am talking about all native Linux games.

---

### Post by markbuntu on 2008-09-29
When you launch these games from a terminal do you get any messsages?

---

### Post by sakuramboo on 2008-09-29
Just the regular output of the game. Nothing that signifies a problem.

---

### Post by markbuntu on 2008-09-30
When they are playing do they show up in the PulseAudio Volume Control/Output?

---

### Post by sakuramboo on 2008-09-30
Yip, each game shows up in the PulseAudio Volume control, they are not muted and they are pointing to the correct stream.

---

### Post by markbuntu on 2008-09-30
But your have no sound from them?
Are they using a plugin?

---

### Post by sakuramboo on 2008-09-30
No sound, the Volume Meter doesn't even move.

I have all the proper plugin's installed.

And, also, it's not just that there is no sound, but to close them, I need to `kill -9` them.

---

### Post by markbuntu on 2008-09-30
But they are in the volume control right?
What does it say is playing, exactly.

---

### Post by sakuramboo on 2008-09-30
ALSA plug-in [abuse]: ALSA Playback

---

### Post by markbuntu on 2008-10-01
Ok. try editing the launcher to 

pasuspender abuse

or pasuspender whatever the app is called. This will suspend pulseaudio while that application is running and maybe it will work. Let me know.

---

### Post by Dark9204 on 2008-10-01
The easiest way to solve this is to disable one of your sound cards.
I had this issue myself at first.
First find out what module name your sound card has by running this command in terminal: sudo asoundconf list
Then set the default sound card with this command: sudo asoundconf set-default-card mondulename.

Then to disable the other sound card, take the other sound cards mondule name from the list and edit this file as sudo: /etc/modprobe.d/blacklist
Then add: blacklist modulename to the end of that file.

Now restart your computer.

---

### Post by sakuramboo on 2008-10-01
@ markbuntu - I tried that when you first mentioned it and it still didn't work.

@ Dark9204 - I removed the second sound card after running into this problem. So, right now, I only have one sound card.

---

### Post by markbuntu on 2008-10-02
Do you have these:

libasound2 (alsa libraries)
libasound2-plugins (jack, OSS, pulseaudio)

If not, you could be missing some necessary plugin that the games need. Where did you get these games anyway?

---

### Post by sakuramboo on 2008-10-02
sakuramboo@sakuramboo-desktop:~$ dpkg -l libasound2 libasound2-plugins
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libasound2     1.0.15-3ubuntu ALSA library
ii  libasound2-plu 1.0.15-1ubuntu ALSA library additional plugins

Some of the games I got from the official repository, some from getdeb and some from binary install. There is no comparisons that I can think of that would be causing this.

---

### Post by markbuntu on 2008-10-02
You got a list, I will give some of them a try.

---

### Post by sakuramboo on 2008-10-02
Regnum Online - no sound/wont close
A7xpg - no sound/ wont close
Abuse - no sound/ wont close
Adonthell - no sound/wont close
Battle for Wesnoth - no sound/wont close
Boson - crashes when starting a mission
Bos Wars - no sound/wont close
Chromium - no sound/wont close
Dogin Diamonds 2 - no sound/wont close
Eschalon: book 1 - no sound
Falcon's Eye - sound on in the intro and outro, no ingame sound
fce ultra - ROM's wont load/game window wont close
GL-117 - sound for a split second, then no sound/wont close
Glest - no sound
Globulation 2 - no sound/wont close
Grid Wars - no sound
Gunroar - no sound/wont close
KETM - no sound
Kobo Delux - no sound/wont close
KQ - no sound
Mu-cade - no sound/wont close
Nexuiz - no sound/wont close

I'll just stop there seeing as how I'm at the half way mark with the games list.

However, I do want to say that the only game that seems to work without a problem is Savage 2.

---

### Post by markbuntu on 2008-10-02
Welll, I just tried abuse,lol.  When I fisrt started it from a terminal, I got a message:

Sound: disabled, could not find sfx directory or something like that 

so I installed the abuse-sfx package and it worked, sort of. It keeps opening and closing the audio stream, like flash does without libflashsupport. 

The game Opens and closes and plays just fine for me except for the glitchy audio but that works too.

---

### Post by sakuramboo on 2008-10-03
The thing is, though, before I started messing with the sound cards, everything just worked. The setup I had before is exactly the same way I have it now. Except, now I have this problem.

And like I said, Savage 2 is the only game that doesn't have this problem.

EDIT: I just tested On The Rain Slick Precipice of Darkness and I got an error message when starting that said it could not detect an audio driver and will shut down.

I think this is the best clue as to figuring out what the problem is.

EDIT 2: Also, alsamixer reports that the sound card is PulseAudio instead of the SB card that it should be.

EDIT 3: I took a look at the /etc/asound.names and /var/lib/alsa/asound.state files and both seem to be okay, however, `sudo alsactl names` returns nothing when "SB" should have been printed.

I tried `sudo alsactl restore` which did nothing and `sudo alsactl -F restore` with the same result.

I believe this is where the issue is. PulseAudio is being listed as the audio device when SB should.

EDIT 4: Here is my ~/.asoundrc.asoundconf file. Do you see anything wrong with it?```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default { type pulse }
ctl.!default { type pulse }
desfault SB
default SB
!defaults.pcm.card SB
defaults.ctl.card SB
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
```

EDIT 4: BAM! I got everything working. I ran the following commands to get it working...

asoundconf unset-pulseaudio #This gave alsamixer the right device
asoundconf delete desfault #That is probably another error that was screwing everything up.

Then I rebooted and now everything works flawlessly. Thanks so much for your help.

---

