---
title: "Dual monitor not working (14.04)"
date: 2017-03-07
forum: Hardware
---

### Post by jrglez on 2017-03-07
Hello,
First of all, forgive me for posting yet once more about the same thing, but none of the previous answers fixed my problem. 
I am trying to use two monitors in Ubuntu 14.04, and it was working, but after I turned on the computer today, it stopped working. 
I have tried using the different drivers under "Additional Drivers", this is, nvidia 378.13 and 375.26 and X.Org X server. 378.13 is how I got it working originally, but now none of them do. I have also tried a few other things that I read online, like creating a new [nvidia config file]("http://paste.ubuntu.com/24130790/"). Finally, I could not find any errors in [Xorg.0.log]("http://paste.ubuntu.com/24130786/").

Thanks

---

### Post by Bucky Ball on 2017-03-07
Try installing arandr from the official repositories (Software Manager or whatever it is now called in Ubuntu). You can also install it using a terminal with

```
sudo apt install arandr
```

Launch that and see if it shows both monitors. If so, right click the one that's off and 'Activate'.

Any luck?

You tell us both monitors were working and now they're not, but not whether both monitors are now not working or just one. Please confirm your situation.

---

### Post by jrglez on 2017-03-07
Hello,
arandr only shows one monitor. 
I have one monitor trough DVI and another one with HDMI, now only the DVI one works.

---

### Post by Bucky Ball on 2017-03-07
Open 'Additional Drivers' again and install the recommended driver. Reboot and open a terminal and give us the output of this command.

```
sudo lshw -C video
```

Might sound silly, but have you another HDMI cable you can try or can you try other HDMI socket on the monitor or video card?

You are trying to use two computer monitors and not a monitor and a television?

---

### Post by jrglez on 2017-03-07
I am not sure what the recommended drivers are or how to check that, but I am using 378.15 ([this]("http://share.pho.to/AdQHU") are the options I have). [This]("http://paste.ubuntu.com/24131578/") is what I get after running lshw.
I don't have another cable and there is only one socket in the monitor and video card. But I I have tried the cable and monitor in my laptop (also Ubuntu 14.04) and it works fine.

Thanks!
Juan

---

### Post by Bucky Ball on 2017-03-07
Your output is not saying much about your video card apart from that it is NVidia. Do you know what the video card is?

Please just paste terminal output here and put code tags around it (see link in my signature). Thanks.

---

### Post by jrglez on 2017-03-08
I had been trying to find what my graphic card is for a while, without much luck. Finally today, the person that bought the computer has sent me the specifications. It's a NVIDIA GeForce GTX 960.

When I got to work this morning, both screens were working and they did until a while back. But after I left the computer idle the monitors turned off and none of them were working when I came back. After waiting a little longer, the main display has started working again, but not the other one.

Thanks.

---

### Post by Bucky Ball on 2017-03-08
Are you sure they weren't in power saving mode? When you leave the machine and the screens are off when you come back, you should be able to hit any key and they'll come back on. Shouldn't be a matter of waiting. Hmm. :-k

---

### Post by jrglez on 2017-03-09
Yes, they were in power saving mode, but I think there is some problem when trying to come back (I had a similar problem with my old laptop). And anyway, in the end the second monitor was never detected again.

---

### Post by Bucky Ball on 2017-03-09
I had something similar going on with an Xubuntu-core install I was fiddling with. It may be a conflict between Light Locker and another power saver. Have a look at the settings in Lightlocker (I think you should have that installed by default, don't install if not) and in the other power manager and see if you can see anything obvious. If Light Locker monitor power saving is on, you might try switching it off and trying to isolate all power management of the monitors to the other power manager.

Or vice versa ...

(I have XFCE Power Manager. You may have Gnome Power Manager or something else *and* Light Locker. Have a sniff around.)

---

