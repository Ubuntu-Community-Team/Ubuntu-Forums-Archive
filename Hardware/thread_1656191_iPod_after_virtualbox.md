---
title: "iPod after virtualbox"
date: 2010-12-30
forum: Hardware
---

### Post by eljer on 2010-12-30
Running ubuntu 10.04. I've only been a linux user for 2 or 3 months, so I could easily be missing something simple here. Or if I should be asking this somewhere else, please let me know.

I got an ipod touch in August, I used rhythmbox and gtkpod to add music to it and it was working great.

I had wanted to update the firmware a month or so ago, so I installed vista inside VirtualBox 3.2.12 to put itunes in. I enabled the usb controller, added a device filter for the ipod, and it worked as I wanted it to.

I then wanted to use it in ubuntu again, but can't figure out how to get it to recognize the ipod again. I've removed the device filter in VB, and then disabled the usb controller there, but still no dice. It charges when plugged in, and after re-enabling the usb controller in VB it still works there in itunes, but I don't want to use it there.

Any ideas?

---

### Post by daqron on 2010-12-30
Well, good job getting your iPod to work with rhythmbox and gtkpod; that's not always easy. Is the post-iTunes behavior you describe possibly due to the fact that iPods associate themselves with iTunes on one machine, and subsequently do not interact with other iTunes installations (and, perhaps, with other non-iTunes media management applications)? If so, maybe give this a shot? [http://support.apple.com/kb/ht1202](http://support.apple.com/kb/ht1202)

Just a thought.

---

### Post by bapoumba on 2010-12-30
[http://ubuntuforums.org/showthread.php?t=1628529](http://ubuntuforums.org/showthread.php?t=1628529)
Solved my own issues :)

---

### Post by eljer on 2010-12-30
daqron, thanks for the link. I looked into it, thinking the update might have changed that setting, but still no. It did give me a bit more to think about.

bapoumba, thanks! That was exactly what I needed. I hoped a thread like that existed, though I couldn't find it when I searched. I was mostly blaming it on virtualbox though, and not the real culprit. Great info there.

Specifically the post [http://ubuntuforums.org/showpost.php?p=10208430&postcount=36](http://ubuntuforums.org/showpost.php?p=10208430&postcount=36)
Followed those steps, rebooted, and voila. Happy eljer!

> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

---

### Post by eljer on 2010-12-30
For what it's worth, my problems aren't 100% solved :) I can now see the ipod, and rhythmbox can transfer music to it, but the ipod can't actually see the music. It sees that its storage is being used but the music player can't see it. This specific issue is certainly solved though. 

I'm looking into it now, I will post back when (hopefully) fixed, for completeness

---

