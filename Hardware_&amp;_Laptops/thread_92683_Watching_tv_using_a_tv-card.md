---
title: "Watching tv using a tv-card"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Nasso on 2005-11-20
I try to watch tv using tvtime and the tv-card that is listed on the picture below. tvtime-scanner works and finds channels. tvtime gives me this error though. i use the fglrx-drivers because i need to use tv-out. -vo xv doesnt work in mplayer either :/
Anyone got any suggestions?
> nasso@nasserv:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/nasso/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

[img]http://nasso.se/ul/tvcard.png[/img]

---

### Post by dave_euser on 2005-11-20
Run "xdpyinfo | grep XV" from a shell, and make sure that XVideo is present... if you don't get anything back, then your driver doesn't have XVideo (the overlay) installed.

Also check that the saa7130 driver is actually providing an overlay - run "v4l-info | less" and check the first few lines - there is a line "capabilities", make sure that "VIDEO_OVERLAY" is in the list. Below is what I get from my board....

```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "saa7134"
        card                    : "LifeView FlyVIDEO2000"
        bus_info                : "PCI:0000:00:0a.0"
        version                 : 0.2.12
        capabilities            : 0x5010015 [VIDEO_CAPTURE,VIDEO_OVERLAY,VBI_CAPTURE,TUNER,READWRITE,STREAMING]

```

Besides that, I don't know much about the ATI Fire GLX drivers, you might have to dig around google a bit for similar problems...

---

### Post by Nasso on 2005-11-20
i have both XVideo and VIDEO_OVERLAY .

i tried xawtv too but it just goes to fullscreen and the whole screen is black, doesnt react on keyboard hits. have to open a tty to kill it from.

---

### Post by yorick on 2005-11-30
Hello.

I just want to say that I have the same problem as Nasso when i use the fglrx drivers. I have the 8.16.20 version. Also with those drivers the subtitles in Xine-ui are not drawn right. They look huge and ugly. 

I think that the problem is that the fglrx does not support overlay mode. Does anyone have the newest fglrx drivers (8.19.20) installed? Does overlay work in them?
 
With the Mesa drivers tvtime works ok. But you don't have 3D...

At the moment I switch between Mesa and fglrx depending on whether I want to watch TV or have 3D graphics. But it is kind of annoying...

The card I am using is an AverMedia TV 98.

---

### Post by ivanhoe on 2005-12-01
Same problem with me and Asus Tv card.
> ivan@marvin:~$ xdpyinfo | grep XV
    XVideo

but v4l-info | less show me this:> ivan@marvin:~$ v4l-info | less
bash: v4l-info: command not found

(meanwhille its blank page) and i have v4l installed from Synaptic.
and **yorick** how to easy switch between Mesa and Ati drivers?

---

### Post by ivanhoe on 2005-12-03
[http://ubuntuforums.org/showthread.php?p=423584](http://ubuntuforums.org/showthread.php?p=423584)

I did this and have 3D and can watch TV as well.:p :p

---

### Post by yorick on 2005-12-05
Thanks, Ivanhoe.

I followed the instructions in that post and installed the latest drivers.It works , but I had to do an additional command (I hope it's correct, I'm writing from memory) :

```
sudo aticonfig --overlay 
```

---

### Post by web250 on 2005-12-05
TV card support is *terrible* as far as I'm concerned with 5.10

The move from 5.04 to 5.10 broke my WinTV Radio. I get a stuck channel since the kernel drivers detect incorrectly and use cx8800 instead of cx88xx

Bug #16060 has been filed for it, and unfixed as of today

---

