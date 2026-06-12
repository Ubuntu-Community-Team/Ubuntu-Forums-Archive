---
title: "getting sound (alsa) to work on fresh ubuntu install"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by basvg on 2005-08-15
Hi,

After several years of linux usage I just did my first ubuntu install. So far I'm impressed, despite the fact that I can't get sound to work on Ubuntu hoary. I tried to play some songs and got the error message "could not open resource for writing". This was my point of departure for googling.Here's what I tried:

first attempt, follow the steps in 

  [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

that wasn't a big succes. Second attempt was to ask for help on #ubuntu. That resulted in another howto that didn't really solve the problem. Finally I did some searching on my own:

-----<paste>-----
root@Librarian:~# lspci | grep -i audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

root@Librarian:~# lsmod | grep -i ac97
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm                84872  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd                    50276  10 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
-----</paste>-----

Seemed to me that the right module (ac97) is loaded and in use. I also tried to restart alsa (/etc/init.d/alsa restart) which didn't complain. The tool 'alsamixer' doesn't show me anything so I guess the card is not found by alsa at all :-( Last but not least, I can't find anything in the logs. 

Can anyone help me get this to work?

  Bas

---

### Post by andlinux21 on 2005-08-15
sound is a big problem for some reason I had heck trying to configure sound for my Micron Laptop, but my desktop didnt have any sound issues so go figure.  If the howtos dont offer any help you may want to kill the sound servers and restart each one and see if you can make any headway.

---

### Post by basvg on 2005-08-15
I tried that to no avail  and am starting to feel a bit confused  :?  I just booted the live-cd from ubuntu and on that one audio *did* work out of the box. What I don't understand is why alsamixer comes up empty...

---

### Post by somuchfortheafter on 2005-08-15
```

$ killall esd

```


that should fix it for your current session. The problem is that gstreamer doesnt work to well with esd, however using the xine engine everything works fine without killall. Personally I stick with killall, just add it to the programs to be run at each logon in your sessions section.

---

