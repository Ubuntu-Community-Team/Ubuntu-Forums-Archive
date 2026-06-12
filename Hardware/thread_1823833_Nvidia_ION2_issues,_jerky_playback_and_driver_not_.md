---
title: "Nvidia ION2 issues, jerky playback and driver not currently in use??"
date: 2011-08-12
forum: Hardware
---

### Post by dabbi2000 on 2011-08-12
I am really confused here....

I have a brand new Asus 1015PN having Nvidia ION2 onboard. 1080 playback is perfect in Windows7 while lagging on Ubuntu 11.04, even on VLC. It's a fresh install with everything updated.

So I tried Unity2d and it's the same so I went back to normal Unity.

In the "additional drivers" window it says Nvidia drivers are installed "but not currently in use". Still Compiz is showing windows effects but remember Intel's built in chip would also be able to perform this. In previous forums some have said that this is a bug but not everyone seems to agree so how can I see what GPU is really in use (in terminal)?

And how can I debug this jerky playback issue, I cannot find anyone here having the same problem?

Also, is the ION in anyway dependent on Compiz, I mean can I disable it and run Unity-2D and still expect it to work?

---

### Post by papibe on 2011-08-12
> **dabbi2000 said:**
> "but not currently in use"
That seems to be a bug.

In order to make sure you are running the Nvidia driver:

Backup your X config file first:
```
# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```
Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine/

As a precaution, disable all effects so can be take out of the equation while testing video hardware acceleration (VHA). There's 2 ways to get VHA. Using nvidia's vdpau or the generic vaapi. I don't have experience with vaapi, so here we go with vdapau.

First check if the library is installed:
```
$ apt-cache policy libvdpau1
```
If installed the output should look something like this:
```
libvdpau1:
  **Installed: 0.3-2build1**
  Candidate: 0.3-2build1
  Version table:
 *** 0.3-2build1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```
VLC doesn't work directly with vdpau so you need to test with SMplayer. Install it from the Software Center. Before playing any video, go to Options -> Preferences -> General -> Video. There, set the Output driver to vdpau. Restart SMplayer and test your HD videos.

Tell us how it goes,
Regards.

---

### Post by dabbi2000 on 2011-08-15
thanks papibe!
turned out libvdpau1 was not installed at all, really strange. I installed also SMPlayer and followed your guide and indeed it did play better, though not perfect. There was a vsync issue and the sound was now jerky (I have an external USB sound card), it was like if the CPU didn't manage to feed the USB somehow.

Can you plz answer me one thing. Do I understand it correctly that the ION drivers are not dependent on Compiz or Unity running, I mean I can login with Unity-2d and still expect the GFX to be hardware accelerated with the ION?

How about OpenGL in Chrome, should it work automatically ith libdvpau1 installed?

What are the common terminal commands to see what GFX drivers are in use currently?

Thanks!

---

### Post by papibe on 2011-08-15
Glad you're making progress!

I'm guessing you have some [tearing]("http://en.wikipedia.org/wiki/Screen_tearing") problems. At this point I'm going to be a little more conservative giving you advice, since I have only solved this problem in Lucid (10.4).

Here are two threads that are very useful. The [first]("http://ubuntuforums.org/showthread.php?t=1390284&highlight=tearing") worked for me with no Compiz effects. With the [second]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing"), I was also able to keep the Compiz effects.

Although I have installed Natty (11.04) on my laptop, I'm using regular Unity (3D), so I haven't installed any Compiz tool. I really don't know the status of the integration between Unity and Compiz.

Having said that, I would start using the instructions related only to the Nvidia part on the first thread. If that doesn't work, I would try installing the Compiz Config Settings Manager. But maybe some research is needed before trying.

BTW, anybody knows how safe is to install CCSM on Unity?

I hope it helps.
Regards.

---

### Post by gordintoronto on 2011-08-15
> **papibe said:**
> BTW, anybody knows how safe is to install CCSM on Unity?

I hope it helps.
Regards.

Numerous threads recommend it!

---

### Post by bobk_nyc on 2011-08-19
> **papibe said:**
> That seems to be a bug.

In order to make sure you are running the Nvidia driver:

Backup your X config file first:
```
# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine/

As a precaution, disable all effects so can be take out of the equation while testing video hardware acceleration (VHA). There's 2 ways to get VHA. Using nvidia's vdpau or the generic vaapi. I don't have experience with vaapi, so here we go with vdapau.

First check if the library is installed:
```
$ apt-cache policy libvdpau1
```If installed the output should look something like this:
```
libvdpau1:
  **Installed: 0.3-2build1**
  Candidate: 0.3-2build1
  Version table:
 *** 0.3-2build1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```VLC doesn't work directly with vdpau so you need to test with SMplayer. Install it from the Software Center. Before playing any video, go to Options -> Preferences -> General -> Video. There, set the Output driver to vdpau. Restart SMplayer and test your HD videos.

Tell us how it goes,
Regards.

says  "$ comand not found"  is something missing?  thanks

---

### Post by papibe on 2011-08-19
> **bobk_nyc said:**
> says  "$ comand not found"  is something missing?  thanks
'$' is just a reference to the command line prompt. Ignore it and copy/paste the rest of the line into the terminal.

Regards.

---

### Post by bobk_nyc on 2011-08-19
[QUOTE=papibe;11145780]That seems to be a bug.



First check if the library is installed:
```
$ apt-cache policy libvdpau1
```

I get this

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.

---

### Post by papibe on 2011-08-19
Try running this before the instructions on post 2:
```
$ sudo nvidia-xconfig
```
After that, check the file /etc/X11/xorg.conf to see if there's a line like this:
```
Driver "nvidia"
```
Regards.

---

