---
title: "how do i install &quot;win32codecs&quot; &quot;libdvdcss&quot;"
date: 2008-10-04
forum: General Help
---

### Post by Vertoxic on 2008-10-04
trying to watch a movie but it wont play nothing! it starts playing the DVD just the FBI warnings and thats it!

---

### Post by drs305 on 2008-10-04
If you don't have the Medibuntu repository enabled (if you are using hardy):
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then:
```
sudo apt-get install w32codecs libdvdcss2
```

---

### Post by exploder on 2008-10-04
Check out this too.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The guide will save you hours of work!

---

### Post by aysiu on 2008-10-04
> **exploder said:**
> Check out this too.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The guide will save you hours of work!
I have to disagree. That'd probably take an hour just to read all the way through and follow all those instructions.

For DVD playback, drs305's advice is the quickest way to get things working.

---

### Post by Vertoxic on 2008-10-04
> **drs305 said:**
> If you don't have the Medibuntu repository enabled (if you are using hardy):
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then:
```
sudo apt-get install w32codecs libdvdcss2
```
toliy@toliy-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for toliy: 
--20:28:44--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

20:28:45 (13.02 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

toliy@toliy-laptop:~$ sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
toliy@toliy-laptop:~$ 

This is what i got back

---

### Post by Vertoxic on 2008-10-04
> **aysiu said:**
> I have to disagree. That'd probably take an hour just to read all the way through and follow all those instructions.

For DVD playback, drs305's advice is the quickest way to get things working.
so pretty much i just need this...
64-Bit Ubuntu Users:

sudo apt-get remove gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar

is that right? i dont see why i have to remove flash took me 2 days to get it to work :( im scared it wont work after this?

---

### Post by exploder on 2008-10-04
Yes, that is what I used and everything worked. You might have to reboot the pc once but that will get you going.

---

### Post by exploder on 2008-10-04
Make sure you have the medibunutu repo enabled.

---

### Post by taladan on 2008-10-04
Odd...I just use:

```
sudo apt-get install ubuntu-restricted-extras
```

And it gets all the flash, java, w32 codecs, libdvd stuff...all of that.

Tal

---

### Post by drs305 on 2008-10-04
I just tried downloading w32codecs and was successful using the command line on my 32-bit machine. 

If you are on a 64-bit machine, you would need to change "w32codecs" to "w64codecs". I suppose it's possible that the generated message you initially received about needing win32codecs is a generic one that did not make a distinction between a 32-bit and 64-bit machine.

Try opening synaptic and seeing if "w32codecs" is listed. If not, make sure the medibuntu repositories are checked in Synaptic > Settings > Repositories > Third-Party Software.

**Added:** After posting this I see you referred to 64-bit as I was writing this. Changing w32codecs to w64codecs should work.

---

### Post by aysiu on 2008-10-04
> **Vertoxic said:**
> toliy@toliy-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for toliy: 
--20:28:44--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

20:28:45 (13.02 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

toliy@toliy-laptop:~$ sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
toliy@toliy-laptop:~$ 

This is what i got back
You missed the ```
sudo apt-get update
``` command (the second one in the original instructions).

---

### Post by Vertoxic on 2008-10-04
hmm just did all this 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and still nothing look at screenshot plz

---

### Post by Vertoxic on 2008-10-05
Ok so now everytime i open my Syntatic Package Manger i get this error 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by drs305 on 2008-10-05
In your [other post](http://ubuntuforums.org/showthread.php?t=938531) the suggested answer was:
```
sudo dpkg --confgure -a
```

Did that work or are you still having problems?

---

