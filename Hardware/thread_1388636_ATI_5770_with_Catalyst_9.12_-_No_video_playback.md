---
title: "ATI 5770 with Catalyst 9.12 - No video playback"
date: 2010-01-23
forum: Hardware
---

### Post by dieresys on 2010-01-23
Hi,

I've installed **ATI Catalyst** drivers (v**9.12**, without the hotfix) for my **5770** and I've no video playback. 

Whenever I play a **video** (I've tried with Totem and VLC) I only see **black** where the image should be.

Steps I followed to install the driver on an **Ubuntu 9.10** fresh installation:

[LIST]
[*] sudo ./ati-driver-installer-9-12-x86.x86_64.run --buildpkg
[*] sudo apt-get install dkms *# missing dependency*
[*] sudo dpkg -i *.deb
[*] *# restart*
[/LIST]

Any idea what could be wrong?
TIA

---

### Post by dieresys on 2010-01-23
Ok, looks like I'll have to wait until new drivers arrives.

---

### Post by poldie on 2010-02-28
> **dieresys said:**
> Ok, looks like I'll have to wait until new drivers arrives.

I've got the new version (at least, I got the latest version, which was released after your post) and I get just black too.

Catalyst is v10.2 according to their site, but I don't see where that version number is displayed from within Ubuntu.

---

### Post by Hangman228 on 2010-07-10
Got the same issue here....
The only way is to reinstall radeon free driver ?

---

### Post by hal8000 on 2010-07-10
I'm in the process of building a new computer, and I'm considering an ATI card. However this is the main concern, ATI have never really provided good drivers for their cards.

I hope someone has a solution for you.
One thing you can try is  start totem or vlc from the terminal. There may be extra output generated which you can post back.

---

