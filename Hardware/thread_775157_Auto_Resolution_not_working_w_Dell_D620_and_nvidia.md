---
title: "Auto Resolution not working w/ Dell D620 and nvidia card"
date: 2008-04-29
forum: Hardware
---

### Post by MystaMax on 2008-04-29
Hello, I have a Dell D620 laptop, and a  nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300 inside. When I first installed Hardy, it used the default driver vesa/nv(xorg.conf below). 

When I boot the laptop on the docking station with a Samsung SyncMaster 225BW 22" LCD Monitor attached, it booted to the default resolution of 1680x1050 w/o me changing anything (WOOHOO!). I booted on and off the docking station various times to make sure I got the same result, which I did. Off the docking station the laptop should (and did) boot to 1440x900.

 I'm a moderate compiz fusion user, and wanted some of the features. So, I had to install the nvidia drivers, which I did using the "Hardware Drivers" application.

After a reboot, and now with the nvidia-glx-new drivers, all my auto-configuration goodness was gone. When I boot on the docking station, I can't see anything when it boots on the Samsung 22" LCD, but I can hear the question.wav file when the login screen is ready. Also after the reboot, my resolution was 1280x800, instead of the default 1440x900. The screen resolution application didn't have 1440x900, so I had to use nvidia-settings to fix it. After changing my res to 1440x900, it was an available option in Screen Resolution application

I would really like the ability to dock my laptop and have it auto-config my display to whatever monitor is attached, using the nvidia drivers.. Currently, a Samsung 22" LCD (1680x1050).

Any ideas? 

[http://pastebin.ubuntu.com/8799/](http://pastebin.ubuntu.com/8799/) - My default xorg.conf file for Dell 620 w/ nVidia GeForce Go 7300 on Fresh Hardy Heron. Autoconfig worked nicely :) , no compiz fusion :(

[http://pastebin.ubuntu.com/8801/](http://pastebin.ubuntu.com/8801/) - My `lspci` . 

[http://pastebin.ubuntu.com/8803/](http://pastebin.ubuntu.com/8803/) - My xorg.conf with nvidia-glx-new installed. Autoconfig did not work properly with or without docking station. Resolution had to be adjusted via GUI or CLI.


Any ideas? Thanks.

---

### Post by chewearn on 2008-04-30
Ubuntu new auto-configuration don't work with nvidia restricted driver.  Instead, use nvidia-settings to generate a new xorg.conf.  Install nvidia-settings by:
```
sudo apt-get install nvidia-settings
```

---

### Post by MystaMax on 2008-04-30
Hi, thanks for the reply, but I've already done that. I mentioned it in my original post. After installing nvidia drivers no autoconfig works, I'm having to adjust manually. And when I use the docking station, I get no image on screen at all. I have to switch to the terminal and change xorg.conf, and restart X.

Any other ideas?

---

### Post by chewearn on 2008-04-30
Yeah, auto-configuration don't work with nvidia restricted driver.  I only know of people manually replacing xorg.conf.  First, use nvidia-settings to generate the xorg.conf for all screen/dock combinations; then write a script to copy the corresponding xorg.conf file when ever dock/undock.

I wish nvidia would fix their driver to use xrandr, but unfortunately they don't.

---

