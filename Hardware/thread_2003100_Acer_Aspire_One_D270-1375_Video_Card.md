---
title: "Acer Aspire One D270-1375 Video Card"
date: 2012-06-13
forum: Hardware
---

### Post by Mercury305 on 2012-06-13
Hi,

I bought the new Atom N2600 Laptop. However, I can't adjust resolution and video playback is really messed up.

Its a very hot and recent laptop at a good price so I am sure there are many others suffering from the same problem as well.

I checked to see Aspire One laptops are Linux certified.

I personally love my new lap. However without enjoying a good video config. i really can't say I am enjoying the Linux experience with it since i cant watch videos and I cant dim my screen either.

I hate windows and I don't want to return my laptop. So please help!:)

---

### Post by idrinktea on 2012-06-14
To fix the brightness problem, in a terminal, type:

sudo setpci -s "00:02.0" F4.B=40

You can change 40 to a lower value to decrease the brightness and vice versa.

If you don't want to have to manually change the brightness in the terminal every time, just edit /etc/rc.local file to include the above line before the the line "exit 0". Then save the file and restart. So now the screen will automatically decrease in brightness whenever you boot into Ubuntu.

Have a read here: [http://ubuntuforums.org/showthread.php?t=2001515](http://ubuntuforums.org/showthread.php?t=2001515)

The Acer D270 is a great machine. I really love mine. :D

EDIT: I have no problems with the resolution and video playback(although it can't play 1080p HD video properly). I've installed Linux Mint Mate Edition 64 bit(which is based on Ubuntu 12.04)

---

### Post by Mercury305 on 2012-06-14
thanks for the terminal commands. But there is a huge difference in comfort when u hit (Fn + Right/Left Arrow key) compared to goin to terminal. I frequently adjust my brightness depending on how dark my room is. This way my eyes don't get hurt. But my bigger problem is a decent driver. As you can see I am also limited with resolution options and the worst is the video playback. Have you tried youtube? Playback is horrible on this laptop. If I can't experience a good desktop env. with ubuntu I am gonna just switch to debian + windows. I also have problems with the Acer Aspire One 722 my second laptop but that 1 with headaches at least I was able work around it. But thanks again for the terminal commands.

---

### Post by Mercury305 on 2012-06-14
BTW, the link you posted I don't think it is solely for the AOD270-1375... as that came out this year. But my fan is always running as well. I guess linux is a lot more compat with Asus then Acers. Never had any problems with Asus.

---

### Post by Mercury305 on 2012-06-14
yea the 1375 using the new intel n2600 cpu has different video card then the other d270 versions.
I will try the Mint version. I never tried Mint so far.

---

### Post by RTPDr on 2012-10-21
I am a new to linux. I removed the Linpus linux that came along with ACER AOD270 Atom N2600. It runs on Cedar Trail platform (I am not a techee) and intel has incorporated the drivers with their own linux distro Meego 1.2. I ve tried Ubuntu 12.04 and after installing couldn't adjust the brightness. But after updating it showed to install additional drivers and installed the Cedarview drivers. Those crashed after some time, without much problems and Now I am very happy with Linuxmint13. Searched the synaptic for cedar and installed 4 softwares for cedartrial and cedarview and I played a movie 1920x800 nicely. For adjusting brighness , the Fn+ arrow keys worked well. Additional brighness reduction was achieved with RedshiftGUI.:guitar:

---

