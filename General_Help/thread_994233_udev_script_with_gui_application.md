---
title: "udev script with gui application"
date: 2008-11-26
forum: General Help
---

### Post by jansch75 on 2008-11-26
I need help for strange problem. I would like to start a script in the moment I plug my USB external hard drive to my ubuntu 8.04 desktop PC. The script uses zenity to show an icon on my desktop... and this creates a lot of trouble for me...

My udev rule looks like this:

```
# USB WD_EXTERNAL hard drive
BUS =="usb", KERNEL=="sd?1", SYSFS{serial}=="5758453830384B3741313837",SYMLINK+="WD_EXTERNAL",RUN+="/usr/local/bin/WD_Externalharddrive.sh"
```

The script starts like this:

```
#!/bin/bash
# Put a notification-icon into the system tray
set -x 
xhost local:MYUSERNAME
export DISPLAY=:0.0
/usr/bin/zenity --notification --window-icon=/usr/share/pixmaps/USB-Drive-32x32.png --text="WD_EXTERNAL 320 GB found."

```

My strange problem is the following: This udev script works fine BUT ONLY if have started it ONCE BEFORE from the terminal... In other words: If I plug my external hard drive and have not started the script once before from the terminal I will not see the icon. If I have started the script once before from the terminal, I can plug the external USB Hard drive and the icon will appear. After reboot of the computer some settings change which force me to run the script once from the terminal before it again also can be started by the udev rule.

I guess it is some problem with gui. If I plug in my hard drive after reboot of the computer, I will not see the icon. But if I run my script from the terminal directly afterwards, the icon will appear twice! This is a good indication (I guess?) that udev has properly started the script but somehow could not find the right display to show the zenity icon...

Anyone, who knows how to start gui windows, icons, messages in a script which will be started by an udev rule??? I have googled a lot, but none of the solutions could help me...

Another (not so urgent) problem: The icon should be shown on the screen as long the hard drive is plugged into my computer. According to the informations about udev, udev will be stopped as long as the script runs... How can I detach the script that it does not block udev as long as the hard drive is plugged into my computer...???

---

### Post by everthonvaladao on 2009-03-19
> **jansch75 said:**
> (...) This is a good indication (I guess?) that udev has properly started the script but somehow could not find the right display to show the zenity icon...

Well, here it works like a charm! Try adding & after the zenity command or reloading the udev rules with:
```
sudo udevadm control reload_rules
```

> **jansch75 said:**
> 
Anyone, who knows how to start gui windows, icons, messages in a script which will be started by an udev rule??? I have googled a lot, but none of the solutions could help me...


You gave me the first tip by adding this to the beggining some script started by udev:

```

#!/bin/bash
set -x 
xhost local:MYUSERNAME
export DISPLAY=:0.0

```

But your zenity icon was executed with root privileges. So if you wanna run some GUI app with your user privileges, you run it this way:

```
su MYUSERNAME -c '/usr/bin/some-gui-app arg1 arg2 etc'
```

> **jansch75 said:**
> Another (not so urgent) problem: The icon should be shown on the screen as long the hard drive is plugged into my computer. According to the informations about udev, udev will be stopped as long as the script runs... How can I detach the script that it does not block udev as long as the hard drive is plugged into my computer...???

The zenity icon is showed until you click it, so you could add some udev rule to remove the zenity icon after you detach your drive, something like:
```
ACTION=="remove", <YOUR HARD DRIVE RULE>, RUN+="/usr/bin/kill -9 $PID_ZENITY"

```

[]'s

---

### Post by drbrando007 on 2009-03-20
You seem to have good handle on the udev, I was wondering if you could post some more info on udev threading,(i.e., split a user or application thread off from the main thread)?

Or hell, maybe just a good place to learn more about udev.


Thanks for your very informative post!


-Cheers

---

### Post by theOGRE on 2012-03-06
This worked great for my need.(3 years later)
Thanks for posting.

---

