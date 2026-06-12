---
title: "Can't install Nvidia proprietary drivers. Always reverts to low graphics mode"
date: 2015-10-05
forum: Hardware
---

### Post by ryanch94 on 2015-10-05
So I'm having trouble installing the Nvidia proprietary drivers on my PC with an GTX 660. I was able to get it working before about a year ago when I last installed Ubuntu on here. But now when I install the driver it reverts to low graphics mode on rebooting and the only way to get it working again is to revert back to the nouveau driver. Anyone know what might be causing this?

lspci output:
```
ryan@ryan-desktop:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8422]
    Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK106 HDMI Audio Controller [10de:0e0b] (rev a1)


```

---

### Post by Bashing-om on 2015-10-05
ryanch94; Hello;

The Nvidia GTX 660 is well supported.

How have you been attempting to install the proprietary driver ? OEM install ?
Is the UN-install scripts still present on the system ?
```

sudo find / -name "NVIDIA-Linux-*"

```

What other Nvidia packages are present - is there a conflict condition ?
```

dpkg -l | grep nvidia
ls -al /etc/X11/xorg.conf

```

Clean up the cruft, and install the proprietary driver from our software repository .

[INDENT][INDENT]see if we can find
[INDENT][INDENT][INDENT]that reason why
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ryanch94 on 2015-10-06
> **Bashing-om said:**
> ryanch94; Hello;

The Nvidia GTX 660 is well supported.

How have you been attempting to install the proprietary driver ? OEM install ?
Is the UN-install scripts still present on the system ?
```

sudo find / -name "NVIDIA-Linux-*"

```

What other Nvidia packages are present - is there a conflict condition ?
```

dpkg -l | grep nvidia
ls -al /etc/X11/xorg.conf

```

Clean up the cruft, and install the proprietary driver from our software repository .[INDENT][INDENT]see if we can find[INDENT][INDENT][INDENT]that reason why
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi,

I've been installing the drivers through the Additional Drivers window in the settings. I keep trying on clean installs but it does the same thing each time.

First I install the driver through Additional Drivers, which appears to work fine:
[IMG]http://i710.photobucket.com/albums/ww106/ryanch09/IMG_20151006_092139837_HDR_zpsbejmqaai.jpg[/IMG]

Next, I reboot the system, this is where it all goes downhill:
[IMG]http://i710.photobucket.com/albums/ww106/ryanch09/IMG_20151006_092251438_zpsfpmbbdvs.jpg[/IMG]

From here on I can only use the terminal. Here's the output of 'dpkg -l | grep nvidia':
[IMG]http://i710.photobucket.com/albums/ww106/ryanch09/IMG_20151006_093110756_zpsiots8zw5.jpg[/IMG]

Running "ls -al /etc/X11/xorg.conf" gives me the output:
```
ls: cannot access /etc/X11/xorg.conf: No such file or directory
```

---

### Post by Bashing-om on 2015-10-06
ryanch94; Hey, hey ....

You are doing well .. all looks prim and proper. There is no fault with your procedure to install the proprietary driver.
However .. that driver does require the config file that is not present. let's make up one -automagically.
```

sudo nvidia-xconfig

```
(the same affect can be done from the GUI nvidia-settings)

Reboot and let's see the effect.
IF all is not good, we want to see the why. The system is very good about reports and advising on what it is doing. The main one we want to look at is cat /var/log/Xorg.0.log .
Post back - Between code Tags, please - the output of terminal command:
```

cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we will see
[INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by ryanch94 on 2015-10-06
> **Bashing-om said:**
> ryanch94; Hey, hey ....

You are doing well .. all looks prim and proper. There is no fault with your procedure to install the proprietary driver.
However .. that driver does require the config file that is not present. let's make up one -automagically.
```

sudo nvidia-xconfig

```
(the same affect can be done from the GUI nvidia-settings)

Reboot and let's see the effect.
IF all is not good, we want to see the why. The system is very good about reports and advising on what it is doing. The main one we want to look at is cat /var/log/Xorg.0.log .
Post back - Between code Tags, please - the output of terminal command:
```

cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we will see[INDENT][INDENT][INDENT]what tale gets told
[/INDENT]
[/INDENT]
[/INDENT]


It's all good! Running ```
sudo nvidia-xconfig
``` fixed it! At least I know now to try that if it happens again in the future.

Thanks for your help Bashing-om! :D

---

### Post by Bashing-om on 2015-10-06
ryanch94; Outstanding !

Pleased all worked out . You do do good work.

As this situation has a happy conclusion:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Happy trails to you
[/INDENT][/INDENT]

---

