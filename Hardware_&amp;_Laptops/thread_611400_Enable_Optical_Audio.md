---
title: "Enable Optical Audio"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by stgmavrick on 2007-11-12
Hello,

Being as this is my first post i'll introduce myself as well.

I 24 and used to be an avid windows user and family and I were beta testers from 98 up to XP.  I was introduced to linux in 2005 via Gentoo.  I had been running and learning gentoo for a few years off and on when my father had asked me to install linux on his laptop(identical to mine) because of his frustration with microsoft.  I installed ubuntu on his because i knew of its ease of use and installation compared to constant configuration of gentoo.  I liked it so much that i myself installed it and just completed such installation today.

However, it seems things are slightly different than the commands i'm used to in gentoo and so when it comes to .conf's, i really dont see too many in ubuntu that i've encountered compared to gentoo.

I am trying to get Optical audio S/PDIF enabled on a Gateway Solo 9550 with an ESS Allegro sound card.  I'm running Ubuntu 7.1.  I've been searching ever since i installed my fathers copy and the only real relevant thread i can find is [http://ubuntuforums.org/showthread.php?t=270351](http://ubuntuforums.org/showthread.php?t=270351), however i cannot decipher it.  As i stated i'm used to just editing a .conf whenever i need something changed.

On a side issue, it seems grub works a bit different too with this install.  I used to be able to just nano -w /boot/grub/grub.conf in gentoo, but i cant find the file i need to edit in ubuntu.

Sorry for the double issue here, however just did not want to tag team post.

Thanks for you help in advance,

Marshall

---

### Post by solar george on 2007-11-13
> nano -w /boot/grub/grub.conf
Try
```
nano -w /boot/grub/menu.lst
```

> Hi!
I have the same sound chipset (Envy24HT) and to get the optical output working I have to create the .asoundrc file (on your home directory) with this content:

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,1"
# format S32_LE
# period_time 0
# period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
buffer_size 65536

# rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
# type hw
type dmix
card 0
device 1
}

pcm.!default {
type plug
slave.pcm "spdif"
}

In the home directory do,
```
nano .asoundrc
```

and paste this into it (ctrl + shift + V)
```
pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,1"
# format S32_LE
# period_time 0
# period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
buffer_size 65536

# rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
# type hw
type dmix
card 0
device 1
}

pcm.!default {
type plug
slave.pcm "spdif"
}
```

Then reboot and hope.

---

### Post by stgmavrick on 2007-11-13
Thanks for the quick reply!!

1)  the menu.lst worked.  Is this the same for all ".conf" i'm used to?

2) I tried making that file and when you said in the /home directory nothing happened, so i then cp that file to my /home/<username here> folder.  No such luck.  

Its pretty important that i get the optical audio to work and i'm willing to dig as far as the rabbit hole goes to get it if anyone has any ideas how to get it going.

Thanks again,
Marshall

---

### Post by stgmavrick on 2007-11-13
alright, that problem is fixed, i forgot to get some files bfore attempting.  I did not find any enable options in the kernel like i hoped i would so maybe this can shed some light for someone.

```
root@Media-Box:~# amixer -c0 contents
numid=3,iface=MIXER,name='Master Mono Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=4,iface=MIXER,name='Master Mono Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=25
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=1,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=2,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=23,iface=MIXER,name='3D Control - Center'
  ; type=INTEGER,access=rw------,values=1,min=0,max=15,step=0
  : values=0
numid=24,iface=MIXER,name='3D Control - Depth'
  ; type=INTEGER,access=rw------,values=1,min=0,max=15,step=0
  : values=0
numid=16,iface=MIXER,name='PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=17,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=12,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=13,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=14,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=15,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Mic Boost (+20dB)'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=22,iface=MIXER,name='Mic Select'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Mic1'
  ; Item #1 'Mic2'
  : values=0
numid=9,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=10,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=7,iface=MIXER,name='Phone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=8,iface=MIXER,name='Phone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=5,iface=MIXER,name='PC Speaker Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=6,iface=MIXER,name='PC Speaker Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=15,step=0
  : values=0
  | dBscale-min=-45.00dB,step=3.00dB,mute=0
numid=21,iface=MIXER,name='Mono Output Select'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Mix'
  ; Item #1 'Mic'
  : values=0
numid=18,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=2,items=8
  ; Item #0 'Mic'
  ; Item #1 'CD'
  ; Item #2 'Video'
  ; Item #3 'Aux'
  ; Item #4 'Line'
  ; Item #5 'Mix'
  ; Item #6 'Mix Mono'
  ; Item #7 'Phone'
  : values=0,0
numid=19,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=20,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=15,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=1.50dB,mute=0
numid=25,iface=MIXER,name='External Amplifier'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
root@Media-Box:~# 

```

the card is an ESS Allegro in the solo 9550 laptop.

Thanks!

---

### Post by stgmavrick on 2007-11-16
Does anyone have an idea of what i can do to get it to work?  I've been searching for days and asking in #ubuntu.

---

### Post by solar george on 2007-11-16
Have you tried messing about with mixer settings?

---

### Post by stgmavrick on 2007-11-16
that was the first thing i tried...the optical light does not come on at all

---

### Post by solar george on 2007-11-16
I'm afraid I can't help then - I don't (have) use optical out on my system.

---

### Post by stgmavrick on 2007-11-19
Ok then, next question.

Who/what forums do i contact to find a solution.  ALSA?  I couldnt find a real "official" forum.  Or is it the kernel driver that doesnt have the ESS Allegro card programmed for Optical?  I think out of all of the things i use on the laptop, optical audio to my stereo reciever is what i want most..

Thanks,

---

### Post by solar george on 2007-11-19
I'm afraid I can't help at all. Try using IRC to contact developers. Most development is done on mailing lists rather than forums.

---

