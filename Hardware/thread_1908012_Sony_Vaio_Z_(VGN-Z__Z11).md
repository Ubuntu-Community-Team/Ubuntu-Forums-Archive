---
title: "Sony Vaio Z (VGN-Z / Z11)"
date: 2012-01-12
forum: Hardware
---

### Post by Jason Pettitt on 2012-01-12
Hello Ubuntu folk

My very linux friendly Toshiba laptop of old died last month and has been replaced with a hurriedly acquired Circa 2009 Sony Vaio Z (VGN-Z21WN) I picked up from eBay.

Good news is that (despite old reports to steer clear I read only once it was too late) Ubuntu 11.10 is very usable with this hardware right out of the box. Everything critical works. But there are some very rough edges (As it happens, it&#8217;s also just as rough with MS Windows, but in different places).

There&#8217;s some Linux information about older Vaio Zs like mine on the Web, which gives hope, but the info seems out of date and I&#8217;ve run into trouble and messes trying to follow it.

Obviously it would be very lovely to get this thing fully working and I'd hugely appreciate any help. I&#8217;ve used Ubuntu as my main (only) OS for years now, but still consider myself a total Linux noob.

There are but four areas of contention.

**Video Output**
There are two (count &#8216;em) graphics chips inside this laptop: one from Intel and also a descrete graphics chip from nVidia. There's a physical Stamina/Speed switch to swap between them. This has Ubuntu thoroughly confused. The switch does nothing. The nVidia card is recognised and I&#8217;m prompted for and can download proprietary drivers - but the nVidia server settings tool complains that they&#8217;re not being used. Screen output seems only to come from the Intel chip. System Info reports the graphics hardware as unknown.


**Audio Output [[SOLVED]("http://ubuntuforums.org/showpost.php?p=11610877&postcount=2")]**
Audio output - audio hardware needs switching off and on again via the sound settings tool after headphones have been inserted - otherwise the output level is &#8216;capped&#8217; at very quiet with headphones, regardless of the volume controls.

**Keyboard Special Keys**
There are three &#8216;special&#8217; multimedia keys on the keyboard.

There is a Mac style eject button for opening the DVD drive - but it only works when a disc is inserted. It would be nice to be able to use it to open the empty drive to insert a disc too.

There are two special keys labled S1 and S2 - it would be nice to be able to assign some use to these.

**Trackpad**
The Track Pad seems a bit flaky in Ubuntu. Sometimes a double tap and hold works to grab and move windows and icons or to adjust size controls - sometimes it doesn't. The physical buttons work well though.

---

### Post by Jason Pettitt on 2012-01-14
Okay, I managed to make a little bit of progress and after umpteen dead ends found a fix for the quiet headphone issue.

The solution is to open the [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") configuration file: **alsa-base.conf** in a text editor (open up a terminal [CTRL+ALT+T] and enter **gksudo gedit /etc/modprobe.d/alsa-base.conf**) and add the following line at the end of it....
```

options snd-hda-intel model=sony-assamd 
```
...then save and reboot.

---

### Post by JohnKMFDM on 2012-03-09
Hello. do you have any progress with the nvidia Video issue on vaio vgn and ubuntu 11.10?

---

### Post by slavabez on 2012-04-01
I started using my Sony Vaio VGN Z27GN (very similar to VGN-Z/Z11) laptop a few days ago, and installed the latest Ubuntu I could find (11.10). It's a very small and convenient laptop; very light and easy to carry anywhere, and decent battery. I have the exact same issues with drivers. 
Thanks for the audio driver help, that was really useful, I can listen to music through the headphones now :D

I am not really bothered by being able to use the mac-style button, but the graphics switch would be quite handy. At the moment, as far as I know, Ubuntu uses both of the graphic adapters (I might be wrong here). What I want to be able to do is to disable the Nvidia graphics adapter, so that the battery lasts longer (At the moment it lasts for about 1,5-2 hours on slightly above than minimal brightness. I'm sure it could last for a lot longer than that if the Nvidia adapter was powered off.

So, if there are any developments with the graphics switch, please post them here. I should've also mentioned that I am a complete noob at linux :D

---

### Post by orawax on 2012-05-02
> **Jason Pettitt said:**
> **Video Output**I won't go into details (at least not yet, since I'm only considering of buying a VGN-Z atm) but I can point you to following links:
[LIST]
[*][https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux) (perhaps join the team and/or subscribe to mailing list?)
[*][http://linux-hybrid-graphics.blogspot.com/2012/01/bumblebee-version-30-tumbleweed-release.html](http://linux-hybrid-graphics.blogspot.com/2012/01/bumblebee-version-30-tumbleweed-release.html)
[*][https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)
[/LIST]Possibly also of interest:
[http://askubuntu.com/questions/8247/problems-with-graphics-of-sony-vaio-z](http://askubuntu.com/questions/8247/problems-with-graphics-of-sony-vaio-z)

(This wisdom was acquired by googling 'vaio vgn-z hybrid graphics linux' :))

---

