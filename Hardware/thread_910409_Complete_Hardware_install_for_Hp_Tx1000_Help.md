---
title: "Complete Hardware install for Hp Tx1000 Help"
date: 2008-09-04
forum: Hardware
---

### Post by _tragic_ on 2008-09-04
I can't Seem to get it all installed right my current issues still are:

Webcam won't work online webchat
microphone don't work
tablet features dont work
when i close the lid the screen bugs out and i have to log out then back in to correct it
i need help with the close lid suspend feature

also is it possible to create a graphical boot up os picker thingy

i used the windows install of ubuntu 8.04.1 LTS

any help with this would be great i have checked around for  another option before posting but most everything out there didnt work.

---

### Post by _tragic_ on 2008-09-04
please any help would be great!

---

### Post by _tragic_ on 2008-09-04
bump

---

### Post by _tragic_ on 2008-09-05
im still totally lost on this any help would be sweet.

---

### Post by Crafty Kisses on 2008-09-05
For the webcam try this:

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)



To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.



If Ekiga doesn't work post results of the command > lsusb

---

### Post by _tragic_ on 2008-09-05
> **Codename said:**
> For the webcam try this:

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)



To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.



If Ekiga doesn't work post results of the command > lsusb

the cam works it just dont work when im trying to do videochat on webdate.

---

### Post by PoHandle on 2008-09-24
What version of Hardy are you using?  32bit or 64bit?  (i am still having a little trouble with 64bit)

Try installing the drivers with EasyCam2: [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

The Mics on either side of the webcam work for me, I had to unmute them in alsamixer.

For the tablet feature, check out: [http://ubuntuforums.org/showpost.php?p=4900007&postcount=963](http://ubuntuforums.org/showpost.php?p=4900007&postcount=963)

As far as your screen bugging out, I was able to fix mine by disabling the kernel framebuffer.
```
sudo dpkg-reconfigure xserver-xorg
```
Then when it asks you if you want to enable the video kernel framebuffer, select "NO" and continue with the default settings for the rest of the configuration.
I assume you are using the nVidia driver, so type
```
sudo nvidia-xconfig
```
then restart your Xserver with crtl+alt+bksp.

Hope this helps.

---

