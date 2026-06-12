---
title: "How I did: touchscreen calibration in Gigabyte M912, Karmic"
date: 2010-01-07
forum: Hardware
---

### Post by JC Cheloven on 2010-01-07
Hi, this is intended to help people with the exact described problem. I'm not an expert in touchscreens. In fact, I didn't see one until yesterday, and I'll probably not see one again anytime soon. Simply a friend came yesterday to me with his shiny new Gigabit M912 tablet pc, and we installed karmic.

Everything appeared to work, but the touchscreen had an error of about 5mm at the borders of the screen (less in the central zone). Enough to make it unusable to access the upper and lower panels. The calibration process was a bit weird, but finally I got it calibrated. Here's what I did in my final trial:

- Downloaded the "PenMount Ubuntu 9.10 Driver V2.4.4.tar.gz" from [here]("http://www.penmount.com/Download/Driver/PenMount/").
- Extracted it to my home directory. A "pmlinux-ubuntu910-20091022" directory is created.
- Removed the package "xserver-xorg-input-wacom", using synaptic. It seems to interfere with the touchscreen driver.
- Opened a terminal. Entered these commands (press enter after each one):
```
cd ~/pmlinux-ubuntu910-20091022
sudo ./install.sh
```
- The graphic user interface was gone. A b&w bash console appears, asking me for login. Ok, don't panic. Gave my username and password. Re-entered the above commands from this bash console.
- Restarted the system (I actually don't remember wheteher I did "sudo shutdown -h now", or the system restarted by itself).
- After restart, I was greeted with an icon in the upper panel, next to the clock, which allows me to calibrate the touchscreen.
- I tried 25 points calibration, but it hanged at point 23. I tried with 16 points and everything was ok. 

That's it.

I realize that a smarter procedure can be devised from this. For example entering in console mode by ctrl-alt-F1 instead of letting the gui crash due to (most likely) an internal error, etc. But since I don't have the tablet pc at hand, I can't test any more, and I'm posting what I did without any guessing.

This is a quick'n'dirty solution though. If someone with the hardware at hand tests a smarter procedure, please post it for general advice. Thanks.

EDIT: I think the touchscreen was a Penmount6000

---

### Post by alonf01 on 2010-02-15
Hi All, I have Ubuntu 9.10 on M912 Gigabite.
I found this instractions very helpfull, thank you JC Cheloven, but it seems like you do not have to remove packages at all, just download the "PenMount Ubuntu 9.10 Driver V2.4.4.tar.gz", unpack it, and install:
 
cd ~/pmlinux-ubuntu910-20091022sudo ./install.sh
 The graphic user interface will be gone. A b&w bash console will appear, asking for login. After login, re-entered the above commands from this bash console. And the system will restart by it self. I tried with 16 points and everything was ok. 
 
All Best,
Alon.

---

### Post by vyszard on 2010-06-29
Hi I also have Gigabyte M912. Before when it has Ubuntu 9.10 installed I had the same issue and did the same thing. Lately I reinstalled my netbook with Ubuntu 10.04, so I try to install PenMount driver again. Everything works well, there's not even B&W bash console. But when I try calibrating, the red point appears a little bit outside my screen and then it won't respond no matter where I touch.

I still can't calibrate my touch screen until now. Any help?

---

### Post by JC Cheloven on 2010-07-03
> **vyszard said:**
> Hi I also have Gigabyte M912. Before when it has Ubuntu 9.10 installed I had the same issue and did the same thing. Lately I reinstalled my netbook with Ubuntu 10.04, so I try to install PenMount driver again. Everything works well, there's not even B&W bash console. But when I try calibrating, the red point appears a little bit outside my screen and then it won't respond no matter where I touch.

I still can't calibrate my touch screen until now. Any help?

Confirmed here. Yesterday my friend came back with the netbook, and calibration behaved as you describe. Not sure of what he did before though (he tried to install by himself...)

I'll have a look this weekend. If I happen to find out something useful, I'll come back with it. Please do the same if you can ;-)

JC

---

### Post by JC Cheloven on 2010-07-06
OK, I figured it out.

To make the history short, the touchscreen works out of the box, but slightly out of tune at the borders. The problem is that the calibration tool for lucid seems to be completely buggy. That tool is called gCal, a binary.

Likely you have the penmount package for lucid. The name of the directory after unpacking it was (for me) pmlinux-ubuntu1004-20100326. In there is the file "gCal" (17.9kB). Please rename it. Something as "useless-gCal" will do.

Hopefully you still have the penmount package for karmic. The name of the directory after unpacking it was (for me) pmlinux-ubuntu910-20091022. Please copy the file "gCal" (21.9kB) from this directory and paste it to the lucid directory.

From terminal, change your current directory to the lucid one (pmlinux-ubuntu1004-20100326), and install the tweaked lucid package

```
sudo ./install.sh
```

After reboot, the expected penmount icon appears in the upper panel. Clicking on it makes it to simply disappear!! Also the touchscreen is freaking uncalibrated!! Don't worry, a working version of the gCal calibration program has been installed in an accesible place (it was /usr/sbin I think). So from terminal run 

```
sudo gCal 9
```

You'll get to a 9-point calibration process, which is responsive and works. Folow the process and you're done.

Note: I tried to run gCal without installation, but it seems to miss some files that are settled during installation. To sum up: it didn't work.

---

