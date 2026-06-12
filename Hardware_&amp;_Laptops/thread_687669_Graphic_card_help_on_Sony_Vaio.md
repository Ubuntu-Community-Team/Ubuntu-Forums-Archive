---
title: "Graphic card help on Sony Vaio"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by murtaza on 2008-02-04
I have a Sony Vaio Pcg-K45 and I need to know how I can find out if the built in ATI Graphic card is installed or not. If it's not, is there a way I can install it if I have the window drivers. Thanks.

---

### Post by taurus on 2008-02-04
Go into System -> Administration -> Restricted Drivers Manager and see if your graphic card is on the list.  If it is, then install a driver from there.

---

### Post by murtaza on 2008-02-04
No its not there. I realized that its not installed because I can't play video files. You can here the audio but there's no video though.

---

### Post by taurus on 2008-02-04
What kind of ATI graphic card does it have?  Which driver are you using right now?

```
cat /etc/X11/xorg.conf
```

---

### Post by murtaza on 2008-02-04
I have ATI® Mobility Radeon&#8482; IGP 345M. It says driver "ati". So, does it look like it's installed properly. If it is, why can't I play videos.

---

### Post by taurus on 2008-02-04
Which media player do you use to play your video files?  Have you installed any codecs, yet?

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by murtaza on 2008-02-04
i used vlc player, mplayer, movie player.

---

### Post by murtaza on 2008-02-05
Still no luck playing videos, I thought it was my graphic card because I couldn't get the 3D cube desktop on compiz-fusion to work. I'm still new to linux and ubuntu.

---

### Post by murtaza on 2008-02-09
Can anyone please help me out with my problem...I can't watch any videos, except for flash videos, mpg divx so far dont work. Flash videos online work but not on VLC player.

---

### Post by murtaza on 2008-02-09
when i turn off desktop effects i can play flash videos on desktop. but how do I switch the player to X11 or OpenGL output instead of XVideo.

---

### Post by murtaza on 2008-02-09
Ok...i know these questions are now off topic are being posted in the wrong section....it looks like my ati graphic card is working fine...I want to play movies online using mplayer plugin instead of totem movie player plugin. how do i do that?

---

