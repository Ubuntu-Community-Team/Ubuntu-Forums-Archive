---
title: "How do I install the ALSA Drivers?"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by ckoy on 2007-02-10
I've downloaded the latest drivers, but I do not know how to install them. I am running Xubuntu 6.10 on a Compaq Presario 3500.

---

### Post by mikewhatever on 2007-02-10
Here is [The Link]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29")

---

### Post by ckoy on 2007-02-10
Hmm. I tried running sudo cp /home/naaman/installers/alsa/sudo tar xjf alsa-driver-1.0.14rc1.tar.bz2, but it said directory does not exist. I named my files like his, but i replace namaan with my name. What do I do now?

---

### Post by mikewhatever on 2007-02-11
That directory, as well as any other needs to be created first.
As you see, they create alsa directory/folder with the following,
```
sudo mkdir -p /usr/src/alsa
```
but assume, /home/naaman/installers/alsa directory/folder is there with the required files inside. You can create it like this
```
 mkdir /home/naaman/installers/alsa
```
and then download the alsa file into it, or to your desktop, and then copy paste.

---

