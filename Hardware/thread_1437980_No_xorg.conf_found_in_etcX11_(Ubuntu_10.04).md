---
title: "No xorg.conf found in /etc/X11 (Ubuntu 10.04)"
date: 2010-03-24
forum: Hardware
---

### Post by AtliThor on 2010-03-24
Hey.

I'm trying to get a second monitor working on a Acer laptop running 10.04. It seems to work; the monitor is recognized and automatically configured (which is very nice, by the way!).

However, the monitor's refresh rates seem to be configured incorrectly. I thought "no problem, I'll just tweak the xorg.conf"... only to find that there is no such file. - I've used this monitor (A 19'' Acer LCD) before on this laptop, using an older version of Ubuntu (8.10 and 9.04), so it should be compatible.

Reading other threads here, I tried using a few versions of:
```
sudo dpkg-reconfigure xserver-xorg
```
But none of them really did anything, and no xorg.conf has shown up yet.

Any help would be appreciated.

A few spec highlights:
[list]
[*]Acer Aspire 5670
[*]ATI Radeon Mobility X1600 
"Mesa"/"radeon" driver. Auto intalled by Ubuntu.
[*]Acer AL1916 (The extra LCD)
Ubuntu identifies it as "Acer technologies 19''"
[/list]

Thanks,
- Atli

---

### Post by diesch on 2010-03-24
Current version of X.org don't use a xorg.conf by default but try to recognize everything automatically. If you create a xorg.conf it will be used.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) may be helpful, too

---

### Post by AtliThor on 2010-03-24
Thanks diesch. That link was a big help.

I've managed to use the xrandr command to modify the refresh rate, but I still can't seem to manage to sync the horizontal and vertical rates so the screen stops flickering.

Closest I've gotten so far is to use:
```
$ gtf 1280 1024 60
```
to generate a Modeline, and then apply that to the screen by doing:
```
$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
$ xrandr --addmode VGA-0 "1280x1024_60.00"
$ xrandr --output VGA-0 --mode "1280x1024_60.00"
```

The screen still flickers, but not as badly as it used to. It's more like a slow "wobble" right now :)
Still unusable, of course, but I'm getting closer (I think).

Thanks again.

---

### Post by tbobo05 on 2010-04-08
Seems I am having the same problem, I just upgraded from 9.10 to 10.04 Beta 2.  

Using a atix1250 and an external Samsung SyncMaster2333.  

Have you made any leadway?  

I will start playing with the xrandr commands this weekend to see if I can come up with a acceptable fix.

---

### Post by |2eason on 2010-04-09
> **AtliThor said:**
> 
The screen still flickers, but not as badly as it used to. It's more like a slow "wobble" right now :)
Still unusable, of course, but I'm getting closer (I think).

Thanks again.I have a similar config to you and I tried 59.5 for the refresh. Works fines, no flickering. Now I just need to figure out how to generate a new xorg.conf to get the settings to persist.

---

### Post by seamustry on 2010-05-07
how do i use "xrandr" to manually set my laptop's main resolution? i dont have any external monitors...

---

### Post by at0msk on 2010-06-08
Is it possible to edit the xorg.conf file? It says it's owned by root and I can't make any changes.

---

### Post by rainbowagent7 on 2010-06-08
Hi all. Just read this thread and figured I'd throw in what little knowledge I've gained so far. You can create an xorg.conf file by entering recovery mode (hold down shift at startup, or choose it from GRUB when it appears) and type: 
```
sudo Xorg -configure
```at the prompt.

To test it I've read you can use:
```
X -config /root/xorg.conf.new
```but I cant be sure if it works because I haven't tried it. However it is supposed to work if you get a grey grid screen with the  cursor. All I know is I now have an xorg.conf and Lucid does use it because it is in my /var/log/Xorg.0.log file,it just doesn't use it by default.This code says it is in the /root folder, but I found mine in my /home folder, you might check before you run it to be sure. I think you still have to be in recovery mode to do this code as well.

To move the file to its proper location where it is looked for by X type:
```
cd /root/xorg.conf.new /etc/X11/xorg.conf  
```just replace /root with whatever directory it happens to be in when it's created.

Also, if you need to back up your xorg.conf:
```
cp /etc/X11/xorg.conf etc/X11/xorg.conf.bak
```it will move you current configuration to a backup file in the same directory and allow you to piddlefartass with the new one.

Hope this helps someone!

Oh yeah, to edit the xorg.conf when it is owned by root:
```
gksudo gedit etc/X11/xorg.conf
```but you probably want to back it up before you mess with it.

Peace,out.:p

---

### Post by AtticusG3 on 2010-06-09
This is also relavant to me.

I'm currently rebuilding a Mame box. Currently it is running Windows XP with an ArcadeVGA AGP card. System works well but it's time to upgrade the hardware.

I've built a newer machine from scrap bits and pieces (Dual CPU P3's 256MB RAM and an ATI Rage 128) installed Xubuntu 10.04, sdlmame and Wah!Cade. Everything is running beautifully with a standard monitor and now it's time to switch it into the cabinet and hook up the 15KHz screen.

However I've had difficulty finding comprehensive information regarding setting Xorg up for this. I would like to keep this setup running as it's a very neat interface and looks great when running.

So far I have tried a few things form this tread and others like it. I am hoping someone has written a script to do this automagically and i've just failed to find it. I know the Lincade project has some scripting written for it and I'm about to troll them for info.

---

### Post by rainbowagent7 on 2010-06-10
I hear that. I wish I knew more about scripting, but all in good time. But I do know the above codes work to get an xorg.conf created and that Lucid does refer to it once it's created, but beyond that the settings of your machine is all on you. Good luck getting your system fine tuned.

---

### Post by AtliThor on 2010-06-13
Interestingly, I've discovered that when I put the same laptop I was talking about before into Suspend or Hibernation mode while having a paused video open in Totem, once I wake it up again the same problem that happens with the external LCD happens with the laptop's LCD.

It seems to gradually go out of sync. Sometimes takes it a few minutes to even become noticeable, but then it goes on to become completely unusable.

I'm starting to think this is a display driver issue, rather than some misconfiguration in the X server.

---

### Post by zeh on 2010-06-17
I really miss the old days when things in linux were not automatic. Somehow hard to get the right configuration but once done, no problems at all.
Automation is good when it works....

---

### Post by Roger Norton on 2010-09-29
Hi,

I'm looking to create a xorg.conf file, and have followed your suggestion (You can create an xorg.conf file by entering recovery mode (hold down shift at startup, or choose it from GRUB when it appears) and type: 
```
sudo Xorg -configure
```at the prompt.).

On testing with X -config /root/xorg.conf.new at the root prompt, the screen goes blank.  Is this what should happen?

Regards,

Roger
 
(specs: 
computer: Dell Inspiron 4150,
OS: ubuntu 10.04
video controller: ATI mobility RADEON 7500C)

> **rainbowagent7 said:**
> Hi all. Just read this thread and figured I'd throw in what little knowledge I've gained so far. You can create an xorg.conf file by entering recovery mode (hold down shift at startup, or choose it from GRUB when it appears) and type: 
```
sudo Xorg -configure
```at the prompt.

To test it I've read you can use:
```
X -config /root/xorg.conf.new
```but I cant be sure if it works because I haven't tried it. However it is supposed to work if you get a grey grid screen with the  cursor. All I know is I now have an xorg.conf and Lucid does use it because it is in my /var/log/Xorg.0.log file,it just doesn't use it by default.This code says it is in the /root folder, but I found mine in my /home folder, you might check before you run it to be sure. I think you still have to be in recovery mode to do this code as well.

To move the file to its proper location where it is looked for by X type:
```
cd /root/xorg.conf.new /etc/X11/xorg.conf  
```just replace /root with whatever directory it happens to be in when it's created.

Also, if you need to back up your xorg.conf:
```
cp /etc/X11/xorg.conf etc/X11/xorg.conf.bak
```it will move you current configuration to a backup file in the same directory and allow you to piddlefartass with the new one.

Hope this helps someone!

Oh yeah, to edit the xorg.conf when it is owned by root:
```
gksudo gedit etc/X11/xorg.conf
```but you probably want to back it up before you mess with it.

Peace,out.:p

---

### Post by Roger Norton on 2010-09-29
Please ignore my previous post.  I've just re-read rainbowagent7's of June the 8th ("However it is supposed to work if you get a grey grid screen with the cursor.").

Doh!

Roger

> **Roger Norton said:**
> Hi,

I'm looking to create a xorg.conf file, and have followed your suggestion (You can create an xorg.conf file by entering recovery mode (hold down shift at startup, or choose it from GRUB when it appears) and type: 
```
sudo Xorg -configure
```at the prompt.).

On testing with X -config /root/xorg.conf.new at the root prompt, the screen goes blank.  Is this what should happen?

Regards,

Roger
 
(specs: 
computer: Dell Inspiron 4150,
OS: ubuntu 10.04
video controller: ATI mobility RADEON 7500C)

---

### Post by baseballguy on 2010-10-26
This works you should place this as solved


> **AtliThor said:**
> Thanks diesch. That link was a big help.

I've managed to use the xrandr command to modify the refresh rate, but I still can't seem to manage to sync the horizontal and vertical rates so the screen stops flickering.

Closest I've gotten so far is to use:
```
$ gtf 1280 1024 60
```
to generate a Modeline, and then apply that to the screen by doing:
```
$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
$ xrandr --addmode VGA-0 "1280x1024_60.00"
$ xrandr --output VGA-0 --mode "1280x1024_60.00"
```

The screen still flickers, but not as badly as it used to. It's more like a slow "wobble" right now :)
Still unusable, of course, but I'm getting closer (I think).

Thanks again.

---

### Post by entodoays on 2011-01-24
Hi all,

I also need to create an xorg.conf file but only to set a couple of parameters and do not wish to mess with the rest. Can an xorg.conf file have only partial information, say for the touchpad only or would this block my computer?

I'm actually using Ubuntu 10.10.

Thanks,

---

### Post by paragua on 2011-02-04
Hi there...
I think I managed to solve this same issue.
I have a Toshiba Satellite A215 with ATI X1200 (RM690) Video Card, and had a lot of issues with this card. 
After trying to solve with the XrandR and gtf, and having some enhancements but not a true solution, I managed to solve all issues by changing (upgrading) to the kernel version 2.6.34-020634-generic.
I hope it works for you too.

 


> **AtliThor said:**
> Interestingly, I've discovered that when I put the same laptop I was talking about before into Suspend or Hibernation mode while having a paused video open in Totem, once I wake it up again the same problem that happens with the external LCD happens with the laptop's LCD.

It seems to gradually go out of sync. Sometimes takes it a few minutes to even become noticeable, but then it goes on to become completely unusable.

I'm starting to think this is a display driver issue, rather than some misconfiguration in the X server.

---

