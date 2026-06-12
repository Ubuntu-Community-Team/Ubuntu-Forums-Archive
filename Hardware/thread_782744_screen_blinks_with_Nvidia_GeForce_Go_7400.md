---
title: "screen blinks with Nvidia GeForce Go 7400"
date: 2008-05-05
forum: Hardware
---

### Post by ryu kun on 2008-05-05
I have a HP Pavilion dv5158ea notebook. When I enable Nvidia drivers on Ubuntu 8.04, its screen blinks (goes black for an instant) once in a while. When I disable the drivers there is no problem.

Could you please help me to solve this problem? 

Should I upgrade my nvidia drivers? I have installed them by using "System-Admin-Hardware Drivers" menu. Could you tell me how can I learn version of nvidia drivers in use?

---

### Post by diablillo77 on 2008-05-05
I have a dell XPS with the same graphics card. I used Envy to install nvidia driver v. 96.43.05. I use an external monitor a lot and that driver will automatically detect it and shuts off my laptop screen when the external monitor is plugged in. You just have to restart you X every time you plug and unplug (Ctrl-alt-backspace)
You should be able to "sudo apt-get install envyng-gtk" with universe repo enabled. The newest driver also works but it's a pain to get it to detect my external monitor. So, once envyng is installed, I like to shutdown X "sudo /etc/init.d/gdm stop" and run "envyng -t" go with option 1 for the latest driver if you don't need external monitor support or option 5 to manually select 96.43.05. The process is pretty self-explanatory. After the driver is installed, just restart your machine and you should be back in business. Envy will also make the necessary modifications to your xorg-conf.

---

### Post by ryu kun on 2008-05-05
diablillo77, thanks for your reply, but my problem is blinking of my laptop's screen. I don't use an external monitor, therefore I could not understand how your answer is related to my problem.

By the way, I found out that the application of "Nvidia X Server Settings" shows Nvidia driver version in use. The version on which I have blink problem is 169.12, latest version according to the [official site]("http://www.nvidia.com/object/linux_display_ia32_169.12.html").

---

### Post by ryu kun on 2008-11-01
My problem was solved after adding following code to /etc/modprobe.d/options

```
NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Reference 1: [http://www.nvnews.net/vbulletin/showthread.php?t=112769](http://www.nvnews.net/vbulletin/showthread.php?t=112769)
Reference 2: [http://www.nvnews.net/vbulletin/showthread.php?t=96673](http://www.nvnews.net/vbulletin/showthread.php?t=96673)

---

