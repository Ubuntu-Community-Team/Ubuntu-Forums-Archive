---
title: "Applet for monitoring laptop CPU temperature"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by infinito on 2005-08-29
I've written a little applet to monitor laptop CPU temperature.
You only need to have installed Gnome and support for ACPI thermal_zone, which every laptop should have.

If you're interested, take a look at: [http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)

---

### Post by c0rderr0y on 2005-08-29
will this work with kde?

---

### Post by infinito on 2005-08-29
[QUOTE=c0rderr0y]will this work with kde?[/QUOTE]
 I'm sorry, but this is a GNOME applet, so it won't work on KDE.
I have another version based on notification area, which should work ok on KDE, but i haven't released it yet. Soon it'll be available, so stay tuned.

---

### Post by gmc on 2005-08-30
[QUOTE=infinito]I've written a little applet to monitor laptop CPU temperature.
You only need to have installed Gnome and support for ACPI thermal_zone, which every laptop should have.

If you're interested, take a look at: [http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)[/QUOTE]

I just tried your applet. Unfortunately, it doesn't want to run at all here. When I tried to add it to the panel, it borked and asked me if I wanted to delete the applet from the panel. 

G.

---

### Post by JLB on 2005-08-30
works great on breezy! i appreciate your work. thanks!

---

### Post by infinito on 2005-08-30
[QUOTE=gmc]I just tried your applet. Unfortunately, it doesn't want to run at all here. When I tried to add it to the panel, it borked and asked me if I wanted to delete the applet from the panel. 

G.[/QUOTE]
 Umm, ok, let's try to debug what's happen... Please do this:

(1) Download latest .deb from: [http://infinito.f2o.org/laptoptemp/laptoptemp_0.2-2_i386.deb](http://infinito.f2o.org/laptoptemp/laptoptemp_0.2-2_i386.deb)
(2) Open a terminal an run this commands:
```
$ sudo apt-get remove --purge laptoptemp
$ sudo apt-get install python-gnome2 python-gnome2-extras
$ sudo dpkg -i laptoptemp_0.2-2_i386.deb (or wherever the .deb is)
$ /usr/lib/gnome-applets/laptoptemp
```
(3) Don't close the terminal and then add Laptoptemp to panel, you'll see what happens on terminal. Then paste the output here, so i can see what's going on...

Thanks!

---

### Post by gmc on 2005-08-30
Hi,

I followed your instructions (Note, I didn't have python-gnome-extras installed). Here's what I got:

---(cut here)---
gord@ikenai-ookami:~ $ cd /proc/acpi/thermal_zone/THRM/
gord@ikenai-ookami:/proc/acpi/thermal_zone/THRM $ ls -l
total 0
-rw-r--r--  1 root root 0 2005-08-30 13:18 cooling_mode
-rw-r--r--  1 root root 0 2005-08-30 13:18 polling_frequency
-r--r--r--  1 root root 0 2005-08-30 13:18 state
-r--r--r--  1 root root 0 2005-08-30 13:18 temperature
-rw-r--r--  1 root root 0 2005-08-30 13:18 trip_points
gord@ikenai-ookami:/proc/acpi/thermal_zone/THRM $ cd /home/gord/
gord@ikenai-ookami:~ $ /usr/lib/gnome-applets/laptoptemp

(No text output from running laptoptemp from CLI, after waiting for about a minute, I'm returned to the command prompt.)

If I try adding laptoptemp to a panel, I get a window telling that ACPI is not enabled. Sorry for the ass backwardness of this message... I had cut/pasted all appropriate output to a message but the browser crashed before I could post it.

G.

Additional note: I just ran it a second time and it appears on the panel, but no temprature is displayed.

---

### Post by infinito on 2005-08-30
[QUOTE=gmc]Hi,

I followed your instructions (Note, I didn't have python-gnome-extras installed). Here's what I got:

---(cut here)---
gord@ikenai-ookami:~ $ cd /proc/acpi/thermal_zone/THRM/
gord@ikenai-ookami:/proc/acpi/thermal_zone/THRM $ ls -l
total 0
-rw-r--r--  1 root root 0 2005-08-30 13:18 cooling_mode
-rw-r--r--  1 root root 0 2005-08-30 13:18 polling_frequency
-r--r--r--  1 root root 0 2005-08-30 13:18 state
-r--r--r--  1 root root 0 2005-08-30 13:18 temperature
-rw-r--r--  1 root root 0 2005-08-30 13:18 trip_points
gord@ikenai-ookami:/proc/acpi/thermal_zone/THRM $ cd /home/gord/
gord@ikenai-ookami:~ $ /usr/lib/gnome-applets/laptoptemp

(No text output from running laptoptemp from CLI, after waiting for about a minute, I'm returned to the command prompt.)

If I try adding laptoptemp to a panel, I get a window telling that ACPI is not enabled. Sorry for the ass backwardness of this message... I had cut/pasted all appropriate output to a message but the browser crashed before I could post it.

G.

Additional note: I just ran it a second time and it appears on the panel, but no temprature is displayed.[/QUOTE]
 Sorry! It's my fault! I didn't know about thermal_zone/THRM (i didn't read acpi documentation, i'm an asshole!)

I'm gonna fix it tonight. Thanks for the report!

---

### Post by gmc on 2005-08-30
Hi (again),

Actually while I've got you, is there any change of looking at the graphics background. If you play with the panel's transparency options the background on laptoptemp continues to display as white or gray. See attached image,


Thanks for the quick responce and help, very much appreciated.

G.

---

### Post by bearbigears on 2005-08-30
infinito, i downloaded the deb. pkg to my desktop. when i go to install it tells me no such file or directory exists. i read somewhere here that you could change the directory of the terminal with cd ./~ is this the command. i have tried this one but no success. any help would be gladly appreciated.

---

### Post by infinito on 2005-08-30
[QUOTE=bearbigears]infinito, i downloaded the deb. pkg to my desktop. when i go to install it tells me no such file or directory exists. i read somewhere here that you could change the directory of the terminal with cd ./~ is this the command. i have tried this one but no success. any help would be gladly appreciated.[/QUOTE]
 Suppossing that you downloaded the .deb to your Desktop, you should try:
```

$ sudo dpkg -i ~/Desktop/laptoptemp_0.2-2_i386.deb

```

---

### Post by infinito on 2005-08-30
[QUOTE=gmc]Hi (again),

Actually while I've got you, is there any change of looking at the graphics background. If you play with the panel's transparency options the background on laptoptemp continues to display as white or gray. See attached image,


Thanks for the quick responce and help, very much appreciated.

G.[/QUOTE]
 I think this is a limitation of PyGtk (python for gtk) or gnome-python, not sure which. I will ask on mailing lists...

---

### Post by bearbigears on 2005-08-30
thank you so much, works like a charm.

---

### Post by infinito on 2005-08-30
[QUOTE=gmc]Hi (again),

Actually while I've got you, is there any change of looking at the graphics background. If you play with the panel's transparency options the background on laptoptemp continues to display as white or gray. See attached image,


Thanks for the quick responce and help, very much appreciated.

G.[/QUOTE]
 I've uploaded version 0.3. It should fix the transparent panel issue, and your problem with thermal_zone not recognized.

[http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)

---

### Post by gmc on 2005-08-30
Hi,

Just installed version 0.3 and BINGO! it's working like a charm. Thanks so much for the time and trouble. Good Job!

G.

---

### Post by gmc on 2005-08-31
[QUOTE=infinito]I've uploaded version 0.3. It should fix the transparent panel issue, and your problem with thermal_zone not recognized.

[http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)[/QUOTE]

Hi Infinito,

    I've included a snapshot of a minor cosmetic problem. If you download and zoom in on the snapshot, you'll see a white line across the top of laptoptemp on the panel. Looks like there's a problem with the graphics image size or the size thinks the image size is. The second thing is a possible feature addition. Since the fan can be monitored at /proc/acpi/fan/FAN, I thought it might be nice if the graphic image with the thermometer changed colour say from red to green when the fan is active.

Just a thought, other than that... great job, well done.

G.

---

### Post by infinito on 2005-08-31
Ummm. that f***in white line! I tried yesterday to get rid of it for a loong time without succes. I'm gonna try tonight again. I'm missing something, and i don't know what...

About the fan thing, it's on my TODO list. Probably i'll add support for changing icon depending on temp and fan, or maybe add a fan icon, not sure how i will do it.

Check for updates soon!

---

### Post by gmc on 2005-08-31
:-) Will do, in the meantime, I'll download the tarball and take a look at the source and see if I can see where the line is comming from. 

G.

---

### Post by gmc on 2005-08-31
[QUOTE=infinito]Ummm. that white line! I tried yesterday to get rid of it for a long time without succes. I'm gonna try tonight again. I'm missing something, and i don't know what...[/QUOTE]

I think I've got it. The laptoptemp_small.png is 24x24, however the panel (at least in my situation) is 25 pixels tall. Now I know that the panel hight can be adjusted, but it's minimum size is based on the theme/icons your using. I think (I'll try it) by making the small image to 25x25, the line should disappear.

G.

Ok! Did resize the image in question to 25x25, however it didn't help. I'll keep looking...

G2.

---

### Post by vtec on 2005-08-31
Great Applet!!! Works great on my system. If possible in the future it would be nice to have an option for Fahrenheit, and have an option to display just the text or icon.

---

### Post by ssck on 2005-09-01
works great.

thanks

---

### Post by John.Michael.Kane on 2005-09-05
program not working with acer travelmate 290 cl51. installed aplet says no ACPI thermal_zone to monitor.. now i know said laptop is acpi inabled and the software for it was installed. if you can please explain how to get your app working? thanks..

---

### Post by infinito on 2005-09-05
[QUOTE=SD-Plissken]program not working with acer travelmate 290 cl51. installed aplet says no ACPI thermal_zone to monitor.. now i know said laptop is acpi inabled and the software for it was installed. if you can please explain how to get your app working? thanks..[/QUOTE]
 You need to have both "processor" and "thermal" modules loaded.
If so, you will have something inside /proc/acpir/thermal_zone.
The applet reads the cpu temperature from that dir.

Please, try doing:
$ sudo modprobe processor
$ sudo modprobe thermal

And then:
$ ls -l /proc/acpi/thermal_zone

If it's empty, the applet will not work...

---

### Post by John.Michael.Kane on 2005-09-05
Comes back as total 0.. so what is needed to get it to work?

---

### Post by infinito on 2005-09-06
[QUOTE=SD-Plissken]Comes back as total 0.. so what is needed to get it to work?[/QUOTE]
 If you don't have acpi thermal_zone enabled, maybe you should try lm_sensors and another software, but this applet won't work fot you, sorry :(

---

### Post by spier on 2005-12-20
Works great, nice and really simple! Thanks.

---

### Post by infinito on 2006-01-11
I've just release version 0.4 with these changes:

* Changing icon depending on temperature.
* Three display modes: Graphic, Text or Graphic and Text.
* Support for Celsius and Fahrenheit.
* Added tooltip with temperatures.

Source code: [http://infinito.f2o.org/laptoptemp/laptoptemp-0.4.tar.gz](http://infinito.f2o.org/laptoptemp/laptoptemp-0.4.tar.gz)
Ubuntu .deb: [http://infinito.f2o.org/laptoptemp/laptoptemp_0.4-1_all.deb](http://infinito.f2o.org/laptoptemp/laptoptemp_0.4-1_all.deb)
More information: [http://infinito.f2o.org/laptoptemp/](http://infinito.f2o.org/laptoptemp/)

---

### Post by floflooo on 2006-01-12
I absolutely like the compact look of this version... and the dynamic icon.
Great job infinito! :p

---

### Post by zugvogel on 2006-01-14
I just installed it and it works well. Thank you for this.

---

### Post by lolcese on 2006-01-25
Great app, thank you

---

