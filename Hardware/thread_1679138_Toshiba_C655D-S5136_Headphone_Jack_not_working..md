---
title: "Toshiba C655D-S5136 Headphone Jack not working."
date: 2011-01-31
forum: Hardware
---

### Post by mwpruett on 2011-01-31
I love this laptop, aside from my headphone jack not working.  When headphone jack is plugged in nothing happens.  Sound continues to play from speakers.  Pop is heard on plugging headphones in, but that's about it.  Have searched and can't find any information specific to this.

I have tried editing alse-base.conf unsuccessfully with 

options snd-hda-intel model=thinkpad
and
options snd-hda-intel model=ideapad


  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:d2300000-d2303fff

---

### Post by mwpruett on 2011-01-31
I know this problem comes up a lot but if somebody can just point me in the right direction I'd greatly appreciate it...

---

### Post by mwpruett on 2011-02-01
anybody have any ideas?

---

### Post by NautilusUK on 2011-11-06
I had the same problem on a Toshiba Satellite L750. Tried all the other fixes I could find but to no avail. Was about to give up when I found this:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

All I did was the following:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update[B]

Install the linux-alsa-driver-modules package[/B] 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

**Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.**

Now all works fine with auto-sensing headphone jack! Hope this works for others too.

---

### Post by barnabas02 on 2011-11-06
Try to boot with the jack. I mean plug in the headset first, then tun the computer on. If it don't works, try the contrast.
Or go to the system settings, and try to add the headphone in the manager.

---

### Post by ilyklinux on 2012-03-24
I had tried this one. when am updating the package lists using 
sudo apt-get update, some errors are showing like dis........

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
wat does it mean???

---

### Post by snowmethod on 2012-03-27
I have tried most of the guides for troubleshooting audio and non of them worked for me.I have messed up even more so i have had no sound at all. I have decided to update to the latest kernel 3.3 following this guide:

[http://www.upubuntu.com/2012/03/how-to-install-linux-33-kernel-in.html](http://www.upubuntu.com/2012/03/how-to-install-linux-33-kernel-in.html)

...and the sound is back, headphones work as they suppose to. Happy days :)

---

### Post by mathiaho on 2012-04-06
I don't know if this is solved or not (if so, please set your thread as solved)

I have a Toshiba satellite L650D which I had a lot of trouble with under Linux. All of which were solved by a BIOS update.

Might be so with your Toshiba as well

---

