---
title: "System Sound Problems"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by AndyAWS on 2005-04-13
Hi,
I just installed Ubuntu ('Hoary') this weekend and I've been spending my time this week trying to get everything working normally.
Everything has worked out fine except for a minor and annoying sound problem.

If I go into the Gnome panel and enable Sound Server Startup, I get Gnome system sounds, but no sounds in games (i.e. Enigma, FrozenBubbles). If I disable Sound Server Startup I get game sounds but no system sounds.

In Multimedia System Select I have ALSA in Sink, and OSS in Source. Changing things around in there doesn't seem to make any difference.

I've tried the How-To for getting Multiple sounds to work, and that made no difference that I could tell.

Music Player works fine with MP3's regardless of my Sound Server Startup setting.

For now it's just a minor annoyance having to disable the Sound Server to play games. But I didn't have this problem with Mandrake Gnome, so there must be a way to fix it. I just don't want to keep trying various fixes at random from this forum because everytime I apt-get something that's supposed to fix the sound it uninstalls something else, no harm so far but I don't want to end up totally soundless.

Does anyone have any ideas?

---

### Post by dusu on 2005-04-13
Go and read, this may help
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by AndyAWS on 2005-04-13
Yes I've tried all of that, libesd-alsa0 is installed, I edited the esd.conf, and created the asound.conf file.

I still have to disable Sound Server Startup if I want to hear sounds in games, and enable it if I want system sounds. 

Other than that, all sounds, music, etc, work fine.

---

### Post by AndyAWS on 2005-04-13
Has anyone else had this specific problem?

Is the problem related to ESD, ALSA or OSS?

Am I still missing some ESD library or driver?

Or do I need to try different settings in esd.conf or asound.conf? If so, is there a reference somewhere to help determine what those settings should be for my particular hardware configuration?

---

### Post by AndyAWS on 2005-04-13
I've looked all over in this forum and can't find a fix for this exact problem. I'm assuming that the 'Sound Server Startup' in the Sound panel is refering to ESD, and that there is a problem with ESD working with ALSA.

1. Should I Install everything refering to ALSA with apt-get

or

2. Try installing polypaudio in place of ESD.

or

3. Play it safe and live without system sounds for now?

It seems like a simple stupid problem...all my sounds work, but not if gnome system sounds are on (Sound Server Startup enabled). Also multiple sounds at once seems to be working...I can play an MP3 and still have other sounds chime in.

---

### Post by ploum on 2005-04-13
Are you sure that the config of ESD says :

spawn_options=-terminate -nobeeps -as 2 -d default

(the important part here is -terminate -as 2)

---

### Post by AndyAWS on 2005-04-13
Here is my esd.conf:

[COLOR=Navy][esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=[/COLOR]

---

### Post by AndyAWS on 2005-04-17
Ok, I got it working but I'm not sure what all was needed to fixed the problem.

The last thing I tried was installing **libsdl1.2debina-all** then I set my sink to alsa and my source to alsa and in the sound panel turned on 'Start Sound Server'. After rebooting I have all sounds in all programs (as far as I know), including Gnome System Sounds, and multiple sounds at the same time.

I also had changed /etc/libao.conf from "default_driver=esd" to "default_driver=alsa" shortly before that.

I had also modified esd.conf as posted above and had setup 'asound.conf' as instructed in other posts to use dmix.

I also have installed some other ALSA packages as suggested in some other sound problem posts.

I can't really say what all was actually required, but installing the '-all' libsdl package was what finally did the trick.

---

