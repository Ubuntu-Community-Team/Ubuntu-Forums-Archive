---
title: "Why is my ubuntu using 80% resources with nothing running?"
date: 2008-09-18
forum: General Help
---

### Post by raiderleaf on 2008-09-18
I have a HPdv5000 with an AMD Turion64 2.2GHz Processor, 2 GB of ram, latest version of Ubuntu, but my system resources window says i'm constantly using over 80% when nothing is running. I don't know what is going on. What can I do to lower this down a lot?

---

### Post by fooman on 2008-09-18
see whats eating it up...run "top" in a terminal:

```
top
```

---

### Post by Nitefang on 2008-09-18
Top is useful but I prefer to use the System Monitor in the Main Menu (the bar thing [I think that's what it is called]) System>Administration>System Monitor. Once in there go to resources, that will tell you things like processor usage and memory usage, then go to services to see what is actually causing the problem.

  I don't see what is the point of using top besides be able to post the information here, can it be used to do things besides monitoring the system?

---

### Post by mb_webguy on 2008-09-18
> **Nitefang said:**
> Top is useful but I prefer to use the System Monitor in the Main Menu (the bar thing [I think that's what it is called]) System>Administration>System Monitor. Once in there go to resources, that will tell you things like processor usage and memory usage, then go to services to see what is actually causing the problem.

  I don't see what is the point of using top besides be able to post the information here, can it be used to do things besides monitoring the system?

Top provides all of the information you named, and is more accurate.

---

### Post by Nitefang on 2008-09-18
> **mb_webguy said:**
> Top provides all of the information you named, and is more accurate.

Ooooh, ok. Thank you for clearing that up.

---

### Post by mb_webguy on 2008-09-18
Don't get me wrong...  I use System Monitor all of the time, just to keep an eye on what's going on with my system.  It's certainly easier to read.  But it doesn't always report memory or CPU usage correctly, while top does.  So if I'm trying to figure out why something doesn't look or act like I think it should, I'll use top.

Also, when getting help on the forums, it's easier to post the output of top than it is to post a screenshot of System Monitor.

---

### Post by bigbear2350 on 2008-09-18
Some of the 80% could be disk cache. Linux dosent like leaving memory unused unlike windows.

---

### Post by Lord Udedenkz on 2008-09-18
XORG is using 1-60% of my C2D T8300... espiecially high for some reason when using flash.

---

### Post by mb_webguy on 2008-09-18
> **Lord Udedenkz said:**
> XORG is using 1-60% of my C2D T8300... espiecially high for some reason when using flash.

Xorg will naturally spike briefly at certain times, such as when when moving the mouse or drawing a window, but it shouldn't stay high for an extended period.

---

### Post by Lord Udedenkz on 2008-09-18
> **mb_webguy said:**
> Xorg will naturally spike briefly at certain times, such as when when moving the mouse or drawing a window, but it shouldn't stay high for an extended period.

Eye it goes back down when I pause any open youtube videos.

---

### Post by Nitefang on 2008-09-19
Wow I just looked at my System Monitor, one of my CPUS is going at a 100%, another is at 20% another one is at 34% and my last one is about 10%. It has been that way for the past few minutes. I am also using about 740Mb or RAM and firefox is 248Mb alone. I am going to bed now but tomorrow I am going to compare all of this to Vista. I sear i never used this much of my resuarces with Vista.

---

### Post by mssever on 2008-09-19
> **mb_webguy said:**
> Top provides all of the information you named, and is more accurate.
htop is a nice alternative to top. I no longer use top.

---

### Post by mb_webguy on 2008-09-19
I find that the colors make htop harder to read than top, but it could just be my terminal settings.  YMMV.

---

### Post by raiderleaf on 2008-09-19
please look below!

---

### Post by raiderleaf on 2008-09-19
raiderleaf@raiderleaf-laptop:~$ top

top - 11:31:49 up 30 min,  2 users,  load average: 0.51, 0.62, 0.75
Tasks: 123 total,   1 running, 121 sleeping,   0 stopped,   1 zombie
Cpu(s): 23.8%us, 13.6%sy,  0.0%ni, 62.0%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   2074392k total,  1146684k used,   927708k free,    18584k buffers
Swap:  2096472k total,        0k used,  2096472k free,   478844k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                     
 5834 raiderleaf  20   0  291m 131m  26m S 22.0  6.5   9:17.10 Xgl                                                                                         
 6250 raiderleaf  20   0 54248  22m  14m S 12.6  1.1   3:20.94 gnome-system-mo                                                                             
 6830 raiderleaf  20   0 88112  19m  11m S  0.8  1.0   0:01.06 gnome-terminal                                                                              
 5901 raiderleaf  20   0 21032  13m 5388 S  0.5  0.7   0:13.02 compiz.real                                                                                 
 6254 raiderleaf  20   0  245m 107m  24m S  0.5  5.3   1:47.59 firefox                                                                                     
 6536 raiderleaf  20   0  196m  75m  50m S  0.5  3.7   0:20.72 soffice.bin                                                                                 
  171 root      20   0     0    0    0 S  0.3  0.0   0:00.04 pdflush                                                                                     
 2520 root      15  -5     0    0    0 S  0.3  0.0   0:00.10 kjournald                                                                                   
 4974 avahi     20   0  3024 1652 1212 S  0.3  0.1   0:04.72 avahi-daemon                                                                                
 5347 root      20   0  182m  27m 7648 S  0.3  1.4   0:09.98 Xorg                                                                                        
 6850 raiderleaf  20   0  4164 1556 1152 R  0.3  0.1   0:00.22 top                                                                                         
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.06 init                                                                                        
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                    
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                 
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0                                                                                 
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                  
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0                                                                                    
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                     
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0                                                                                   
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                      
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                
  133 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kseriod                                                                                     
  172 root      20   0     0    0    0 S  0.0  0.0   0:00.18 pdflush                                                                                     
  173 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                     
  214 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                       
 1485 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                               
 1488 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                       
 1520 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                    
 2331 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                       
 2333 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                     
 2348 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0

---

### Post by raiderleaf on 2008-09-19
I do have a picture from htop available, but I don't know how to get it on here because it asks for a URl...pm me with an email or something and I'll send it to you if you'd like

---

### Post by raiderleaf on 2008-09-19
Any updates anyone? Thanks,

raiderleaf

---

### Post by retrow on 2008-09-19
oftentimes, the only process that is running when your system is 'idle', is Tracker or tracker-search-tool. Tracker is documenting your files and sometimes searching within the files to build a database of your files and some of their content. You can look under Sessions and disable the loading of tracker at startup if you don't care much about creating a database of your files. 

As a matter of fact you can just go ahead and remove tracker and its related files:
```
sudo apt-get remove tracker tracker-search-tool tracker-utils
```

---

### Post by fooman on 2008-09-19
> **Nitefang said:**
> Wow I just looked at my System Monitor, one of my CPUS is going at a 100%, another is at 20% another one is at 34% and my last one is about 10%. It has been that way for the past few minutes. I am also using about 740Mb or RAM and firefox is 248Mb alone. I am going to bed now but tomorrow I am going to compare all of this to Vista. I sear i never used this much of my resuarces with Vista.

just opening system monitor will make your cpu jump +20-25%.  at least it does with my amd dual-core.

while my system monitor applet in the panel may be idling away at 0%....as soon as i open it up onto my desktop,  one cpu will jump to at least 20-25%, while the other will get up to 5-10% (both in the window on my desktop and the monitor applet in my panel).  
as soon as i close that desktop system monitor window, the monitor in my panel will drop back down to 0%.

---

### Post by raiderleaf on 2008-09-19
See I would love to get my computer down to 5-10% or better yet 0, but the fact remains that right now as I'm typing this I am running at 100% and the only thing running is the Avant Window Manager and Firefox. That is it... What can I do to fix this? I even removed the tracker thing as aforementioned, but no improvement....

---

### Post by raiderleaf on 2008-09-19
^^^

---

### Post by mssever on 2008-09-19
> **raiderleaf said:**
> I do have a picture from htop available, but I don't know how to get it on here because it asks for a URl...pm me with an email or something and I'll send it to you if you'd likeJust attach the picture using the Manage Attachments button.

---

### Post by raiderleaf on 2008-09-19
> **mssever said:**
> Just attach the picture using the Manage Attachments button.

Here it is:

---

### Post by Steveway on 2008-09-19
> **raiderleaf said:**
> Here it is:

Why in the world are you using XGL?
It is discontinued and not needed anymore.
As I can see it is XGL that is eating up all your processing-power.

---

### Post by raiderleaf on 2008-09-19
How do I get rid of XGL? What do I do? When I kill the process it logs me off and when I log back in, it is still running. How do I get rid of it, and do I need to replace it with anything?

---

### Post by Steveway on 2008-09-19
The way to remove it depends on how you installed it.
Normally you should be able to remove it with your package-manager.

---

### Post by mssever on 2008-09-19
> **raiderleaf said:**
> How do I get rid of XGL? What do I do? When I kill the process it logs me off and when I log back in, it is still running. How do I get rid of it, and do I need to replace it with anything?
XGL is a remix of Xorg (I think) to provide compositing support. It worked somewhat when I used it back in 2006. But as Steveway said, it's now obsolete. I'm guessing you followed some outdated tutorial somewhere and got XGL that way. Undo that tutorial.

(There are a lot of outdated tutorials out there. Don't follow tutorials unless you're sure they're complete and up-to-date.)

---

### Post by LongMike on 2008-09-30
Hey, this is my first post on the forums, so sorry if I forget something.  I have been having the same problem with a Lenovo X200.  Top shows almost no CPU usage, but the battery lasts only about 70% as long as with Vista and the fan is usually on (laptop gets hotter).  With only firefox and the terminal open, PowerTOP reports C0 (2% @ 2.41GHz) C1 (0% @ 2.4GHz) C2 (.2% 1.6GHz) C3 (97.1% @ 800MHz).  Something is fishy here.

---

### Post by mssever on 2008-09-30
> **LongMike said:**
> Hey, this is my first post on the forums, so sorry if I forget something.  I have been having the same problem with a Lenovo X200.  Top shows almost no CPU usage, but the battery lasts only about 70% as long as with Vista and the fan is usually on (laptop gets hotter).  With only firefox and the terminal open, PowerTOP reports C0 (2% @ 2.41GHz) C1 (0% @ 2.4GHz) C2 (.2% 1.6GHz) C3 (97.1% @ 800MHz).  Something is fishy here.Welcome to Ubuntu Forums!

You didn't say which process is eating 97% of core 3. That's info we need.

Also, it's usually best to post new questions in new threads. Probably the only people who saw your post were the ones who posted earlier in this thread. And we might not know anything about your problem, since it isn't the same as the OP's problem--unless you're also running XGL, which you shouldn't be doing these days.

---

### Post by raiderleaf on 2008-09-30
On another note, it seems to be a common trend that Ubuntu users have less battery life than Windows. How can this be considering that all I hear about Linux use is that it is "more efficient"?

---

### Post by ft23002 on 2008-09-30
> **raiderleaf said:**
> On another note, it seems to be a common trend that Ubuntu users have less battery life than Windows. How can this be considering that all I hear about Linux use is that it is "more efficient"?

System Monitor itself uses a lot of resources. Keeping system monitor closed and run top in terminal. It should drop. When I have system monitor opened cores bounce around at around 60% use.

If your using a taskbar, right click and choose "add to panel" and choose system monitor. Its a basic cpu display that works well for seeing overall cpu use in graph form.

Also, you could install screenlets. It has a screenlet or widget called sysmonitor that has lots of useful info on system like each core use, ram use, swap file, load, etc. It can be installed via the synaptic package manager. Start the spm and search for "screenlets". It uses very little resources.
You can search the web for more info on screenlets and find screenshots. Its a great desktop addon with lots of useful widgets just like vista's sidebar.
There is a newer version that is out, but would need to be manualy installed. If you install the version that in the synaptic package manager and use the weather screenlet, there is a file that needs to be edited b/c weather.com changed the web address. Search this forum for "how to" fix. The newer manually installed version should be OK with weather. Theres lots of options for each screenlet used to set them up as you like, you will have to play around with them to get them to work the way you want. Its not hard, but lots of options (which I like) to choose from to have work as you want.

---

