---
title: "a/v codecs"
date: 2008-10-11
forum: General Help
---

### Post by mr.farenheit on 2008-10-11
is there anyway i can download all the audio and video codecs needed for ubuntu preferrably in .deb format?

---

### Post by RequinB4 on 2008-10-11
go to add/remove and install "ubuntu restricted extras"

---

### Post by mr.farenheit on 2008-10-11
and that will solve the codec problem i hope?

---

### Post by fragos on 2008-10-11
That installs many but are still a few you might want for instance to play DVD movies. Go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the instructions to add their repository. Not only will you access to all codecs but also aps like Google Earth which are free but not open source. Video tools like ffmpeg will have more complete functional capabilities, again relating to not being open source.

---

### Post by oldos2er on 2008-10-12
> **mr.farenheit said:**
> and that will solve the codec problem i hope?

 What codec problem?

 You need to enable Medibuntu repository to get libdvdcss2.

---

### Post by mr.farenheit on 2008-10-12
thank you all

---

### Post by fooman on 2008-10-12
saw this "silver bullet" for multimedia codecs posted in another thread here (sorry, i can't remember where or who posted it or i would just post a link).  anyways,  it will enable the medibuntu repos and install the needed codecs...just copy/paste the following into a terminal and press enter:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

