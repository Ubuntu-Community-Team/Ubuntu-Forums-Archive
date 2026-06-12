---
title: "Media Keys not working"
date: 2014-04-18
forum: Hardware
---

### Post by rkarulkar94 on 2014-04-18
I have a Dell Inspiron 15R running 14.04. My media keys (Play/pause, next, prev) have not been working. The functions work if I set different shortcuts, but my inbuilt media keys don't work. I tried using these keys in the VLC media player, but they still don't work. What could be wrong? How can I fix it?

---

### Post by atqueensu on 2014-05-10
Here is the bug report [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1302885](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1302885)
& here you go, this should do the trick...

                        The problem is that an incorrect string is set in dconf key: (Example)

 Original (working) value:
~$ gsettings get org.gnome.settings-daemon.plugins.media-keys volume-up
'XF86AudioRaiseVolume'

 After running "unity-control-center keyboard", and setting the shortcut for
volume-up key:
~$ gsettings get org.gnome.settings-daemon.plugins.media-keys volume-up
'AudioRaiseVolume'
 The new value misses the "XF86" part of the string, and does not work.
 You can get the key working again by resetting the value, with:
~$ gsettings reset org.gnome.settings-daemon.plugins.media-keys volume-up

              


to reset key using GUI, you can install dcobfig-tools

$ sudo apt-get install dconf-tools

---

### Post by rkarulkar94 on 2014-05-10
That worked. Thanks.

---

### Post by futak-eric on 2014-08-24
Hey, I am having the same issue on lubuntu, but regarding the media keys Play/Pause, Next and Previous. They worked great in ubuntu, but my guess is that the the lighter version lubuntu nixes a lot of features like this. That's my guess anyway. I still don't have enough posts on this forum to post a pic, but my play, pause, previous and next button values in dconf begin with xf86, as well as the volume button values. Any thoughts? Tried the command line for the volume control problem abouve but replaced with play and so forth for the others. No change yet, I'll try logo.

 I'd appreciate any help!

---

### Post by futak-eric on 2014-08-24
logging off didn't do the trick

---

