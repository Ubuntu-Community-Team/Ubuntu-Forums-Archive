---
title: "[SOLVED] How to see hardware config??"
date: 2008-11-17
forum: Hardware
---

### Post by Jacob Collstrup on 2008-11-17
Heya,

I tried to search for 'hardware specifications' and 'hardware configuration' for this one, but there seems to be a lot of irrelevant clutter in my search, so I couldn't sort out the good results from the bad. So I hope its ok I start a new thread...

I would like to know my hardware spefications. I tried the 'lshw' console command. But its WAY too technical for me. I look for the 'Hardware info' in 'System'-->'Preferences'-->'Hardware info' but that option isn't there.

I'm using Ubuntu 8.04 Hardy Heron...

Jacob

---

### Post by Malta paul on 2008-11-17
You can try 'SysInfo' you can find it in Add/remove. Its rather good :)

---

### Post by starcannon on 2008-11-17
If you would like a command line approach:
```
sudo lshw
```
If you would like a command line approach that spits out a nice html file:
```
sudo lshw -html > hardwarelist.html
```
That should leave a file named hardwarelist.html in the /user/your_username folder; open with Firefox for a nicely formatted hardware list.

GL and keep it fun

---

### Post by Jacob Collstrup on 2008-11-17
I like that Sysinfo, thanks!!

Though it says that my CPU is running at 600mhz...:confused:

Its supposed to be a 1.5Ghz cpu...is it because it can step the cpu speed?

Jacob

---

### Post by starcannon on 2008-11-17
Yeah, you need to:
```

sudo dpkg-reconfigure gnome-applets

```choose to allow it to have admin or was it root, anyway god like power over the cpu frequency scaling applet.

Now then right click on the gnome panel of your choice, top or bottom, click "add to panel" then choose "CPU Frequency Scaling Monitor", it *should* allow you mouse click access to a gui that lets you set your cpu frequencies; if it does not, then you will need to come back with the cpu brand/model/era cpu that your using, and we'll get the correct kernel module loaded so you can control that bad boy.

GL and keep it fun

P.S. heres a link to help you along:
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by Jacob Collstrup on 2008-11-17
Neat trick...it even tells me the current CPU speed...nice...

Jacob

---

