---
title: "computer shuts down when playing flash videos now?"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by rose34 on 2009-09-17
Hi everyone,

I installed a few updates last night, as I haven't had internet access for a little while - about 110MB worth, afraid I can't remember all the names of the updates though. Now when I'm playing a flash video in Firefox after about 10-15 minutes the tower will sound a two tone alarm, and the computer shuts down. It doesn't seem to happen while doing any other task, just this. Has anyone got any ideas what could have happened?

Thanks,
Joe

---

### Post by rose34 on 2009-09-17
has nobody got any ideas about this?

thanks,
Joe

---

### Post by QIII on 2009-09-17
Please wait 24 hours before bumping.  Doing it too soon is considered poor sportsmanship and the moderators may strike you with lightning.

You may be heating something up, such as your processor.  Why, I don't know.

But it sounds like the "Oh, crud I'm hot" CPU shutdown.

Try installing a temperature sensor from Applications and putting it on your panel.

Watch the temperature of your processor and see if it starts to climb unreasonably.  That might give us an indication where to proceed.

---

### Post by rose34 on 2009-09-17
my sincere apologies - I did not realize it was considered rude to bump before 24 hours were up!

thanks for the advice, I wonder why it does this only when playing flash videos though? Will try and get a temperature sensor and see what it comes out with.

Thanks,
Joe

---

### Post by QIII on 2009-09-17
That may not be it at all, but that's what it sounds like.  What we're really doing here is ruling out a possible cause.

Sometimes troubleshooting is ruling out everything you can.

---

### Post by rose34 on 2009-09-17
I've just tried to install hardware sensors, as detailed on this page:

[http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/)

I got down to the part where it says add applet to the panel, however when I right click on the panel and choose add to panel I don't see any Hardware Sensors Monitor, or anything like it. However all the other steps seemed to go fine. Any ideas why this might be please?

sorry to be a pain, I'm getting better with linux but still not absolutely sure what I'm doing all the time!

Thank you very much,

Joe

---

### Post by rose34 on 2009-09-17
ok, sorry about that - I managed to get hardware sensors working.

Sys Temp and AUX Temp both remain constant, at 33C and 50C respectively. CPU Temp is around 60-65C while I do most tasks, browse the web, listen to music, use OpenOffice etc. Once I start using flash however, it climbs up to 70 and would probably keep climbing but I exit the video as I don't want to damage my computer. It seems to climb faster when the video is in fullscreen mode.

Even the idle temperature of 60C seems quite hot - I have an Intel Celeron D processor, and [this thread]("http://www.geekstogo.com/forum/Celeron-D-340-Acceptable-Temperature-t103926.html") on a seperate forum seems to suggest that 53C is a bit too high.

As it wasn't until I installed the most recent updates that I started to have this problem, is it possible that one of them caused this? However, I don't know what temperature the CPU was running at before then.

Thanks again,
Joe

---

### Post by QIII on 2009-09-17
Definitely hot.
 
I get excited above 35 degrees, which only happens on hot days without the air conditioner on.
 
You are definitely headed for trouble if you are running that hot constantly.  The supposed "max" operating temperature of your CPU is the point just before it spontaneously erupts into flames.  You don't ever want to have your machine running anywhere close to that.
 
Go to the terminal and type 
 
```
top
```Stop the updates by pressing control+C, then cut and paste the results.
 
We'll see what is eating your CPU.
 
One thing that often does not show up in top is vino (desktop sharing).  Check to see if it is on and turn it off if it is.

Edit:  Sorry -- didn't tell you how to do that.  Sometimes I forget I know what I'm talking about, but you may not.

Systems | Preferences | Remote Desktop  Uncheck "sharing"  (I think.  I'm not at my Ubuntu machine right now.)

---

### Post by rose34 on 2009-09-17
Remote Desktop is not on, and here are the results from top: (I hope they appear ok, I don't know how to format the text so it doesn't get broken up by the website)
> 
joe@joe-desktop:~$ top

top - 00:21:14 up 56 min,  2 users,  load average: 1.01, 0.95, 0.89
Tasks: 127 total,   3 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.0%us,  9.7%sy,  0.0%ni, 69.7%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    443640k total,   438152k used,     5488k free,     2296k buffers
Swap:  1309256k total,   113192k used,  1196064k free,    90252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3375 joe       20   0  440m 173m  17m R 16.3 40.1  19:05.52 firefox            
 2696 root      20   0  264m  57m 8648 S  7.0 13.3   4:00.66 Xorg               
 3218 joe       20   0  156m 2616 1788 S  2.3  0.6   1:16.04 pulseaudio         
 3256 joe       20   0 22912 8120 5336 S  1.0  1.8   0:07.97 metacity           
 1652 root      15  -5     0    0    0 S  0.7  0.0   0:18.44 ntos_wq            
 4878 joe       20   0 32028 9760 4940 R  0.7  2.2   0:01.24 gnome-terminal     
 3250 joe       20   0 30544 3448 2540 S  0.3  0.8   0:02.28 gnome-settings-    
 3257 joe       20   0 48328  11m 5236 S  0.3  2.8   0:24.63 gnome-panel        
 3520 joe       20   0 29104 5736 3992 S  0.3  1.3   0:23.05 sensors-applet     
    1 root      20   0  3084  328  304 S  0.0  0.1   0:01.29 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.11 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0       


thanks a lot for taking the time to help, this is why I love ubuntu -  the amount of support and help available!

---

### Post by QIII on 2009-09-17
You were only using about 30% of your CPU at the time, 70% idle.  

Is there anything obstructing your fan?  Can you hear it running?  Can you take off the case cover and blow out the dust bunnies?

---

### Post by RJARRRPCGP on 2009-09-17
Sounds like you need to clean and reseat the heatsink. 

Don't forget to spread even thin coat of thermal paste over the top of the processor, just enough to cover the top, where you can't see the silver top of the heat spreader.

---

