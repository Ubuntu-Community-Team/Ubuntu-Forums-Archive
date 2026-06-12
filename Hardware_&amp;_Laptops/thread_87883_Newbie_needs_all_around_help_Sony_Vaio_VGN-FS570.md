---
title: "Newbie needs all around help Sony Vaio VGN-FS570"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by the~jester on 2005-11-09
I am a newbie to Linux and I know that Linux and the Sony Laptops don't get along to well. I have tried to various other distros with no luck in several areas. Fedora FC3 and FC4, Suse 9, earlier versions of Ubuntu and others. The main areas are issues with video res. , sound, and wireless. So I have to decided to try the latest Ubuntu after the live CD booted with the wireless working right away.

I found the following link [http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/) that talked about several areas that I have experienced issues with.

I followed the steps for getting the video resolution to work and for the most part it does. The only part that does not work is I have to manually enter the command to get 1280 x 800 after each boot. I did the section  " Add the line 915resolution 3c 1280 800 after the line : [ -f /etc/default/rcS ] && . /etc/default/rcS" and still no luck. I think i might have resolved that, in that like a nub I didn't not specify the full path to the file when I added it. I have corrected that and hopefully after the next reboot it should automagically make the need change so that it boots up as 1280 x 800.

So with screen res being 1280x800 (for the most part) and the wireless working straight out of th box, the next step is to get audio working. Volume control shows 2 devices: HDA Intel (ALSA Mixer) and Realtek ALC260 (OSS Mixer). Any ideas? I tried the above link but ran into errors. I have attached the config.log for the attempt.

Here are the results from a lsmod regarding sound.

snd_hda_intel          15872  2
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm


Thanks
jester

---

### Post by scubajeff on 2005-11-09
jester,

try this [http://usefulinc.com/edd/notes/UbuntuOnSonyVaioTRSeries]("http://usefulinc.com/edd/notes/UbuntuOnSonyVaioTRSeries")

---

### Post by the~jester on 2005-11-09
Thanks, that site should prove very useful when I start working on the stuff, right now I am focusing on getting sound to work first before I move on to something else. Unless I missed something there is nothing on that link that deals with getting sound working. I am focusing on getting that to function first before the other features. I want to get at least the basic function working so I can play with *nix to see if I can get away from Windoze completely.


jester

---

### Post by scubajeff on 2005-11-09
user alsamixer, and try to turn off the "External Amplifier" switch.

---

### Post by the~jester on 2005-11-09
Thanks, that helped somewhat. after pulling up the alsamixer like you suggested I was not able to find an "external amplifier". Like any other knob out there I just started mucking with things. I muted the headphones and once that was done I now get sound from the speakers. Any reason why this would work? does this mean now, that if I want to listen to sound through the headphones I have to go back and muted the speakers and  unmute the headphones. 

Thanks for the help scubajeff

with the bare essentials working I can now start to experience linux as a user and see how it goes. BTW, adding the full path to the 915reolution command to the /etc/init.d/bootmisc.sh file, made it successful in starting up in wide screen mode.

---

### Post by scubajeff on 2005-11-09
jester,

in alsamixer, go to preference menu, check "External Amplifier", than you will got the chance to switch it off in mixer. I have a Sony TR2, the default installation turn that switch on on my machine. I remember some other people who have Sony Vaio notebook all have the same problem. This should be a bug. And I hope it will solve the sound problem in your case.

---

### Post by the~jester on 2005-11-10
I was able to get sound working but, by muting the headphones. I do not have an option for an external amp in the alsamixer.

I am experience a new issue inwhich images from sites don't appear in firefox. If I got a site like [www.ilovebacon.com](www.ilovebacon.com) I can see the images of the website but if I go to another site, [www.dumbassdaily.com](www.dumbassdaily.com) I do not see any images at all on the site. Anyone have any ideas?

thx
jester

---

### Post by zonk on 2005-11-10
Like I wrote in another thread before: 
For problems with graphics maybe take a look at:

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

I don't know if this really helps, but this should at least be the "correct" chipset driver. It is even reported to work with your laptop. 
Maybe that helps.

Good luck.

zonk

---

### Post by the~jester on 2005-11-10
The video so far is working fine.. The issue with images was due to a corruption of the firefox profile. I moved ~jester/.mozilla to ~jester/.mozilla_backup Restarted mozilla and the images appeared.

jester

---

