---
title: "HP Docking Station Headphone Jack Does Not Work"
date: 2009-11-02
forum: Hardware
---

### Post by poctob on 2009-11-02
I am not able to get the headphone jack working on HP docking station/port replicator.  I am running Karmic 9.10 on HP EliteBook 6930p.  Built-in headphone jack works fine and properly mutes the internal speakers.  When I plug the headphones into the docking station the internal speakers still have sound and there is no sound in the headphones.  I did not test the microphone using the docking station, but I suspect the results would be the same.  Seems like the system doesn't even recognize that there are additional headphone jacks.

Did anyone have a similar issue.  My alsa details are posted at the following link:
[http://pastebin.ca/1653082](http://pastebin.ca/1653082)

Thanks.

---

### Post by wladyx on 2009-11-05
I have the same issue.

---

### Post by laidback82 on 2009-11-05
Same problem here with HP DV-7 series laptop. It seems very strange. internal speakers work fine, and continue to work when I plug in speakers/headphone. Annoying.

---

### Post by m3741 on 2009-11-05
I'm running Karmic x64 on an HP 8530w with a dock and was having the exact same issue. Alsa detects the port but for some reason it doesn't show up in the sound preferences. That'll probably take a person smarter than me to fix. To get your sound going though, fire up a terminal and type:```
amixer -c 0 sset Dock,0 unmute
```

However, doing so doesn't mute the internal speakers. If you run amixer from terminal it'll list everything that alsa detects AFAIK but I can't find anything to mute that'll fix it. I just turned my real speakers up louder...

---

### Post by m3741 on 2009-11-05
Now I'm thoroughly confused. While I was screwing with the sound I had Rhythmbox playing the whole time. Eventually my playlist ran out. After I started it up again to play around some more, I noticed that it worked exactly as expected. The dock speakers are on and the internal ones off. Also, the touch mute button thing went from blue (not muted) to orange (muted). Strange but exactly like Intrepid if I remember correctly.

I'm feeling lazy and don't feel like rebooting at the moment to try to reproduce it. Anyone else? What's your experience?

P.S. - I found a slightly easier way (I guess) to get the sound on. Fire up alsamixer from a terminal, move over to "Dock" and press "M". Hmm... I guess I'm a happy camper now.

---

### Post by laidback82 on 2009-11-05
Sadly none of these work for me. I've now noticed that the only speaker I get sound out of is the bass speaker on the bottom of the laptop. This is infuriating.

---

### Post by m3741 on 2009-11-06
Show me the output of "amixer scontents" from the terminal. Let's see what you've got. I'm not very familiar with that laptop.

---

### Post by wladyx on 2009-11-06
[http://pastebin.com/f4ccd89fe](http://pastebin.com/f4ccd89fe)

---

### Post by poctob on 2009-11-06
In my case control option "Dock" is not even available in the amixer or alsamixer.

---

### Post by poctob on 2009-11-06
OK, I got it to work.  I had to edit /etc/modprobe.d/options.conf and comment out mobile option:

```
#options snd-hda-intel model=mobile
```


After reboot I have dock option in alsa mixer.  Laptop internal speaker can be muted using mute button on the laptop itself.  The annoying thing is that the sound preferences applet in Karmic has been dumbed down to a point where a user has absolutely no control over the sound except the master volume and balance.

---

### Post by wladyx on 2009-11-06
ls -al /etc/modprobe.d/
total 48
drwxr-xr-x   2 root root  4096 2009-11-06 17:41 .
drwxr-xr-x 137 root root 12288 2009-11-06 14:51 ..
-rw-r--r--   1 root root  2497 2009-10-12 01:07 alsa-base.conf
-rw-r--r--   1 root root   325 2009-09-16 00:55 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 2009-09-16 00:55 blacklist.conf
-rw-r--r--   1 root root   213 2009-09-16 00:55 blacklist-firewire.conf
-rw-r--r--   1 root root   662 2009-09-16 00:55 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 2009-10-12 01:07 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 2009-10-23 13:47 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  1077 2009-09-16 00:55 blacklist-watchdog.conf
-rw-r--r--   1 root root    16 2009-08-26 12:51 libpisock9.conf


no options.conf on karmic.

---

### Post by poctob on 2009-11-06
> **wladyx said:**
> ls -al /etc/modprobe.d/
total 48
drwxr-xr-x   2 root root  4096 2009-11-06 17:41 .
drwxr-xr-x 137 root root 12288 2009-11-06 14:51 ..
-rw-r--r--   1 root root  2497 2009-10-12 01:07 alsa-base.conf
-rw-r--r--   1 root root   325 2009-09-16 00:55 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 2009-09-16 00:55 blacklist.conf
-rw-r--r--   1 root root   213 2009-09-16 00:55 blacklist-firewire.conf
-rw-r--r--   1 root root   662 2009-09-16 00:55 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 2009-10-12 01:07 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 2009-10-23 13:47 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  1077 2009-09-16 00:55 blacklist-watchdog.conf
-rw-r--r--   1 root root    16 2009-08-26 12:51 libpisock9.conf


no options.conf on karmic.



Try searching for it in other files, it may be in alsa-base.conf
```
grep mobile /etc/modprobe.d/*
```

If it is not there, you may have a different issue.

---

### Post by poctob on 2009-11-06
> **wladyx said:**
> ls -al /etc/modprobe.d/
total 48
drwxr-xr-x   2 root root  4096 2009-11-06 17:41 .
drwxr-xr-x 137 root root 12288 2009-11-06 14:51 ..
-rw-r--r--   1 root root  2497 2009-10-12 01:07 alsa-base.conf
-rw-r--r--   1 root root   325 2009-09-16 00:55 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 2009-09-16 00:55 blacklist.conf
-rw-r--r--   1 root root   213 2009-09-16 00:55 blacklist-firewire.conf
-rw-r--r--   1 root root   662 2009-09-16 00:55 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 2009-10-12 01:07 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 2009-10-23 13:47 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  1077 2009-09-16 00:55 blacklist-watchdog.conf
-rw-r--r--   1 root root    16 2009-08-26 12:51 libpisock9.conf


no options.conf on karmic.

Actually I just looked at [http://pastebin.com/f4ccd89fe](http://pastebin.com/f4ccd89fe) and it shows that you already have Dock enabled.  From the terminal run 
```
amixer -c 0 sset Dock,0 unmute
```

That should unmute your dock sound.

---

### Post by m3741 on 2009-11-06
> **poctob said:**
> OK, I got it to work.  I had to edit /etc/modprobe.d/options.conf and comment out mobile option:

```
#options snd-hda-intel model=mobile
```


After reboot I have dock option in alsa mixer.  Laptop internal speaker can be muted using mute button on the laptop itself.  The annoying thing is that the sound preferences applet in Karmic has been dumbed down to a point where a user has absolutely no control over the sound except the master volume and balance.

I totally agree with you on the sound preferences. I'm looking in to getting the better one back. I remember seeing something about apt-getting gnome-alsa-mixer or something. I'll look it up again.

---

### Post by poctob on 2009-11-06
> **m3741 said:**
> I totally agree with you on the sound preferences. I'm looking in to getting the better one back. I remember seeing something about apt-getting gnome-alsa-mixer or something. I'll look it up again.

Thanks for the tip, I just installed gnome-alsamixer.  Much better alternative.  Don't bother with alsamixergui package though, it is total junk.

---

### Post by wladyx on 2009-11-10
> **poctob said:**
> Actually I just looked at [http://pastebin.com/f4ccd89fe](http://pastebin.com/f4ccd89fe) and it shows that you already have Dock enabled.  From the terminal run 
```
amixer -c 0 sset Dock,0 unmute
```

That should unmute your dock sound.

Thanks, that did the trick :)

---

### Post by felipe_mora on 2009-11-14
Thanks a lot people, i just install yesterday find here and found a solution great work ;):KS

---

### Post by SNR99 on 2010-01-28
Hi there
I stumbled across this thread as am having trouble with a docking station headphone jack which isnt producing any sound.  The headphone socket on the laptop works fine and the sound from the laptop also works fine.

I am running Ubuntu 9.10 and tried the amixer and there is not a Dock option.  There is an external option which is unmuted.

Also, dont have a /etc/modprobe.d/options file to edit so cant try that approach.

Are there any ideas out there?

---

### Post by poctob on 2010-01-28
> **SNR99 said:**
> Hi there
I stumbled across this thread as am having trouble with a docking station headphone jack which isnt producing any sound.  The headphone socket on the laptop works fine and the sound from the laptop also works fine.

I am running Ubuntu 9.10 and tried the amixer and there is not a Dock option.  There is an external option which is unmuted.

Also, dont have a /etc/modprobe.d/options file to edit so cant try that approach.

Are there any ideas out there?

Actual package name is gnome-alsamixer.  Try that one first.

---

### Post by colorprint on 2010-01-29
I have the same problem...
And I have no "Dock" option in gnome-alsamixer

---

### Post by poctob on 2010-01-29
> **colorprint said:**
> I have the same problem...
And I have no "Dock" option in gnome-alsamixer

Did you run ```
amixer -c 0 sset Dock,0 unmute
``` first?  See attached screenshot.

---

### Post by feenstra on 2010-03-16
Just my two cents. 

Un-muting 'dock' in gnome-alsamixer worked in getting output on my external speakers, but not muting the internal ones. 

Twiddling the mute button and volume controls on my laptop, and the mute buttons for master and pcm in gnome-alsamixer got me to a state where 'mute' is on for the internal speakers, while sound still comes out of the external ones. Unfortunately I don't remember the exact sequence - you know how that goes - and I don't have time to try and replicate now. (Besides, I don't want to interrupt the Breeders!)

Running karmic 64 (latest updates) on a HP 6930p, sound from Rhythmbox.

Hope this gives others a hint! :D

---

### Post by enigva on 2010-05-31
I do have the Dock option in alsamixer but I just can mute or unmute, when hiting + or up arrow to increase volume the program terminates...

Any idea?

---

