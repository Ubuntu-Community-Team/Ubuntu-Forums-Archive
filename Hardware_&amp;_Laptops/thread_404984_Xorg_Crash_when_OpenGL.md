---
title: "Xorg Crash when OpenGL"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by nilsvdburg on 2007-04-09
I am using Ubuntu Edgy with 2.6.17-11-generic kernel and the official nvidia drives on a laptop (with an geforce go 7300 video card).

Since the last 3 days i have a problem with the x windows, every time i start anything that have to do with OpenGL the X crash and restart.

It happens when loading beryl-manager (even without being in an xgl session), when loading google earth, and even when typing "glxinfo" into the console.

I didn't change anything, on windows i can use google earth so i don't think that is is an hardware problem, it has to do something with the driver i think, but cant figure out what exactly.

If someone has any idea...


thanks.
nils

---

### Post by morepowerr on 2007-04-09
I have been running in to the same thing here on my desk top. Also using official nvidia drives. It has only been scents the last update so. All i can think is maybe something that just changed. Wish i know where to find what has been up dated in last few days may give use some clue.

---

### Post by nilsvdburg on 2007-04-09
Yeah, i hope it too, it's quite annoying that i can't use Google Earth or any OpenGL apps...

If there were any way to find out which packages were those that were last updated i may could put it back to its old version. I think it was an update that came de 6 of April of 2007.

Do anyone knows if there is a log for the update manager?

---

### Post by r00tuk on 2007-04-09
Ah finally found some users who are having the same problems as me since the update!

Any fixes yet?

---

### Post by wdaniels on 2007-04-10
I have exactly the same problem/setup/timeframe here - trouble is my screensaver uses OpenGL and keeps crashing my X session every time I leave the room for a moment :D  Opening the screensaver settings has the same effect (presumably the preview function) so can anyone tell me how to disable the screensaver manually until there is a fix?

---

### Post by wdaniels on 2007-04-10
nm, looks like "sudo killall gnome-screensaver" will do the job, has nobody found a fix for this yet?

---

### Post by wdaniels on 2007-04-10
I can't find any kind of log for synaptic/apt but dpkg has a log in /var/log/dpkg.log
"cat /var/log/dpkg.log | grep upgrade" gives me:

2007-04-03 07:40:31 upgrade libgphoto2-port0 2.3.0-0ubuntu3~edgy2 2.3.0-0ubuntu4~edgy1
2007-04-03 07:40:36 upgrade libgphoto2-2 2.3.0-0ubuntu3~edgy2 2.3.0-0ubuntu4~edgy1
2007-04-04 07:38:27 upgrade libkrb53 1.4.3-9ubuntu1.1 1.4.3-9ubuntu1.2
2007-04-04 07:38:28 upgrade libxfont1 1:1.2.0-0ubuntu3 1:1.2.0-0ubuntu3.1
2007-04-04 07:38:28 upgrade xserver-xorg-core 1:1.1.1-0ubuntu12.1 1:1.1.1-0ubuntu12.2
2007-04-05 07:42:54 upgrade mysql-common 5.0.24a-9ubuntu1 5.0.24a-9ubuntu2
2007-04-05 07:42:55 upgrade libmysqlclient15off 5.0.24a-9ubuntu1 5.0.24a-9ubuntu2
2007-04-05 07:42:57 upgrade libswt3.2-gtk-java 3.2.1-0ubuntu2 3.2.1-0ubuntu3
2007-04-05 07:42:58 upgrade libswt3.2-gtk-jni 3.2.1-0ubuntu2 3.2.1-0ubuntu3
2007-04-05 07:42:59 upgrade mysql-client-5.0 5.0.24a-9ubuntu1 5.0.24a-9ubuntu2
2007-04-05 07:43:05 upgrade mysql-server-5.0 5.0.24a-9ubuntu1 5.0.24a-9ubuntu2
2007-04-05 21:04:57 upgrade kdelibs-data 4:3.5.5-0ubuntu3.2 4:3.5.5-0ubuntu3.3
2007-04-05 21:05:15 upgrade kdelibs4c2a 4:3.5.5-0ubuntu3.2 4:3.5.5-0ubuntu3.3
2007-04-05 21:05:22 upgrade kdebase-bin 4:3.5.5-0ubuntu3.3 4:3.5.5-0ubuntu3.4
2007-04-07 17:25:22 upgrade gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1 0.10.3+cvs20060918-1
2007-04-07 20:10:45 upgrade libfaad2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
2007-04-07 20:11:15 upgrade libfaad2-dev 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3

I'm guessing "2007-04-04 07:38:28 upgrade xserver-xorg-core 1:1.1.1-0ubuntu12.1 1:1.1.1-0ubuntu12.2" is responsible, but have to wait for a large download to finish before I try putting the version back...

---

### Post by Cesa on 2007-04-10
I had the exact same problem, until I found [this post]("http://ubuntuforums.org/showpost.php?p=2413073&postcount=2")

It worked fine for me!

---

### Post by wdaniels on 2007-04-10
Worked for me too, thank you! :)

---

### Post by thecarpy on 2007-04-12
I have the same issue, but I can start beryl ... xorg in that case uses close to 80% CPU ... and not the 7% I was used to ;-).

I cannot open glxinfo it crashes X and I have an ati gpu with the official crappy ati drivers ... so not quite the same setup here and not quite the same issues, but it worked yesterday, before an update of xserver-xorg .... will reinstall the ati drivers and let you know ...

---

