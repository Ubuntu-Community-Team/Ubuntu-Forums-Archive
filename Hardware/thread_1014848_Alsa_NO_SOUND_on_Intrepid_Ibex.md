---
title: "Alsa NO SOUND on Intrepid Ibex"
date: 2008-12-18
forum: Hardware
---

### Post by Stupid_Guy on 2008-12-18
Hello, 
I'm using Ubuntu 8.10 (64-bit) on Vaio VGN-FZ29VN, few days ago I tried to install manually the last version of ALSA (cause ONLY shuffles didn't work) but building failed. When I rebooted I've lost all sounds except a BEEP XD (f.e. when I receive mails)... GStreamer is disabled and it say that : 
No volume control GStreamer plugins and/or devices found.
----
$ aplay -l
aplay: device_list:215: no soundcards found...
----
 lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
----

I tried to reinstall both ALSA and GStreamer but didn't work...

Please someone help me!!! :confused:
Thanks in advance.

---

### Post by albinootje on 2008-12-18
> **Stupid_Guy said:**
> Hello, 
I'm using Ubuntu 8.10 (64-bit) on Vaio VGN-FZ29VN, few days ago I tried to install manually the last version of ALSA (cause ONLY shuffles didn't work) but building failed.

Can you show us the relevant error messages of the failed building ?

---

### Post by jpmelos on 2008-12-18
Hello.

Well, I'm not sure it will help you, but everytime I install a fresh Ubuntu, no matter what version, in my VAIO, I have to follow these steps:

To reinstall ALSA driver, run:

```
$ sudo su
# apt-get update
# apt-get install module-assistant
# m-a update
# m-a prepare
# m-a a-i alsa
```

in terminal. These steps may take a while. Then:

```
# gedit /etc/modprobe.d/alsa-base
```

Add the following line in opened config file:

```
options snd-hda-intel model=vaio position_fix=0
```

Now, reboot your VAIO. If it doesn't work this way, try update Ubuntu and add this line right after the "apt-get update":

```
# apt-get install build-essentials
```

Hope it helps you! :D

---

### Post by Stupid_Guy on 2008-12-18
@albinootje : unfortunately I lost the build log...
@jpmelos : ALSA build fails with this log (only the last piece):

 /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit 
declaration of function‘PAGE_ALIGN’
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2  


I don't want to go back to Win!!! Damn!!! :mad:
Thank you for your help! I love this community!!

---

### Post by albinootje on 2008-12-18
> **Stupid_Guy said:**
> 
 /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit 
declaration of function‘PAGE_ALIGN’
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2  

Can you try :
cd /usr/src/modules/alsa-driver
sudo make clean
And then try again ?

---

### Post by Stupid_Guy on 2008-12-18
albinootje, I tried but I've got the same result...:cry:

---

### Post by duanedesign on 2009-01-02
these are 3 very good threads that deal with sound issues. hope on of them helps

[http://ubuntuforums.org/showthread.php?t=1012179](http://ubuntuforums.org/showthread.php?t=1012179)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

