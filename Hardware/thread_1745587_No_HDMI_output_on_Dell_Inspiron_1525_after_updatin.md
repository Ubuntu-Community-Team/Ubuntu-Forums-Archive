---
title: "No HDMI output on Dell Inspiron 1525 after updating to 11.04"
date: 2011-05-01
forum: Hardware
---

### Post by dRoRdAyAn on 2011-05-01
Hallo Everybody,

I have a Dell Inspiron 1525 with Kubuntu installed, from which I watch video content on a projector using my HDMI output. (Only video, audio using the normal earphones plug). I Recently updated to 11.04, after which my projector failed to find my HDMI signal from the laptop. My computer recognizes the new display (even with an automatic pop-up notification, which didn´t happen before the upgrade) but when I select the new display resolution and klick "Apply", the projector still doesn´t recognize a source. 

I have re-enabled all repositories and third-party-sources and ran apt-get update, after which my projector seemed to detect a signal for a split second but lost it immediatly.

would be grateful for any ideas.

Again: Dell Inspiron 1525 using Kubuntu 11.04. Tell me if you need more information and terminal output.

thanks and all the best,

Dror

---

### Post by ranjan_mg on 2011-05-10
I am facing a similar issue - kubuntu 11.04 on a sysem76 laptop. I migrated out of ubuntu/unity to KDE. Now HDMI does not seem to work at all. No video; Function key to toggle display does not do anything. Any idea how to force it ?

---

### Post by lidex on 2011-05-11
Perhaps a known issue?
[http://ubuntuforums.org/showthread.php?t=1749312](http://ubuntuforums.org/showthread.php?t=1749312)

---

### Post by dRoRdAyAn on 2011-05-22
couldn´t find it as a known issue, nor anywhere on google. I thought after a couple of weeks an update will come along which will fix it, but nothing yet and I´m still not able to find anything on the forums. 

any ideas?

cheers,

Dror

---

### Post by lidex on 2011-05-22
How about some system info:
```
cat /var/log/Xorg.0.log
```
```
cat /etc/X11/xorg.conf
```
```
sudo lshw -C display
```
```
grep "X Driver" /var/log/Xorg.0.log
```

---

