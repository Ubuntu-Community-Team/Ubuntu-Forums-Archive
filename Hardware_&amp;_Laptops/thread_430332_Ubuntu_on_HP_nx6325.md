---
title: "Ubuntu on HP nx6325"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by meenavin on 2007-05-02
I have bought a new HP nx6325 with AMD64 bit processor. I am planning to install Ubuntu in it but i would like to know if all the drivers are available for HP laptop in this OS??

Navin

---

### Post by jamesstansell on 2007-05-02
Here is some information that might help answer your question.

[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325)

I hope you give it a try and report your experience.

---

### Post by EXCiD3 on 2007-05-03
My HP DV9000t has almost everything working. I have not tried Webcam, Microphone, Card Reader, or the ExpressCard slot. However, everything else seems to work perfectly!! ;)

---

### Post by revol on 2007-05-06
Hello!
I have a nx6325 with turionx2 2ghz. I can tell that there are a lot of bad things about Kubuntu Feisty running on my laptop...First of all, I upgraded the Bios firmware ti F06 version, but some problems can't be resolved. 
[COLOR=Silver] --**Audio problem**--: trying to use skype, for example, I can see that internal microfone isn't well supported by alsa, because after some time it goes down, and audio input disappear. It's the same if I modify /etc/modprobe.d/alsa-base by adding 'options snd-hda-intel model=hp position_fix=1 enable=yes'...there's no difference between 32 or 64 bit. [COLOR=Black]Audio Problem resolved: just installing Alsa 1.0.14!!now skype works good, but the problem still exist when screensaver starts...[/COLOR][/COLOR]
--**Card Reader**--: does not work in 64bit kubuntu feisty, perhaps in 32bit too.
--**Low Latency Kernel**--: I installed low latency kernel (linux-image-2.6.20-15-lowlatency), I restarted the pc and everything seemed to be ok, but...when I try to install realtime-lsm, via module-assistant, with the goal tu run jack in realtime, I get errors from m-a during the configuration of realtime-lsm-restricted...at the end, realtime can be loaded with modprobe in the kernel (also with any=1 option), but it does not work. No difference between 64 or 32 bit arch.

Furthermore, with dmesg I can see that APIC is not well supported, and if I start with 'noapic nolapic' options added to the kernel, my computer works just with single core of the cpu, instead of two. This is the error I get from dmesg: 'APIC error on CPU0: 40(40)'..I don't know what it means..

Sorry for my bad english, If there is someone can help me....

---

### Post by meenavin on 2007-08-22
Thanks for all the reply..Let me try installing and see what happens.

---

