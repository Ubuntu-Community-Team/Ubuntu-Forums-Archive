---
title: "No Audio in 13.10"
date: 2014-01-24
forum: Hardware
---

### Post by dave2001 on 2014-01-24
I'm thankful for any help and input offered on this. First, a brief background of the situation to help with troubleshooting:

In my quest to learn more about Ubuntu and linux in general, I decided to do something different for my "upgrade" to 13.10 Saucy on my Thinkpad T500. I did a base-system only installation, using the minimal.iso. After that I used the command line to install some basic packages like nano, manpages, etc. I much prefer KDE to either Unity of the new Gnome, so I then used apt-get to install kde-plasma-desktop, which is the smaller of ubuntu's KDE-metapackages.

I've gotten most things to work fine, but the audio is stumping me. I have no audio what-so-ever. Possibly related, the volume buttons on my Thinkpad have no effect when pressed. The other on-screen-display buttons specific to Thinkpads (like screen brightness) work fine. I've tried the actions listed here: [http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

here is a screenie of my audio settings:
[https://www.dropbox.com/s/6zsjj14xi097elu/Audio.png](https://www.dropbox.com/s/6zsjj14xi097elu/Audio.png)

and this:
```
~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CX20561 Analog [CX20561 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CX20561 Digital [CX20561 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Happy to post any other info that will be helpful

---

### Post by dave2001 on 2014-01-25
Anything? Would love some help with this.

---

### Post by dave2001 on 2014-02-03
Solved this one. So simple it was ridiculous. The *kde-plasma-desktop* metapackage does not include the audio package you need to integrate sound control into your desktop. 
terminal command:
```
sudo apt-get install kmix
```

Thought I'd post the solution for anyone else who runs across this problem when doing a KDE install rather than a Kubuntu install.

---

