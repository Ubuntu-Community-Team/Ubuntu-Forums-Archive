---
title: "Alsa - ad1986"
date: 2012-07-18
forum: Hardware
---

### Post by Wazowsky on 2012-07-18
I have a pc with SounndMax AD1986, Fujitsu-Siemens E620

I have installed Kubuntu 12.04 and work fine, but it has a problem with audio card.

I have uninstalled  pulseaudio, and now Kmix works well automatically, now i can see every channel of my audio card.

But Muster control of mixer doesn't work and doesn't work mic.
I have tried to configure ALSA drivers,  but without success.
I have upgraded ALSA driver  from 1.0.24 to 1.0.25, but without success.

Now i have only a channel to listen: Headphone. :(

Please! Have you an idea?

---

### Post by jmfal on 2012-07-18
Welcome to Ubuntu

Do you have any sound at all??

Post the output of:
```
  aplay -l    
```
And
```
  sudo lshw  
```

copy/paste between [CODE][CODE] tags using [SIZE=4]#[/SIZE] above.

---

### Post by Wazowsky on 2012-07-18
I have sound in output, but mic doesn't work.

The jack in front of panel for output exclude rear output and work fine.

In alsamixer i have a lot of channels in output and input that hardware doesn't have !!!

In alsamixer works only a channel , the "headphone". Other channels don't work!


My hardware:

============= aplay -l ==================

**** List of PLAYBACK Hardware Devices ****
 card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
   Subdevices: 1/1
   Subdevice # 0: subdevice # 0
 card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
   Subdevices: 1/1
   Subdevice # 0: subdevice # 0

============ sudo lshw ==================
......
*-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:3800(size=256) ioport:3400(size=64) memory:f0140800-f01409ff memory:f0140400-f01404ff
......

Thank You!

---

### Post by jmfal on 2012-07-18
Ok open a terminal and run:

```
  gksudo gedit /etc/modprobe.d/alsa-base.conf   
```

Enter password in window, file will open, scroll to end of file and add this:

```
 option snd-hda-intel model=fujitsu    
```

save/close and make sure to save to etc folder (click etc , click save)

Restart laptop
Make sure speakers are not muted in alsamixer
Play some music

---

### Post by Wazowsky on 2012-07-19
I have tried these solutions, but nothing seems to happen:

# options snd-hda-intel model=3stack
# options snd-hda-intel mode=auto
# options snd-hda-intel mode=laptop
# options snd-hda-intel mode=generic
# options snd-hda-intel model=hp position_fix=1 enable=yes
# options snd-hda-intel mode=lenovo
# options snd-hda-intel mode=samsung
# options snd-hda-intel mode=fujitsu
options snd-hda-intel model=fujitsu

This options don't change channel of mixer !

I don't understand -->  "mode" or "model" ?!

---

### Post by jmfal on 2012-07-19
It's complicated and I think this should explain part of it (first two paragraphs)

Don't leave all those option in the file.
If you removed 'Pulseaudio" you should reinstall it, I don't think it is the problem.

Open the alsabasa.conf. file
and change option to>> model=8x0m
Restart
check mixer, not muted
Play some music

---

### Post by Wazowsky on 2012-08-03
Thank You very much for your help!

I removed "Pulseaudio" because Kubuntu has "Kmix"!

I noticed that sometime If you remove Pulseaudio in Kubuntu, 
after reboot (one or two times) you can use Kmix with the same channels of Alsamixer! 

But, I don't know if it's always true for all version of Kubuntu and if this tip always works, 
but, In other pc, i have resolved with this tip.

In this case i made the same and now i have Kmix with a lot of channels but only three or four of these can change audio. 
Other channels don't make any change. (It's strange!)


However! I noticed that if i use stereo headphone like a mic (and i turn off "mic boost"), 
channel of mic works well (like a stereo mic). :)

But i have a mono mic! :-(

---

