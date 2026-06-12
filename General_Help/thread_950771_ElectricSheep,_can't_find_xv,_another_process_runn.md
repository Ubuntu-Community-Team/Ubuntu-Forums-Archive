---
title: "ElectricSheep, can't find xv, another process running, terminated"
date: 2008-10-17
forum: General Help
---

### Post by Sugi on 2008-10-17
I am having issues with Electricsheep for Ubuntu Hardy Heron.  I know some, if not all of these issues have been bugging people sinces the days of Dapper, but google searches are not really helping me.

I installed electricsheep through apt-get. No problem.  I selected electricsheep from Gnome-Screansavers. No problem. Electricsheep will start up, run and download sheeps. No problem, but when it's running it will only workings in the top left corner.  I don't know how to fix these, but I have tried the following:

electricsheep --zoom 1 --mplayer 1
```
detected another electricsheep process.
using read only access, ie disabling downloading of sheep.
Terminated
```

electricsheep --zoom 1 --root 1
```
detected another electricsheep process.
using read only access, ie disabling downloading of sheep.
Cannot find xv port
```

But if I do a restart:

electricsheep --zoom 1 --root 1
```
Cannot find xv port
```

electricsheep --zoom 1 --mplayer 1
```
Terminated
```

The odd thing is, ps -e shows electricsheeps running, but nothing is showing up on my desktop or in any shape or form.

mplayer -vo xv -fs ~/.sheep/*.mpg
(i did a lot of terminal output for this command. some of the main stuff)
```
[VO_XV] It seems there is no Xvideo support for your video card available.
```
```
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
```
(I don't really want to use Xscreensavers, I rather just use the default.)

Any ideas?
Sugi

---

### Post by Sugi on 2008-10-19
bump

---

### Post by Sugi on 2008-10-20
Bump

---

### Post by Sugi on 2008-10-24
Bu<p

---

### Post by Sugi on 2008-10-29
bump

---

### Post by DarkDead on 2008-11-02
Hi. The best solution is to remove your current version of electricsheep:
```
sudo apt-get remove electricsheep
```
And then you can use [_**this script**_]("http://electricsheep.org/install-electricsheep-package.sh") and run
```
sudo sh install-electricsheep-package.sh
```
This will install a new version of electric sheep from a PPA on lauchpad. 

Credits to spotspot:
[U][http://ubuntuforums.org/showthread.php?t=826554]("http://ubuntuforums.org/showthread.php?t=826554")
[http://community.electricsheep.org/node/271]("http://community.electricsheep.org/node/271")[/U]

---

### Post by Sugi on 2008-11-06
THANK YOU so much.  I will test it tonight.  Thanks again for the script.

Sugi

---

### Post by nuroxs on 2008-11-07
DarkDead, thank you.

Finally someone helps ! =o)

Nice to see other Portuguese ubunters!

Obrigado!

---

### Post by Sugi on 2008-11-10
Well, I remove electricsheep through apt-get and installed it again through the install script.  I head over to Screensaver in Preferences and Screensaver shows the option for electricsheep, but there is no preview.  But I did add the old sheeps that I downloaded before to current ~/.sheep directory.

Any idea on how to fix this?
Sugi

---

### Post by nuroxs on 2008-11-10
> **Sugi said:**
> Well, I remove electricsheep through apt-get and installed it again through the install script.  I head over to Screensaver in Preferences and Screensaver shows the option for electricsheep, but there is no preview.  But I did add the old sheeps that I downloaded before to current ~/.sheep directory.

Any idea on how to fix this?
Sugi

I have the same issue.

---

### Post by nuroxs on 2008-11-20
This is still a problem for me...! ~.~

---

### Post by mrmooge88 on 2008-12-13
I have the problem here too. I have some sheep in /home/user/.sheep I tried playing with some of the preferences with no results.

---

### Post by Sugi on 2008-12-15
BUMP

Still having issues here as well :-/

Sugi

---

### Post by markg1123 on 2008-12-29
Bump -- does anyone have a fix for this?

---

### Post by laluz on 2009-04-30
Hi, 

I have done exactly as proposed with the install shell script. Then went to the Screensaver setup and removed the "--zoom 1" option. Also I have set up the GL as the video-driver (may vary for you)

Now everything works again. Kubuntu Intrepid, KDE.

---

### Post by kd0afk on 2009-06-24
> **DarkDead said:**
> Hi. The best solution is to remove your current version of electricsheep:
```
sudo apt-get remove electricsheep
```And then you can use [_**this script**_]("http://electricsheep.org/install-electricsheep-package.sh") and run
```
sudo sh install-electricsheep-package.sh
```This will install a new version of electric sheep from a PPA on lauchpad. 

Credits to spotspot:
[U][http://ubuntuforums.org/showthread.php?t=826554](http://ubuntuforums.org/showthread.php?t=826554)
[http://community.electricsheep.org/node/271](http://community.electricsheep.org/node/271)[/U]

Did it. Here is the return:

shawn@HAL:~$ electricsheep
Terminated
shawn@HAL:~$

I had a thought, does electric sheep require compiz to run? Just grabbing for straws here.

---

### Post by starcannon on 2009-06-24
Please post the output of:
```

glxinfo | grep direct

```

---

### Post by kd0afk on 2009-06-24
> **mrmooge88 said:**
> I have the problem here too. I have some sheep in /home/user/.sheep I tried playing with some of the preferences with no results.
How in the hell did you get a .sheep file?

---

### Post by starcannon on 2009-06-24
> **kd0afk said:**
> How in the hell did you get a .sheep file?
mrmooge88 made that post in Dec of 08; so chances are your not going to get a response from him.

Generally its best to continue in the thread you started, I followed you here just to continue helping.

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> mrmooge88 made that post in Dec of 08; so chances are your not going to get a response from him.

Generally its best to continue in the thread you started, I followed you here just to continue helping.

Going for anything I can get.

---

### Post by birddog165 on 2009-09-07
thank you so much, you rock DarkDead

---

