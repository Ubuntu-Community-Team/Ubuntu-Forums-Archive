---
title: "Cant play dvd"
date: 2008-12-01
forum: General Help
---

### Post by fedex1993 on 2008-12-01
Hmm i had this working in hardy with libdvdcss but now i cant seem to get my dvds to play. When i open them up in vlc i get VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
 and some other line that says i dont have acess to it for some odd reason.

---

### Post by Cyhawk on 2008-12-01
You'll need to install the codec for it.

Its in the repository under libvavcodec-unstripped i believe.

An easy way to get it would be to run the DVD in totem and it will attempt to auto-install the packages with the codecs. (it will have a list of 3, get them all)

Note: Memory is spotty on the name of the package.. maybe its in the mplayer or xine packages.. Eh, just search for "dvd codec" in Synaptic. It will be there.

Oh and there are legal issues with this, so consult your local laws and stuff =)

---

### Post by theozzlives on 2008-12-01
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by fedex1993 on 2008-12-02
hmm got it working it was encrypted but now it seems to be working fine with libdvdcss isntalled

---

