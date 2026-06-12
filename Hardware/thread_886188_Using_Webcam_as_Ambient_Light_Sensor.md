---
title: "Using Webcam as Ambient Light Sensor"
date: 2008-08-10
forum: Hardware
---

### Post by ionman on 2008-08-10
Hi all. I have done some extensive searching and haven't been able to come up with anything to solve this quest yet.

I would like to be able to use my webcam as an ambient light sensor to automatically adjust my backlight brightness on my laptop. I have a Dell XPS M12010, with the Logitech webcam built in. I am running Ubuntu 8.04. My webcam is working and shows up at /dev/video0. I know gnome-power-manager can do this, and I have seen the gconf-editor settings for the ambient light sensor, but when I change these settings nothing happens.

If anybody has some helpful advice, or can point me somewhere else it would be most appreciated!

Thanks!

- ionman

---

### Post by ionman on 2008-08-13
Has anyone had any success doing this?

---

### Post by stratocastom on 2010-06-05
Have you had any luck trying to get this working?
I've been searching around recently, and there still doesn't seem to be a solution.
Only thing I can find is redshift, which changes the screen warmth according to global position.

---

### Post by dnyy on 2010-06-08
I found this: a formula to calculate the brightness. I not good in writing apps so I am not able to do anything with it, but maybe someone else is able to use it

[http://social.msdn.microsoft.com/Forums/en/roboticssimulation/thread/4e53a3c8-97c4-4560-9aae-bcc8609951d2](http://social.msdn.microsoft.com/Forums/en/roboticssimulation/thread/4e53a3c8-97c4-4560-9aae-bcc8609951d2)

---

### Post by blchinezu on 2010-08-13
It's funny how we all thought of this at the same period of time.
I've done something but it's in a serious alpha state and it's tested only with my asus x55sv laptop.
It uses quite a lot of things but it's fine with me for the moment as I already had most of them installed.

**Requires:**
+ webcam (obviously)
+ **streamer** (to grab webcam image)
+ **convert** (to resize the image so there will be less pixels to be analysed)
+ **php5-cli** and **php5-gd** (to analyse each pixel - I didn't know any other method of analysing the brightness)
+ changing the permissions of the brightness file (*sudo chmod 777 $file*) which in my case is: */sys/class/backlight/acpi_video0/brightness* but for you it might be other so you might have to modify it in the script (I wrote in the script where you have to replace the path)


**Archive description:**
+ **RUN.sh** (it's the main bash script which has to be run)
+ **ret-brightness.php** (it's runned by the bash script so you don't have anything to do with this)
+ **sleep-time** (it's the sleep time in seconds between 2 webcam grabs)


**How to kill the script:**
*Method 1*: If you run from a terminal just CTRL + C
*Method 2*: **rm /tmp/auto-brightness-*** (run this in terminal, it will remove a flag created by the script. It will still run the remaining sleep time but when the next webcam grab comes it exits)


In my opinion this is at least a start... I didn't find anything through the internet to do this so I'm quite happy with this.. even if it's a mess:D

---

### Post by blchinezu on 2010-08-13
I made it better than what i've attached in the upper post. But it's still a beta.
Anyway... The configuration is way more easier as I made a separate cfg.ini file. Easy to use and understand. (at least I hope so).

Link:[ http://gnome-look.org/content/show.php/Webcam+Adjust+Screen+Brightness?content=128780]("http://gnome-look.org/content/show.php/Webcam+Adjust+Screen+Brightness?content=128780")

Good Luck

---

### Post by vnkatesh on 2010-08-17
Tested. Works

How about making this as a minor-launchpad project?

And maybe, move from Shell/PHP to C++?

---

### Post by blchinezu on 2010-08-19
> **vnkatesh said:**
> Tested. Works

How about making this as a minor-launchpad project?

And maybe, move from Shell/PHP to C++?
That would be nice but I don't really know much about C. I only know some basic things in C so I don't think it will be me the one to turn it into a binary app

---

### Post by velko on 2012-05-17
the [http://gnome-look.org/content/show.php/Webcam+Adjust+Screen+Brightness?content=128780](http://gnome-look.org/content/show.php/Webcam+Adjust+Screen+Brightness?content=128780) link works

I may post mine refined version of the above script soon.

---

### Post by smilzoboboz on 2012-06-04
It's more or less a year I'm working on Calise (acronym for camera light sensor).
Check it out on [calise.sourceforge.net]("http://calise.sourceforge.net/"), it quite good and the "daemonized" version resource (CPU, MEM, power) usage are negligible.

Right now it's successfully used by some archlinux users like me but I've tested it also on ubuntu and put all needed instruction to run it on INSTALL and README files (for usage instruction, once installed you can read calise and calised man pages).

Hope this helps.

Nicolò

---

### Post by sghpunk on 2013-01-17
> **smilzoboboz said:**
> It's more or less a year I'm working on Calise (acronym for camera light sensor).
Check it out on [calise.sourceforge.net]("http://calise.sourceforge.net/"), it quite good and the "daemonized" version resource (CPU, MEM, power) usage are negligible.



Just tryied it on ubuntu 12.04, it's working! Thanks!

---

