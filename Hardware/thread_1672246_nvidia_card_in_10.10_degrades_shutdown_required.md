---
title: "nvidia card in 10.10 degrades shutdown required"
date: 2011-01-20
forum: Hardware
---

### Post by myalenti on 2011-01-20
Specs: 
Dell e6400 Dual core i3 Intel 2.4gz
2.0gb Ram
250gb hard drive

Video:
PCI-E X 16 512mb nVidia Quadro NVS 160m

Ubuntu Version 10.10 
Kernel: Linux Late6400 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

It appears that after viewing a video there is a hardware resource of some sort on my video card that either runs out or get locked up, or some such.

I can play a movie in VLC or Xine for example for 20-30 mins before the video becomes choppy and not worth watching.

At that point if i kill all my applications my system is still slugish. Rendering seems to burden the system, meanwhile top seems to indicate that the system is indeed largely idle.

In order for me to clear this sad state of affairs, i actually have to shut the laptop down. Would you believe that doing a reboot does not suffice? In fact, if i reboot when my lappy is in this state and boot right into windows 7, even windows is every sluggish.

So apparently there is a resource of some sort that is being consumed on the video card while playing a movie that is never released or renewed, even when rebooted. It requires a complete shutdown.

In an effort to alleviate the problem i actually upgraded to the most recent nVidia drivers, 260.19.29. I didn't have high hopes for this as nvidia-current is currently at 260.19.09 i think.

Needless to say the upgrade did not help...

Any ideas anyone? Known bug? Something i need to know about? A setting i need to massage?

Thanks for the feedback!

---

### Post by myalenti on 2011-01-20
Sorry all, this is a duplicate post from the DB problem earlier this evening.

---

### Post by myalenti on 2011-01-22
Problem seems to be been cleared using Nvidia 260.19.29 driver and kernel 2.6.36...

Note that it is very likely that just installing the more recent kernel would likely address the issue, i just have not tested this theory.

Thanks

---

