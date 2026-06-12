---
title: "MSI GT735 Laptop audio troubles."
date: 2009-04-07
forum: Hardware
---

### Post by em3raldxiii on 2009-04-07
I recently purchased an MSI GT735 laptop, and so far I am very happy with it.  However, I have sound only sorta-working, and I cannot figure out why sound does not work in games such as Frozen-Bubble and Chromium.  I haven't tested many other games, but I am assuming sound probably doesn't work in most other games.

It's important to point out that I have sound working for the system sounds, and for applications such as Audacity.  I had to enable ***[COLOR="Indigo"]IEC958 Default PCM[/COLOR]*** in my Volume Control preferences, then I had to check the checkbox.  I am not 100% convinced that was the true solution becuase I was doing many other things to try to get sound working before that; for example, I updated ALSA to the latest version using a script I found here on the forums.

From my LSPCI:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device

At this point, I am not sure which one is actually being used (not even sure how to check).  The laptop sound is 4.1; there is a subwoofer on the bottom.  The system sounds that I do have working sound EQ'd wrong, so I am thinking there is something else wrong that I am not aware of.

Just for anyone else with this laptop:  You have to install Ubuntu 8.04, since 8.10 hangs during a battery discovery step in the installation process.  Wireless networking is easily set up using the RALINK driver from their website.  There is a post about that somewhere on the forums (or linuxforums), I'll post a link if I find it again.

Cheers.

---

### Post by TheOmegaMan on 2009-04-18
Well I have slightly different problems with my MSI GT735. The only sound I do get is from the subwoofer. I can't get any of the other speakers to work correctly. 

BTW I'm currently using Ubuntu 9.04. Does anyone have any idea on what I can do. I do know in windows I have to enable the speakers through PCM speakers. I don't believe these speakers are connected via analog connection.

---

### Post by em3raldxiii on 2009-05-05
I have to ammend my original post ... it appears as if all sound does indeed only come from the subwoofer on the bottom.  Kinda annoying.  Any updates?

---

### Post by Cone on 2009-07-19
I'm also having this problem.  Sound only seems to come from the subwoofer at the bottom of the laptop.  I have tried upgrading to Alsa 1.0.20, but that didn't help.  Aside from that, this is a stock Ubuntu 9.04 install.

Any help would be greatly appreciated.

---

### Post by Cone on 2009-08-07
Adding
```
options snd-hda-intel model=6stack-dig probe_mask=1
```
to the bottom of my /etc/modprobe.d/alsa-base.conf and reloading alsa (killing the processes using it first, of course) got me sound through 2 speakers + the subwoofer.  Plugging in headphones also plays sound through the headphones, but doesn't cease to play it through the speakers as well.  Huh.

---

### Post by em3raldxiii on 2009-08-31
> **Cone said:**
> Adding
```
options snd-hda-intel model=6stack-dig probe_mask=1
```
to the bottom of my /etc/modprobe.d/alsa-base.conf and reloading alsa (killing the processes using it first, of course) got me sound through 2 speakers + the subwoofer.  Plugging in headphones also plays sound through the headphones, but doesn't cease to play it through the speakers as well.  Huh.

This gave me sound through my front speakers too, although I had to go into the sound volume controls, add some of the options in the preferences, and unmute/turn up some of the controls.

The sound quality is still not 100% - it sounds a little less bassy than it should, and I can't seem to get it as loud as I can with my original Vista installation.  It will be nice once these types of problems are totally resolved.  Serves me right for trying to be non-conformist and going with an MSI laptop, eh?  LOL, I totally love the machine though!  Pretty much everyone who ever sees it is like, "oooh, that's a fancy laptop" hehe ... ;)

---

### Post by em3raldxiii on 2009-09-10
It appears that either a recent update caused some trouble, or I reset something, but the sound stopped working.

The solution I found was to go to System > Preferences > Sound and then under the Devices tab, change all of the playback options to OSS.  It seems a little bit counterintuitive, but whatever, it works.

Cheers!

---

### Post by em3raldxiii on 2009-11-13
**UPDATE**:  A couple of days ago, I updated my laptop to Karmic.  Everything now works perfectly; I haven't played around with the audio settings, but by default everything works; sound is coming out of the mains, the fronts, and the subwoofer.  I will update the UbuntuTestingTeam page here:  [https://wiki.ubuntu.com/LaptopTestingTeam/MSIGT735]("https://wiki.ubuntu.com/LaptopTestingTeam/MSIGT735").

---

### Post by Rescue9 on 2009-11-27
Trying to run 9.10 persistently on a USB. I'm having the subwoofer only problem. If anyone knows a quick workaround for USB persistent, then I'd be happy. If not, then I'll try to troubleshoot.

---

### Post by _deepfire on 2010-01-05
> **em3raldxiii said:**
> **UPDATE**:  A couple of days ago, I updated my laptop to Karmic.  Everything now works perfectly; I haven't played around with the audio settings, but by default everything works; sound is coming out of the mains, the fronts, and the subwoofer.  I will update the UbuntuTestingTeam page here:  [https://wiki.ubuntu.com/LaptopTestingTeam/MSIGT735](https://wiki.ubuntu.com/LaptopTestingTeam/MSIGT735).

Unfortunately, I have a MSI GT735 and the subwoofer-only sound is there  in fresh install of 9.10.

---

### Post by defensorfedei on 2010-03-19
I have an MSI GX730, which is very similar to the GT735, only my machine uses an AMD processor and ATI graphics card.  As far as I can find out, both machines use the Realtek 1200 audio chipset.  

I have been able to get surround sound to work in my 9.04 installation by using the modprobe hack in my alsa-base.conf file and upgrading my alsa to 1.0.21rc3 (a while ago).  I have the same problem with sound still coming out of my speakers when I plug in headphones.

My biggest problem is this.  I cannot, for the life of me, get my built-in microphone, or any other microphone for that matter, to work. I also cannot record audio from my soundcard using audacity or arecord, even with a virtual loopback driver.  I uninstalled pulse audio and still nothing, in fact pulse audio seems to make absolutely no difference after adding the modprobe hack.

My question for everyone else is......can you get your mics working....and can you record audio directly form your soundcard?  It would seem to me that it is a bit premature to report audio success to the laptop testing team, when only one guy has got this thing working out of the box, and nothing has been said of the microphone or audio recording situation.  

Has anyone else had success with this Realtek 1200 chipset?  Has this issue been given up?

---

### Post by em3raldxiii on 2010-03-20
Regarding the microphone(s):  Both the front mic and the mic plug must be unmuted in alsamixer (or a mixer of your choice) before they will work.  You may also want to enable the boost option.  I haven't made any other changes to my system (except normal update) since my last post so I don't really know what the difference between the clean install versus the updated-install would be.

Sound does still come through the speakers when the headphones are plugged in.  I have to manually mute the mains if I want to control that :(

I have never tried recording audio directly from my soundcard on that machine, but I will try once I am back at it.

Messing with Pulseaudio only ever seems to make a difference with WINE applications in my case.

** I made a quick note on the laptop testing page.  The page doesn't belong to me, though, so please if you have something to add to that wiki page, go right ahead.

---

### Post by defensorfedei on 2010-03-21
Thanks for the quick reply.  I was able to get my mic working after setting my input device to front mic and turning up the front mic boost a bit.

I still cannot get arecord or audacity to do thy bidding when it comes to recording audio from the soundcard.  Actually, that is not true, since I was able to record audio with arecord, but it sounded like hell with all the static.  I still haven't figured out how to clean it up.

This post helped me quite a bit: [http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)

It is not ideal, but I am able to use Skype on my laptop now after about a year of trying.

As a further note, I could not get surround sound to work with pulse, and skype would not play nicely either, so I wound up uninstalling pulse altogether.  

I am curious though....what sort of sound configuration does your 9.10 installation use?  Do you have surround working with pulse in 9.10?

Be sure to let me know how your recording endeavors go.  I may wait it out and install Lucid anyhow, and pick my battles from there.

Thanks again.

---

### Post by Yellow Pasque on 2010-03-22
Did you try other models other than 6-stack-dig? What sound codec does this thing have? (post output of following command)
```
aplay -l
```

Frozen-Bubble and lots of other games/apps use SDL for sound. If you're running pulseaudio (comes pre-installed with Ubuntu), you'll generally have better luck installing libsdl1.2debian-pulseaudio and removing libsdl1.2debian-alsa.

---

### Post by defensorfedei on 2010-03-23
Hi there,

my aplay list is as follows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I have tried this option from this thread: [http://ubuntuforums.org/showthread.php?t=1159334](http://ubuntuforums.org/showthread.php?t=1159334), but it did not work...all sound still came from the subwoofer.
```
options snd-hda-intel model=auto probe_mask=1
```I really don't know what other options there are to get this thing working.  

I tried everything I could find on the net and manpages to get pulseaudio to work on my system, but I could never get all my speakers (7.1 Dolby surround) working.  I even tried manually mapping out each speaker for the pulseaudio server.  After I added the modprobe hack with the 6stack-dig, I was able to get my other channels to work with alsa.  Pulseaudio just would not give me any other options than 2-channel, and no mic.  That is why I uninstalled it, and upgraded Alsa.

I truly believe that the alsa drivers are not fully capable of running my sound card.  My system seems to be using the Azalia driver, which is for the ALC 888 chipset family.  It was really just luck that this driver can somewhat operate my ALC 1200.  

For capture devices, I have Front mic, mic, cd, and line-in.  No stereo mix or anything else that audacity could use.  I even tried Jackd and still nothing.  I suppose this is really just a waiting game, until the drivers and audio servers can catch up with the hardware.

I think I am going to try this: [http://ubuntuforums.org/showpost.php?p=7758827&postcount=19](http://ubuntuforums.org/showpost.php?p=7758827&postcount=19)
I will install the codecs from the Realtek website and try to configure pulseaudio once again.  I will post back with my results.  Thank God for Clonezilla!!!!

---

### Post by defensorfedei on 2010-03-24
No deal on the manual install.  Like I said before, I should be happy that I have sound and a working mic.  Maybe someday this thing will work out of the box.

---

### Post by em3raldxiii on 2010-06-25
Hey folx, so I ran across this thread, and it helped me with some similar issues with another machine ... I will test on my laptop later.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351)

Pay particular note to near the bottom where they suggest adding position_fix=1

-Mike

---

### Post by unuu on 2010-10-31
This is happening to me with my GT725, Ubuntu 10.10 Maverick Meerkat. And I always have to go to sound preferences to switch the audio from hdmi to analog. The sound is only coming out from the subs and not the top speakers.

UPDATE::

Using the information on this page I was able to fix the audio, but also the audio is coming in from speakers and headphones when my headphones are plugged in., no update has fixed this unfortunately.

[http://ubuntuforums.org/showthread.php?p=10087250#post10087250]("http://ubuntuforums.org/showthread.php?p=10087250#post10087250")

---

### Post by ruidc on 2011-02-20
on my GT725 I got the audio to cut out the main speakers when plugging in headphones by following this little extra config: [http://forum-en.msi.com/index.php?topic=137959.0](http://forum-en.msi.com/index.php?topic=137959.0)

unfortunately, the subwoofer stays on

---

