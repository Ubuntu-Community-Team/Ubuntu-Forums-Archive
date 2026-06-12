---
title: "Ubuntu on HP Envy Spectre 14"
date: 2012-12-14
forum: Hardware
---

### Post by IamNotANerd on 2012-12-14
Hi,

I am thinking of buying this laptop but I'd like to know if there are any serious issues in hardware compatibility before actually buying it. So, anyone who owns the Spectre and would be kind enough to share the info? Googling didn't turn up anything useful.

I am planning to do a fresh install of either Ubuntu 12+ or Xubuntu... (Might even venture to try Fedora on this, but that's off topic).

Thanks in advance.

---

### Post by Calinou on 2012-12-14
Should work fine (like nearly any other laptop, basically).
BTW, I advise not buying an ultrabook. Their price is also, "ultra". More overpriced than Apple hardware sometimes. :D

---

### Post by IamNotANerd on 2012-12-15
Thank you, Calinou, but I'm still anxious to know more details and specifically how some of the gimmicks/components affect other components:

- NFC (Doesn't need to work)
- webcam
- keyboard backlight
- wireless
- had some sort of "smart cooling" (could be software driven)

Things like NFC radio aren't on the priority list but who knows if it causes unsolvable problems etc.

Other Envy series laptops have given hard times for Ubuntu users in the past...

---

### Post by russomarco on 2013-09-04
I bought an HP Envy 14 Spectre 3100-el and everything works out of the box with Ubuntu 12.04, except:

- the red Beats light (which I don't really care about)
- the Beats software button to customize sound (though you can install pulseaudio-equalizer or other sound equalizer to enhance your sound) 
- the extra gestures of the touch pad (the two-finger scrolling works both vertically and horizontally, but other more specific gesture don't, though I think you can fix it with little programs like touchegg, synaptiks or gpointing-device-settings, I haven't tried it yet)

The keyboard backlight proximity sensor wouldn't work at first, but started to work after a BIOS update.

---

### Post by IamNotANerd on 2013-09-07
Hey, thanks for contributing to this thread!

I bought the Envy too (cause I think it's just so cool, call me vain), but so far everything's worked smoothly except:

- nfc chip (though I don't need it, so haven't bothered)
- touchpad is REALLY sensitive (like you're going to unintentionally click a number of things)
- fans kick in randomly draining the battery, sometimes spinning 3-5 secs at full speed
- subwoofer didn't work, but fixed it with hda-jack-retask (followed this thread [http://www.reddit.com/r/linux/comments/17sov5/howto_beats_audio_hp_laptop_speakers_on/](http://www.reddit.com/r/linux/comments/17sov5/howto_beats_audio_hp_laptop_speakers_on/))

Other than that, I'm quite pleased. Although I can't stress enough how sensitive the touchpad is: right clicking links is HARD. Most of the time, if you're in a hurry, it'll end up being just a left click OR better yet -- a left click on a link nearby! I tried solving this with a synaptics driver (found it on the forums, didn't help that much) and with synclient. 

The button area on the touchpad registers finger movement by default which is quite annoying. Indeed, I tried to fix this with synclient by reducing the BottomEdge value (moving the movement registering area upwards effectively) but then it wouldn't register right click anymore! 

If anyone knows a way to control the fan frenzy I'd be really rather happy!!

All in all, I confirm that minor issues aside, everything's working.

---

### Post by russomarco on 2013-10-26
> **IamNotANerd said:**
> Hey, thanks for contributing to this thread!

I bought the Envy too (cause I think it's just so cool, call me vain), but so far everything's worked smoothly except:

- nfc chip (though I don't need it, so haven't bothered)
- touchpad is REALLY sensitive (like you're going to unintentionally click a number of things)
- fans kick in randomly draining the battery, sometimes spinning 3-5 secs at full speed
- subwoofer didn't work, but fixed it with hda-jack-retask (followed this thread [http://www.reddit.com/r/linux/comments/17sov5/howto_beats_audio_hp_laptop_speakers_on/](http://www.reddit.com/r/linux/comments/17sov5/howto_beats_audio_hp_laptop_speakers_on/))

Other than that, I'm quite pleased. Although I can't stress enough how sensitive the touchpad is: right clicking links is HARD. Most of the time, if you're in a hurry, it'll end up being just a left click OR better yet -- a left click on a link nearby! I tried solving this with a synaptics driver (found it on the forums, didn't help that much) and with synclient. 

The button area on the touchpad registers finger movement by default which is quite annoying. Indeed, I tried to fix this with synclient by reducing the BottomEdge value (moving the movement registering area upwards effectively) but then it wouldn't register right click anymore! 

If anyone knows a way to control the fan frenzy I'd be really rather happy!!

All in all, I confirm that minor issues aside, everything's working.

I agree with you about the touchpad sensitivity! 

Which model of the HP Envy do you own? Because on my HP Envy 14 Spectre 3100-el I couldn't fix the subwoofer. I followed the guide on your link, but to me it seems like nothing changes. Did you use exactly the parameters in the link ([COLOR=#000000][FONT=verdana]0x0d Internal speaker, [/FONT][/COLOR][COLOR=#000000][FONT=verdana]0x0f Internal speaker, 0x10 Internal speaker LFE)?[/FONT][/COLOR]

---

### Post by IamNotANerd on 2013-11-03
Hi,

I couldn't find model number (not printed on the back, BIOS didn't have info etc.). Anyway, I did follow the guide in setting the parameters. Basically, it should be the same with every HP Envy laptop because they all have the same Beats Audio chip (remember reading that somewhere). Although, I had trouble with pulseaudio and solved the issue following this comment:

> Ok so just got it all working. Awesome for one! Haven't rebooted yet but I'm not really worried.
  But also for people that may have the same issues I had (say on  Xubuntu) (people that are a bit paranoid / security-conscious should see  my following comment first probably btw):
  **Issue 1**: At step 8, a few seconds after clicking "Apply" I would get the message:
  [INDENT] tee: /sys/class/sound/hwC0D0/reconfig: Device or resource busy
 [/INDENT]  And Google pointed me to a bug[1] where David Henningsson himself says[2]:
  [INDENT] You probably need to kill pulseaudio:
  echo autospawn = no >> ~/.pulse/client.conf killall pulseaudio
  Also check with
  sudo fuser -v /dev/snd/*
  for other processes currently using sound cards.
 [/INDENT]  For me
  sudo fuser -v /dev/snd/*
  listed "xfce4-volumed" and "pulseaudio" so I did:
  echo autospawn = no >> ~/.pulse/client.conf
killall pulseaudio
pkill xfce4-volumed
  Then got the "do a test" kind of message after clicking "Apply". To  get my xfce volume thing to work I had to start the stuff up that I  killed:
  xfce4-volumed
  and
  pulseaudio
  in a terminal. Though "pulseaudio" doesn't spawn off a daemon, it  keeps running, so it would be better to do that through the Alt-F2 run  dialog. Might also want to rename or remove that "~/.pulse/client.conf"  file to avoid possibly making pulseaudio troubleshooting more  complicated in the future.
  **Issue 2**: I wasn't getting any subwoofer output until  I saw a new thing in alsamixer called "Speaker 1" and set the volume to  non-zero. Seems to be a control for the subwoofer while "Speaker" does  all the four other speakers.
  **Issue 3**: Headphones muted Killing pulseaudio resets  volume to mute on a lot. I think I've encountered this before. Just  after plugging in headphones, raising the volume in "alsamixer" for  "Speaker" worked fine.



If it works, you should see a control for subwoofer in Sound Settings if you choose Analog Output. Then just apply Boot Override in hda-jack-retask and it should work on every boot.

ps. I recommend running hda-jack-retask from the terminal to see any error messages. Good luck!

---

### Post by russomarco on 2013-11-04
I followed everything in that post: I was able to apply the changes and install the boot override with hda-jack-retask, but nothing changes. The only differences are that the audio profile in the Sound settings menu is now "Analog Surround 4.0 Output" (before it was simply "Analog Stereo Output") and controls for Subwoofer and Fade appeared, but the Subwoofer is not active (grayed out), and if I try to do a sound test the rear speakers don't work... Could you check if the Sound settings and alsamixer look the same on your envy 14? Or upload a screenshot.. Thanks!

[IMG]http://i40.tinypic.com/e5mrza.jpg[/IMG]

[IMG]http://i42.tinypic.com/2vw8ehv.png[/IMG]

---

### Post by laurens.rietveld on 2014-09-07
hda-jack-retrask did not work for me (spectre 13).
Instead, the solution mentioned [here]("https://bugzilla.kernel.org/show_bug.cgi?id=74841") fixed my problem: install alsa-tools, and run 'sudo hda-verb /dev/snd/hwC1D0 0x1a 0x795 0x00'
Future kernel version should include this fix

---

