---
title: "Integrated sound card not detected"
date: 2010-04-09
forum: Hardware
---

### Post by BetterSense on 2010-04-09
I have a DFI RS482 mobo with integrated sound. I am making a car puter and only have a 2GB CF card, so I installed a server install of Ubuntu. Then I got xserver-xorg, mplayer, and fluxbox. I downloaded and installed the latest nvidia driver.

Mplayer spit out tons of sound errors and that's when I realized the server install has no sound. So I installed the 'alsa', 'pulseaudio' and 'pavucontrol' packages. Now mplayer does not complain and acts like it is playing sound, but nothing happens sound-wise. Pavucontrol shows mplayer as playing sound and the volume as unmuted. However the PCM output is going to "dummy output" and the configuration tab says there are no cards to be configured. So I think my sound card is not being detected. I don't know what to do at this point. Can someone point me in the right direction?

lspci shows "Multimedia audio controler: ATI Technologies inc. IXP SB400 AC'97 Audio Controller (rev 80)"

alsamixer fails on "function snd_ctl_open failed for default: No such file or directory"

lsmod | grep 97 returns a bunch of stuff, but I'm not sure what it is.

---

### Post by lidex on 2010-04-09
hardy or karmic?

What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by BetterSense on 2010-04-10
```
chaz@argus:~/Videos$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  chaz       1494 F.... pulseaudio
chaz@argus:~/Videos$ 
```


I thought the problem was my server install, so I gave up and used a spare hard drive to install a FULL ubuntu install. My sound, STILL DOES NOT WORK. It pretends that it is working. Really it does. But nothing comes out. I'm so fed up with this. I ran through the entire Ubuntu sound troubleshooting doc this morning and did all the normal stuff, and it still doesn't work. It acts like it's working, but it's not. I triple checked my sound hardware by plugging my mp3 player in instead of the computer, and it plays fine from the mp3 jack, just not my computer's jack. And the thing is, my other computer, with a different motherboard, acts exactly like this a lot of the time, although the sound has randomly worked before on that system. But most of the time, volumes are all up, applications all act like they are playing, and nothing.

Seriously, I have been using linux for like 2 years; I remember sound working....even with this hardware! What happened? I literally don't know what to do next except chuck the whole system in the trash. The whole point was to have it play video.

---

### Post by lidex on 2010-04-10
I'm going to assume you're on karmic:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Reboot.

---

### Post by BetterSense on 2010-04-11
Actually, my friend gave me an ancient Creative sound card that just worked after reboot. I have no idea why the onboard sound doesn't work, even though it worked with linux a couple years ago.

---

### Post by lidex on 2010-04-11
Don't look a gift horse in the mouth. ;-)

---

