---
title: "Setting the DVD drive speed"
date: 2012-01-06
forum: Hardware
---

### Post by bnilsson on 2012-01-06
Hi!

There are a few threads that describes how to control the DVD drive speed to reduce the acoustic noise from the drive while watching a movie, usually by "eject -x <speed>" or by the "speedcontrol" program. Works fine, except for one thing: The drive speed setting is cleared and returned to maximum whenever media is changed, which is very annoying. You have to bring up the Terminal every time you want to watch another movie.

Is there any way to set this permanently?
Or some automount initscript connected to the /dev/cdrom or /dev/dvd mount event, where the "eject -x <speed> can be added?

Ultimately, a drive speed setting in totem would be preferred. 
Or maybe a general system setting exists?


BN

---

### Post by khelben1979 on 2012-01-06
> **bnilsson said:**
> Is there any way to set this permanently?

Yes, there is a permanent fix. I simply don't remember it exactly though, but...

You can use the **hdparm** command with the **-e** parameter. See the man page for more details. I am not sure if that's the correct way of slowing it down permanently as it supposed to work by itself, I think that your Ubuntu system lacks important packages to make this happen. [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") is an important package to have installed, and once you go there, more packages should get added in the process.

---

### Post by bnilsson on 2012-01-06
Sorry to hear you didn't remember, since hdparm is also cleared when changing media.

---

### Post by khelben1979 on 2012-01-06
Well, I have never known it exactly, so I'm not sorry. :) 

I simply installed some non-free system libraries which made me able to watch DVD movies and by installing libdvdcss and some other system packages solved it for me.

For Ubuntu you should concentrate on [Medibuntu]("http://medibuntu.org/repository.php"), that's where the solution is, somewhere. As I'm more used to Debian, I simply drag down source tar balls and go from there, but that isn't exactly necessary nowadays.

---

### Post by bnilsson on 2012-01-06
[SOLVED)

Found a solution.
I installed **halevt**, which is catching the hardware event then a dvd is mounted/inserted.
The installation script for it is currently broken, however, a workaround is found at [http://ubuntuforums.org/showthread.php?t=1770231](http://ubuntuforums.org/showthread.php?t=1770231)
A config file (dvd-speed.xml) for what I wanted to do is found at [http://forum.xbmc.org/showthread.php?t=62923](http://forum.xbmc.org/showthread.php?t=62923), to be placed in /etc/halevt directory. This file gives the command "hdparm -E4 /dev/dvd" when the dvd insertion event is detected.
Finally, to make it work I had to change the default user for the halevt daemon, since it got "permission denied" for the hdparm command. Changing the user to myself in /etc/default/halevt fixed this.

Now the DVD drive speeds up for a few seconds when inserted, then spins down to a barely audible level and the speed is still enough to play the movie.

---

### Post by bnilsson on 2012-01-06
A final comment:
Setting the username for the daemon as myself did not work when logged in as someone else; still permission denied to modify the /dev/dvd speed.
Setting the username to root worked.

/etc/default/halevt:
> # Default settings for halevt initscript

# Set this to yes if you want the halevt init-script to start a system-wide daemon
START_DAEMON=yes

# Run halevt has user/group
HALEVT_USER=root
HALEVT_GROUP=plugdev


---

### Post by bnilsson on 2012-01-07
Decided to try a much simpler solution:
Create the file /etc/udev/rules.d/dvd-speed.rules:
DEVNAME=="dvd", ACTION=="change", RUN+="/sbin/hdparm -E4 /dev/sr0"
or, which is more clear for the reader
DEVNAME=="dvd", ACTION=="change", RUN+="/usr/bin/eject -x 8 /dev/dvd"

I selected the latter and removed **halevt.**
You probably need to do "sudo stop udev" and "sudo start udev" to activate.

I prefer "eject" before "hdparm" as the docs on how to control the speed is better. 

See "man udev", and you may also try
#  udevadm monitor --env
while changing media in the dvd drive to get more details on the udev events.

---

