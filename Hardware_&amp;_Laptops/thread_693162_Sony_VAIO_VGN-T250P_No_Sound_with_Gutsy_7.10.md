---
title: "Sony VAIO VGN-T250P No Sound with Gutsy 7.10"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by camuyano on 2008-02-10
Hello:

I've been trying to get sound to work for a week after installing Ubuntu 7.10 in my Sony VAIO VGN-T250P. I'm about ready to give up after checking out all the posts about sound and getting nowhere.

After trying the steps outlined here several times: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Here's the output of my aplay -l command:
```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Int
el 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Here's my lspci | grep audio:
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```

lsmod | grep snd:
```
snd_intel8x0           35484  2 
snd_ac97_codec        101924  1 snd_intel8x0
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            42784  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            35456  0 
snd_seq_midi_event      8704  1 snd_seq_oss
snd_seq                54224  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
snd                    56740  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11656  2 snd_intel8x0,snd_pcm
```

I ran alsconf and my soundcard seems to be recognized; however, my modprobe  snd- returns the following:
```
FATAL: Module snd_ not found.
```

I ran alsamixer and unmuted everything but "External" as per instructions. I even downloaded Kmix and installed it since that seemed to work for someone else.

My /etc/modules has snd-intel8x0 listed and everything looks fine but I still get no sound.

I even reinstalled Ubuntu from scratch but didn't get any results. Has anyone been able to get sound to work for this computer with 7.10? Should I get another version of the kernel? I can't think of anything else to try.

Any help will be greatly appreciated.

Later,
Camuyano

---

### Post by arkara on 2008-02-10
did you try to boot with acpi=off?
you can do this by editing the /boot/grub/menu.lst

---

### Post by camuyano on 2008-02-11
Arkara:

Thanks for your reply.

I have not tried that yet. I will try it tonight when I get home.

Thanks again,
Camuyano

---

### Post by camuyano on 2008-02-11
Well, I tried booting with acpi=off and it didn't work. I also tried a couple of other things as well but to no avail. 

The only thing I can think of is that maybe I muted the sound in Windows or using the mute hard key before reformatting my drive and destroying the windows partition. (See [http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved]("http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved")) 

I don't have a Windows or recovery disk so I'll have to wait until next paycheck to buy a copy of Windows and see if that was indeed the cause.

Later,
Camuyano

---

### Post by arkara on 2008-02-12
i don't believe that this is because you have a dual boot of windows...
so i sugest that you don't buy a windows pack(not only it will not offer you anything but also you pay money to ms)
is the laptop a new model??? if yes try the live cd, open the examples folder and see if the sound plays ok.if not your laptop might not be supported. if so you can try the new ubuntu hardy live cd but it is still in bete there so do not install it on a production machine.
be sure that you have unmuted sound on your original installation.
i can't think any other reason.

---

### Post by Rookie1971 on 2008-02-13
I have the same issue as described above. I tried about the same things to fix the issue but no result.
my system is a sony vaio vgn-b1vp

i'll keep on searching. I i find anything i'll post it here. But i'm also interested if the above suggestion works.

---

### Post by camuyano on 2008-02-14
> **"Arkara"]is the laptop a new model??? if yes try the live cd, open the examples folder and see if the sound plays ok.if not your laptop might not be supported.[/QUOTE]

This notebook is a couple of years old. I found the following report on compatibility with the VGN-T350:

[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-T350]("https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-T350")

All the VGN-T series notebooks should share the same chipset, etc. I am not shure what the P at the end of the model number indicates but it might be for the smaller lighter models since this one is pretty small and light. That's why I normally use it as travel PC.

Anyway, there seems to be pretty strong indication that this machine is supported. The report cites that the external amplifier needs to be disabled but I already tried that. I will have to try the live CD again and see if I can get any sound out of the stuff in the samples folder.

I am still tempted to rebuild the Windows partition and see if unmuting in the Windows side does the trick. According to Sony, the recovery disks are on a "special" partition in the hard drive said:**
> i'll keep on searching. I i find anything i'll post it here. But i'm also interested if the above suggestion works.

Thanks. Any further info will be greatly appreciated. I will also post any results in this thread.

Thanks,
Camuyano

---

