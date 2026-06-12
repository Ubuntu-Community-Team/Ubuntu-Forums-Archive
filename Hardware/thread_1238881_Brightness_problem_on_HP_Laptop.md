---
title: "Brightness problem on HP Laptop"
date: 2009-08-12
forum: Hardware
---

### Post by coloel22 on 2009-08-12
Hi All,

I bought a new HP dv3500 and I installed ubuntu 9.04. All seems to work correctly but I cannot decrease the brightness....

The problem is that I can use the function keys to decrease/increase the brightness and when I used it my desktop showed the notification of brightness change. However, the brightness is always at 100%.

In addition, I checked /proc/acpi/video/VGA/LCD/brightness file and it changes when I used the function keys. However the brightness of my screen never decrease.

Please, help me! I'm getting blind!

additional information: My laptop has LED Backlight (?) Maybe, that is a problem for the controller. 

Thanks in advance
(sorry for my english, I am trying to improve it)

---

### Post by AppleBonker on 2009-10-06
Did you figure this out?  I know it's been a while since this post.  I've figured out a work-around based on postings for Sony laptops on here.  However, I'm running it on 9.10.  It should work the same in 9.04, but I can't guarantee it.  If you're still following this thread, let me know and I'll walk you through what I did.  It's based on this [thread]("http://ubuntuforums.org/showthread.php?t=1004568&highlight=sony+brightness+working").  I cannot take credit.  There were some differences, so let me know and I'll point them out.  I think this issue is from the graphics card, not the LED backlight.

---

### Post by coloel22 on 2009-10-06
Hi,

Unfortunately, I'm still having the same issue. The only way that I can decrease the brightness is going to System-Administration-NVIDIA X Server Settings.

I'll try to figure out the problem again using the thread that you posted.

Thanks for your response, i'll be posting as soon as posible my results.

---

### Post by AppleBonker on 2009-10-06
coloel22,

Apparently you're still checking this thread.  Here's what I did (based on the thread I posted):

First, install nvclock.  You should be able to get that from Synaptic.

Check that is works:

```
$nvclock -S -10 #should decrease brightness
$nvclock -S +10 #should increase brightness
```

If that works, you'll need to edit a couple of files in the /etc/acpi/events folder, so open a terminal and get in there.  On my laptop, the two files were called asus-brightness-down and asus-brightness-up.  Here's what my files ended up looking like:

asus-brightness-down
```
event=**[COLOR=Red]video LCD 00000087 00000000[/COLOR]**
action=**[COLOR=SeaGreen]/usr/bin/nvclock[/COLOR]**[COLOR=SeaGreen][COLOR=Black] -S -8[/COLOR][/COLOR]
```

asus-brightness-down
```
event=**[COLOR=Red]video LCD 00000086 00000000[/COLOR]**
action=**[COLOR=SeaGreen]/usr/bin/nvclock[/COLOR]**[COLOR=SeaGreen][COLOR=Black] -S +8[/COLOR][/COLOR]
```

To verify the text in red, run the following:

```
$apci_listen -c 2
```

And press the Fn+brightness down key followed by the Fn+brightness up key.  If they match my event codes, then the red section will work for you.  If not, replace the red with what your machine returns.

The green section of the code refers to where nvclock is installed.  For me, it was in /usr/bin.  I think it sometimes is installed in /usr/local/bin, so check your computer to see where the nvclock file is located and use that there.

Now, you need to restart acpid:

```
sudo /etc/init.d/acpid restart
```

Try the function keys now and they should work to increase/reduce brightness.  Let me know if this works.  Good luck!

---

### Post by AppleBonker on 2009-10-06
If that works, I also created two new files in the events folder called asus-brightness-batt and asus-brightness-ac.  Those appear as follows:

asus-brightness-batt (dims screen when AC is removed)
```
event=**[COLOR=Red]ac_adapter AC 00000080 00000000[/COLOR]**
action=/usr/bin/nvclock -S 40
```The section in red can be found running acpi-listen -c 5 and unplugging the AC adapter.  It should probably be similar (if not the same as mine).  Again, the action is dependent on your install location of nvclock.  I have it set to 40 so my screen dims to 40% on battery.  You may want to go brighter/dimmer based on your preferences.

Next, when you plug the AC back in:

asus-brightness-ac
```
event=**[COLOR=Red]ac_adapter AC 00000080 00000001[/COLOR]**
action=/usr/bin/nvclock -S 80
```Again, check with acpi_listen to make sure this event is correct.  I also set the brightness to 80 since 100% burns my eyes.  Don't forget to restart acpid before testing these two as well.

I've noticed this doesn't coincide correctly with the on-screen brightness meter when adjusting, but that is a small price to pay at this point.  I'll have to see if there is a way to fix that later.  At least for now, this makes the laptop usable in my opinion.  Let me know if you have any problems.

Edit:  Almost forgot, you may have to chmod to make those files executable.  I didn't have to, but your results may be different.  Also, let me know if your filenames are the same as mine.  I've got a DV-3510nr and I'm just wondering out of curiosity.  Thanks!

Edit2: You can actually chance the nvclock -s +/-8 to +/-10 and it will coincide correctly with the on-screen display mostly.  The display will get down to dim settings 10 and 0, but nvclock hits bottom at 15, so it isn't perfect, but close.

---

### Post by coloel22 on 2009-10-06
It works!!!

Thanks for your help!

The files that I had to edit on my laptop where video_brightnessdown and video_brightnessup

Thanks for your fully explanation and for response me. I thinked that I will never fix that fn keys :) !!

Please, don't hesitate to contact me for any other problems/issues related to this model of laptop.

BR,
//Jonatan

---

### Post by coloel22 on 2009-10-06
The other thing that not works on my laptop is the remote control. Does yours work?

I read that it should work out of the box on all hp laptops. Unfortunately, my laptop is the exception.:confused:

In windows the remote control works perfectly.

---

### Post by AppleBonker on 2009-10-06
Glad the screen brightness trick worked for you.  I've only been running Ubuntu (on that laptop, my desktop and a netbook) for a couple of months and that was bugging me on the laptop.  I was very pleased when I got it working.

As far as the remote goes, you'll need to install lirc.  I tried messing with it for a little while.  I'm running a mythbuntu box as well and wanted to use the laptop as a frontend.  I couldn't get the remote to function yet, but I honestly didn't play with it that much.  Right now, I'm trying to work out some of the bugs on 9.10 Karmic with the HP laptop, so I haven't gotten around to fixing the remote.  I'm sure I'll play with it more in the near futuer, and if I find anything out I'll definitely let you know.

---

### Post by albertoguevara on 2010-01-20
Thanks AppleBonker, this worked with my dv3500 notebook too. Hey I was wondering if there's a chance that this display dim thing could be controlled by the power management tools that comes with kde/gnome... cause i tried to set the dim percentage for each energy profile with no success.

Thanks again!
Alberto.

---

### Post by JakcV on 2010-01-23
I have the similar problem, that my brightness can't change using the shotcut key of laptop but i am not using nvidia graphic card, I am using intel X3100 chipset from my laptop. 

I am using ubuntu 9.10 64 bit currently. I was able to change brightness with the shot cut key at ubuntu 8.10 64 bit.

p/s: I am able to change brightness using the brightness applet.

---

### Post by racitup on 2010-11-02
Thanks AppleBonker, ever since changing to Ubuntu 10.04 64-bit my eyes have been assaulted by the LCD brightness on 100% permanently!
I have a HP Pavilion DV3505ea

Before that (9.10 I think) I also had to fix the problem using nvclock in a boot script and some scripts and buttons I created and pinned to the panel. This is a bit more user friendly, but still a hack!

I assume this problem exists because HP has wired the LCD brightness control to the nvidia chipset rather than the ACPI BIOS!? So isn't really an Ubuntu problem, more an HP proprietary way of dealing with LCD brightness problem!?

Anyway, another workaround for this (don't have time right now) might be to write a script to:

[LIST]
[*]Read the output of /proc/acpi/video/VGA/LCD/brightness (which is gnome-controlled)
[*]Use the output in a call to "/usr/bin/nvclock -S"
[/LIST]
Then use this script in the events (/etc/acpi/events/):

[LIST]
[*]battery: ac_adapter AC 00000080 00000000
[*]ac: ac_adapter AC 00000080 00000001
[*]asus-brightness-down: video LCD 00000087 00000000
[*]asus-brightness-up: video LCD 00000086 00000000
[/LIST]
NOTE: the power event files are slightly different on my machine.

Thanks again!
Richard

> **AppleBonker said:**
> If that works, I also created two new files in the events folder called asus-brightness-batt and asus-brightness-ac.  Those appear as follows:

asus-brightness-batt (dims screen when AC is removed)
```
event=**[COLOR=Red]ac_adapter AC 00000080 00000000[/COLOR]**
action=/usr/bin/nvclock -S 40
```The section in red can be found running acpi-listen -c 5 and unplugging the AC adapter.  It should probably be similar (if not the same as mine).  Again, the action is dependent on your install location of nvclock.  I have it set to 40 so my screen dims to 40% on battery.  You may want to go brighter/dimmer based on your preferences.

Next, when you plug the AC back in:

asus-brightness-ac
```
event=**[COLOR=Red]ac_adapter AC 00000080 00000001[/COLOR]**
action=/usr/bin/nvclock -S 80
```Again, check with acpi_listen to make sure this event is correct.  I also set the brightness to 80 since 100% burns my eyes.  Don't forget to restart acpid before testing these two as well.

I've noticed this doesn't coincide correctly with the on-screen brightness meter when adjusting, but that is a small price to pay at this point.  I'll have to see if there is a way to fix that later.  At least for now, this makes the laptop usable in my opinion.  Let me know if you have any problems.

Edit:  Almost forgot, you may have to chmod to make those files executable.  I didn't have to, but your results may be different.  Also, let me know if your filenames are the same as mine.  I've got a DV-3510nr and I'm just wondering out of curiosity.  Thanks!

Edit2: You can actually chance the nvclock -s +/-8 to +/-10 and it will coincide correctly with the on-screen display mostly.  The display will get down to dim settings 10 and 0, but nvclock hits bottom at 15, so it isn't perfect, but close.

---

