---
title: "Webcam not installed properly"
date: 2017-10-25
forum: Hardware
---

### Post by peyre on 2017-10-25
The webcam on my Sony Vaio is a VGP-VCC6 [R5U870], and on my previous installation(s) of Xubuntu I've successfully installed it by running this in a terminal:
```
sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 
```
But Xubuntu got kind of messed up over time, so I did a wipe and reinstall of 17.10 64-bit yesterday.  Everything went smoothly, and it said it installed successfully, but the webcam isn't working.  Cheese takes forever to open (probably timing out) and then says "There was an error playing video from the webcam".  Skype shows no signs of a webcam in settings.  So I tried installing the 64-bit firmware and driver for the webcam from here: [http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/"), but that hasn't made a difference.  Anyone have any suggestions?

---

### Post by peyre on 2017-10-28
Bump!  Anyone?

---

### Post by peyre on 2017-10-28
It *is* working, after all.  Just cheese doesn't show it, and Skype isn't showing it in Settings.  But in a live Skype session, the webcam works.  Sorry everyone.

---

