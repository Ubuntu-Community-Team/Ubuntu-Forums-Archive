---
title: "External usb soundcard"
date: 2016-04-22
forum: Hardware
---

### Post by jay_bowles2 on 2016-04-22
I have recently upgraded to Ubuntu 16.04 and am now having an issue with my Cambridge Audio DacMagic 100 soundcard. When I first booted into the desktop I noticed that the led lights indicating the sample rate were not lit. I popped into the sound settings and although the card was there, the test failed to produce sound. Having installed Nvidia drivers, I rebooted and now the card has disappeared from sound settings. Now I have tried un plugging it and it does (strangely) work in Kubuntu 16.04 (I'd rather not use this though). I have checked the release notes and nothing leaps out at me and my brief look on Launchpad produced nothing either. As a final test I reinstalled with a different iso, but again no sound....

Does anyone know a way forward with this??

---

### Post by jay_bowles2 on 2016-04-23
Just had a look at the logs and noticed this:

```
Apr 23 11:04:02  kernel: [  584.900386] usb 2-3: 1:1: usb_set_interface failed (-71) 
Apr 23 11:04:02 penguinclaw-desktop pulseaudio[1795]: message repeated 3749 times: [ [alsa-sink-USB Audio] alsa-sink.c: Failed to set hardware parameters: Input/output error
```]

So it looks like a kernel error?? Does Kubuntu use a different kernel version?

---

### Post by jay_bowles2 on 2016-04-25
Anyone??

---

### Post by jay_bowles2 on 2016-04-27
Okay I have given up with this as I am too concerned about the risk of harm to my soundcard. Little peeved that no-one could help, but I realise that the forum is run by volunteers... so no worries. I have migrated to kubuntu which works fantastically. I would raise a bug but I have no idea how to do that, being as I don't know what the issue is with. :/

PS I still have my trusty Ubuntu Touch phone and Ubuntu on my HP 255 so I'll still be around.... evil laugh :D

---

### Post by Danny_Saba on 2016-04-27
I've noticed the same issue with my SMSL M8 using Ubuntu 16.04 so I had to switch to a different distro because it was frustrating. It worked with Kubuntu 16.04?

---

### Post by jay_bowles2 on 2016-04-28
> **Danny_Saba said:**
> I've noticed the same issue with my SMSL M8 using Ubuntu 16.04 so I had to switch to a different distro because it was frustrating. It worked with Kubuntu 16.04?


Yes it does and really well. The only thing with Kubuntu at the moment is that there is a known bug with the proprietary driver App in that it just hangs. If you use this feature you can either wait for a fix or manually install the ones you want. Other than that Kubuntu 16.04 is nice and stable on my machine and sounds good :)

---

### Post by talisker2 on 2016-04-28
I have the same issue after upgrading to 16.04.
The workaroud is to kill the process fwupd and remove the package (sudo apt-get remove fwupd)
My DAC work like a charm now. By the way I don't need this tools (fwupd)

---

### Post by jay_bowles2 on 2016-04-29
That's interesting to know. I take it you are using Ubuntu and not Kubuntu. It's interesting because from what I can tell Kubuntu is the only *buntu where fwupd hangs.... so I wonder if the bug has to do with usb hardware (or at least usb soundcards). If I get a spare minute I'll do some digging, although I am happy with Kubuntu for now.

---

### Post by talisker2 on 2016-04-29
I use Ubuntu 16.04.
The bug report is here : [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079)

---

### Post by jay_bowles2 on 2016-04-29
> **talisker2 said:**
> I use Ubuntu 16.04.
The bug report is here : [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1574079)

Cheers for the link!!

---

