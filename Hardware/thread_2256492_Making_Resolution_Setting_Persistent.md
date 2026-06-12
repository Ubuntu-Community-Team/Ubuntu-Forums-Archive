---
title: "Making Resolution Setting Persistent"
date: 2014-12-13
forum: Hardware
---

### Post by rbscairns on 2014-12-13
When I start my Ubuntu PC and log in, I am limited to a 1024x768 resolution on my wide-screen monitor.

[CENTER][ATTACH=CONFIG]258530[/ATTACH][/CENTER]

To get my required resolution of 1368x768, I useb xrandr

[CENTER][ATTACH=CONFIG]258531[/ATTACH][/CENTER]

This gives me an acceptable resolution. I now want to make this resolution persistent at the login screen and for all users.

I have tried to follow the recommendations at [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions). That refers to /etc/gdm/ and /etc/kde4/kdm/Xsetup as a place where to paste an xrandr command line string to set the persistent resolution. My Ubuntu 14.04 has neither of these folders/files.

How do i go about setting a persistent resolution at the login screen and for all users?

---

### Post by rbscairns on 2014-12-13
I can understand that the following code will need to run before the login screen:

```
xrandr --newmode "1368x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync
xrandr --addmode VGA1 1368x768_60.00
```

How do I do this and where do I put it?

Remember this is Ubuntu 14.04 I am dealing with and a lot of the older Ubuntu version config files have changed.

---

### Post by rbscairns on 2014-12-13
After reading [terdon's post here]("http://askubuntu.com/questions/445957/is-it-normal-for-lightdm-conf-edits-to-not-affect-the-desktop-screen-resolution/446050#446050"), it would appear that I need to make my 1368x768 resolution available to Unity and let it handle the setting. To do this, I made a shell script file /usr/bin/lightdmxrandr.sh

```
#!/bin/sh
xrandr --newmode "1368x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync
xrandr --addmode VGA1 1368x768_60.00
```

As recommended by terdon, I then added the line "session-setup-script=/usr/bin/lightdmxrandr.sh" to the /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf file so the file looked like:

```
[SeatDefaults]
user-session=ubuntu
session-setup-script=/usr/bin/lightdmxrandr.sh
```

I then rebooted and it kind of works. I do not get my 1368x768 resolution for the log-in screen and after logging in I get a split screen for a few seconds (at 1368x768) until things settle down to the screen I want.

It would be nice to have the 1368x768 resolution for the log-in screen.

---

