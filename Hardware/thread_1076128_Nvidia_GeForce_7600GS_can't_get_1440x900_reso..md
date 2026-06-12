---
title: "Nvidia GeForce 7600GS can't get 1440x900 reso."
date: 2009-02-21
forum: Hardware
---

### Post by jeffmanh on 2009-02-21
I have a Samsung SyncMaster 906BW LCD powered by my Nvidia GeForce 7600GS.
I have dual boot with XP and I can get a resolution of 1600x900 in xp (beautiful). But with Ubuntu (Hardy) the highest resolution I can get is 1024x768. Now the driver that is currently installed is the one the was provided to me by Envy (idk how to check which version). I've tried editing the xorg.conf file but have had no luck:(. 

I've got Compiz running and Ubutu is lovely, I just would like to get my full resolution. Never had this problem with OpenSUSE.

I've only been using Ubuntu for about a week, so you could say I'm sort of a noob. Any help would be greatly appreciated.

---

### Post by jeffmanh on 2009-03-08
Anyone!!, PLEEEZZ

---

### Post by taurus on 2009-03-08
Have you looked in System -> Preferences -> Screen Resolution?

---

### Post by nwadams on 2009-03-08
I have the same video card, use the closed source nvidia driver and it will work. 

system/administration/hardware drivers. It will allow you to enable it there. Will require a reboot to make it work.

---

### Post by jeffmanh on 2009-03-19
Sorry for the late response, but yes, I have checked the screen resolution, and the highest available is 1024x768.

Also, in proprietary drivers I get nothing listed. Something I forgot to mention in my first post is that I used Envy to install my video driver.

---

### Post by weemee on 2009-03-20
Hello,

Try having a go with this.  You may need to remove the existing driver as I have only ever used this process from a fresh install.

1) Firstly download the latest driver directly from [http://www.nvidia.com]("http://www.nvidia.com") - save to desktop and rename so file appears as nvid.run.

2) Whilst in Ubuntu, press CTRL, ALT and F1, this will drop you into a text based command line - fear not!  Login using your usual username and password.

3) Now we need to stop the GUI (AKA X server) running in the background.  The the following
```
sudo /etc/init.d/gdm stop
```

4) Now type ```
cd Desktop
```

5) Now type ```
sudo sh nvid.run
```

6) Follow the onscreen instructions.  Once complete you will be put back at the command line.

7) Type ```
sudo /etc/init.d/gdm start
```.  This will put you back into X server mode.  I suggest you restart at this point.

Hope it helps.

Weemee

---

### Post by rjsec4ever on 2009-03-20
Some better advice... update to Ubuntu 8.10 (or better yet, wait until next month for 9.04 :D). I run an on-board nVidia GeForce 6150SE @ 1440x900 ... BEAUTIFUL!

Also, check the proprietary hardware driver dialog (under System -> Administration). Update the driver to version 178. The nVidia website does have version 182 for all Linux distributions, however, I'm using 178.

---

### Post by jeffmanh on 2009-03-22
I actually did try 8.10, and tried the proprietary drivers to no luck, as a matter of fact, I couldn't get higher than 800x600 which was far worse. I've tried the latest nvidia driver from the website but have no luck either. I think I might try Intrepid once more before upgrading to Jaunty. I will keep you posted if I have any luck with Intrepid.

---

### Post by jeffmanh on 2009-03-22
OK, I just finished installing the latest Nvidia drivers from the website and now I'm running in low graphics mode. help!?

---

### Post by taurus on 2009-03-22
Did you remember to run

```
sudo nvidia-xconfig
```
Probably have to reboot.

---

### Post by jeffmanh on 2009-03-22
That didn't work, I'm still running in Low Graphics Mode.

---

### Post by taurus on 2009-03-22
And there are no higher resolutions that you can choose in System -> Preferences -> Screen Resolution?

---

### Post by jeffmanh on 2009-03-22
No

---

### Post by norwoods on 2009-03-22
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

