---
title: "As god is my wittness there will be blood!"
date: 2009-11-22
forum: Hardware
---

### Post by PauPau on 2009-11-22
Hello, everyone,

I've just gotten really frustrated over this problem that I've been having with my sound card
I run a:
HP Pavillion dv6000, with a 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

With Jaunty i was able to solve the problem by installing OSSv4, but since I've upgraded to Karmic Koala, I have tried Literaly Everything, and yet still no sound or sound card recognition. 
As you may or may not have noticed, I am quite new to Ubuntu, so please prevent me from smashing my laptop into the wall...

Thank you in advance

---

### Post by m3741 on 2009-11-22
Hang on there cowboy (or cowgirl). Have you done some Googling? Check out [http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#audio]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#audio").

---

### Post by TenPlus1 on 2009-11-22
try this: [http://ubuntuforums.org/showthread.php?t=806841](http://ubuntuforums.org/showthread.php?t=806841)

---

### Post by PauPau on 2009-11-22
Thanks guys,
And yet still: 
$ > sudo aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by AllenGG on 2009-11-22
Try adding "sysinfo" from Synaptic. It's a GUI , simple, tells all.
Or, from the horse's mouth, as opposed to the other end:
sysinfo is a graphical tool that is able to display some hardware and
software information about the computer it is run on.

It is able to recognize information about:
  - System (Linux distribution release, versions of GNOME, kernel, gcc and
    Xorg and hostname);
  - CPU (vendor identification, model name, frequency, level2 cache, bogomips,
    model numbers and flags);
  - Memory (total system RAM, free memory, swap space total and free, cached,
    active, inactive memory);
  - Storage (IDE interface, all IDE devices, SCSI devices);
  - Hardware (motherboard, graphic card,**[COLOR=Red] sound card,[/COLOR]** network devices);
  - NVIDIA graphic card: only with NVIDIA display driver installed.8-)

---

