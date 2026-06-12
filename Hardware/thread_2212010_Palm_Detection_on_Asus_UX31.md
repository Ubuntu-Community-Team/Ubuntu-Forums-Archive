---
title: "Palm Detection on Asus UX31"
date: 2014-03-18
forum: Hardware
---

### Post by Jacob_Gerlach on 2014-03-18
Asus UX31 running 12.04, Elantech touchpad

I have serious issues with palm bumps.

"Disable touchpad while typing" selected in default mouse and touchpad settings. This apparently has no effect - I can type with one hand and move the mouse with the other whether it's selected or not.

"Palm Detection" selected with GPointing Device Settings, which I installed based on a recommendation in another thread. No change with range set all the way up or down (wasn't sure which was which) - I can scroll with my palm as easily as with my finger. I can drag the slider for pressure, but when I close the setting box and reopen it, it's always back down at minimum.

GPointing also has an option to disable touchpad when other devices connected that doesn't work for me.

I have seen some posts involving command line modification of syndaemon. I haven't tried this yet - wanted to see if there is something I can change to make the GUI options do what they say they do...

---

### Post by varunendra on 2014-03-21
Please try this -
```
synclient PalmDetect=1
synclient PalmMinWidth=3
```

Any better? If it works as expected, we can make it permanent by writing a two line script, and adding it to your /etc/rc.local file.

---

### Post by Jacob_Gerlach on 2014-03-21
Initial impression is that it is helping. I will report back and mark as solved if it works well over the next day or so.

Is there no GUI front end for this? Should Gpointing settings be setting PalmDetect with it's palm detection option or is it using something else (I'm wondering if there is a bug)?

While this may solve my problem, it also doesn't explain why the "disable while typing" option doesn't work. Is there something I can do to confirm whether or not this is a bug to report?

In any case, thanks for the solution, hopefully it works well!

---

### Post by varunendra on 2014-03-21
Let me first answer what I'm certain about -
> **Jacob_Gerlach said:**
> Initial impression is that it is helping. I will report back and mark as solved if it works well over the next day or so.
As mentioned in my previous post, this would be temporary and the commands would be needed to be run after every reboot. To make it permanent, create a script by saving these lines to a new plain-text file -
```
#!/bin/bash

sleep 20
synclient PalmDetect=1 && synclient PalmMinWidth=3
```
The "sleep 20" command makes the script to wait 20 seconds before executing the commands, so that the drivers are loaded and ready to accept the commands. You can change "20" to a lower value if your system loads faster (or higher value if the system is slower than mine).

Save this file as, say, "PalmDetect.sh" in your Home directory. Then make it executable -
```
chmod +x PalmDetect.sh
```

Now to make it run automatically on each boot, add this script to your **/etc/rc.local** file with the following command -
```
sudo sed -i **'/^exit 0/i /home/[COLOR="#0000CD"]*jacob*[/COLOR]/PalmDetect.sh &&'** /etc/rc.local
```
This will insert the line "**/home/[COLOR="#0000CD"]*jacob*[/COLOR]/PalmDetect.sh &&**" just above the line "exit 0" in the file. I'm **_assuming_** here that your user id is "**[COLOR="#0000CD"]*jacob*[/COLOR]**" on this system. If it is something else, change it accordingly. The idea is to provide the "Absolute" path to the script so it is executed properly.
-----------------------------------------------------------------

Now answers to the remaining questions -
> Is there no GUI front end for this? Should Gpointing settings be setting PalmDetect with it's palm detection option or is it using something else (I'm wondering if there is a bug)?
Yes there are GUI options, Gpointing-Device-Settings being one of them. Since it didn't work, I suggested what I know to be more promising. I *believe* Gpointing device or other GUI programs control the same settings (and probably much more) as we did with "synclient" command, but they seem to do it a bit differently and provide their own range of settings.

> While this may solve my problem, it also doesn't explain why the "disable while typing" option doesn't work. Is there something I can do to confirm whether or not this is a bug to report?
I have seen a few other threads about this and it does seem to be a bug in 13.10 and later. Open "dconf Editor" (it should be already installed, otherwise install it first) and navigate to **"org > gnome > settings-daemon > peripherals > touchpad"** and see if the setting **"disable-while-typing"** is there and enabled. If the setting is not there, or if it is there and enabled but doesn't work, then it certainly a bug which should be reported (at launchpad).

I'd like to admit that I haven't tried to search if such a bug is already reported to which you can (and should) add yourself as "Affected".

---

### Post by Jacob_Gerlach on 2014-03-25
After using this for a while, this has mostly solved my problem. I still get the occasional bump, but much much better than before.

I filed bug reports against [gpointing-device settings]("https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/1295919") (for not disabling touchpad while other devices connected) and [gnome-control-center]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1295914") for disable-while-typing.

I didn't file a bug against gpointing not setting PalmDetect in synclient, since it's not clear to me if that is how it handles it or if it tries to accomplish palm detection in some other way.

Thanks for the help.

---

