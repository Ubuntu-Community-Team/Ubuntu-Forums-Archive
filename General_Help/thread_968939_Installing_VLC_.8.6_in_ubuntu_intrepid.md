---
title: "Installing VLC .8.6 in ubuntu intrepid"
date: 2008-11-03
forum: General Help
---

### Post by parry_mathur on 2008-11-03
I just installed VLC via apt-get install vlc. It downloaded the latest version (.9.4) for me. I don't like it and want the old version(.8.6). Where can I get it from? It's not there when I search in Synaptic, and VLC's website doesn't offer any help on that.

---

### Post by renzokuken on 2008-11-03
0.8.6 is still available in the hardy repos. maybe you could get it from there.

[http://packages.ubuntu.com](http://packages.ubuntu.com)

find it, download the deb to you home folder and

```
sudo dpkg -i vlc*-filename*.deb
```

---

### Post by Yellow Pasque on 2008-11-03
I wouldn't recommend it. From the VLC site:
> The VideoLAN team ceases all form of support for VLC media player the 0.8.6-bugfix tree. After several several call for help, it is apparent that there is no interest in the community to maintain the 0.8.6 branch of the VLC media player. As a consequence, it has not been possible to put sufficient efforts to ensure adequate continued quality of the 0.8.6-bugfix branch. Effective immediately, there will be no more security and critical fixes for VLC 0.8.6. Binary releases of the 0.8.6-bugfix branch had already stopped as of July 2008. The VideoLAN team will continue to provide major or security-related bug fixes for the VLC media player 0.9-bugfix branch. **If you have not already upgraded to VLC version 0.9.5, please do so urgently (exploits for vulnerabilities found in older versions are widely available as of today).**

---

### Post by directcharitycontribution on 2008-11-10
was going to do that

[http://ge.ubuntuforums.com/showthread.php?t=966267](http://ge.ubuntuforums.com/showthread.php?t=966267)

---

