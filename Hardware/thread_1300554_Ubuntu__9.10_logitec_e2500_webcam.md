---
title: "Ubuntu  9.10 logitec e2500 webcam"
date: 2009-10-25
forum: Hardware
---

### Post by su-37 on 2009-10-25
I have just installed ubuntu 9.1 and I have a Logitech QuickCam E2500 that I want to use with Skype (Linux version) - that has been installed and works on voice. I installed Cheese Webcam and I get very poor quality and dark video from the webcam.

Any ideas?

---

### Post by uru wolf on 2009-11-23
I am also having this problem. An image shows in cheese but it's really dark.

---

### Post by tombaugh on 2009-11-29
Same here, a solution would be very welcome.

---

### Post by linmix on 2010-01-14
Same problem here, cheese shows a good image for a split second then goes almost completely dark.

If I test the cam in Skype I only get purple lines and so far no luck with the mic either.

---

### Post by Michael Cornelius on 2010-01-16
I'm seeing the same problem as well, both on 8.04 and 9.04 with the Logitech QuickCam for Notebooks (usb ID 046d:08dd). I'm still troubleshooting, but if there are any clues out there, I'd appreciate hearing them.

---

### Post by no2498 on 2010-01-23
ok for the bad pic's get wxcam it has some settings in it
if not a good pic open ekiga softphone if you get a good pic go back try wxcam if its still bad go back ti ekiga put all settings to 0
i need to do it at times

---

### Post by aslok on 2010-12-12
```
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make menuconfig <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make install
v4l2ucp <-- Auto Gain off

```
[IMG]http://lh3.ggpht.com/_sV6UrDQh-5s/TQVaMwkuN_I/AAAAAAAAAb4/BnS5Jz95IWY/s800/ss85.png[/IMG]

---

