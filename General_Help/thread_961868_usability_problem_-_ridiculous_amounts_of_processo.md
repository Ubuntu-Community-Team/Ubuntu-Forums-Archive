---
title: "usability problem - ridiculous amounts of processor, memory, hdd use during normal ta"
date: 2008-10-28
forum: General Help
---

### Post by insert_name_here on 2008-10-28
Specs: Lenovo T60, Intel Core Duo 2.0 gHz, Fujitsu 100gb HDD, 2gb RAM, 2GB swap, Ubuntu Hardy fully updated.

Problem:  My computer, in the past few weeks or so, has gotten really *really* slow.  Ordinarily, I'll boot up Ubuntu, and start Amarok, firefox 3.0, and pidgin.  Running in the background are the Ubuntu defaults, like beagle, tracker, pulseaudio, etc.  

My processor load is usually between 40% and 100%, my memory usage is usually about 33% for programs and 66% for cache, and my hard drive activity light is *always* on.  This causes serious usability issues - opening new tabs takes 10 seconds, closing Firefox takes 10 seconds or so, and amarok and firefox are often grayed-out by compiz for being non-responsive.

When I open system monitor, nothing looks strange.  My processor is hovering around 60% usage right now, but the system monitor says only about 20% of processor is being used -- about 15% for amarokapp and about 5% for beagled-helper.  What's the deal with this?

Additionally, I know that Linux allocates memory differently than Windows, but should it really be using >95% of RAM minutes after bootup?  That seems strange as well.

And finally, my hard drive is being used almost constantly.  That can't be good for it.  Part of this may be that Amarok is "updating collection" almost constantly, and I don't know why it sees a need to do that.  Any ideas?

Much thanks, and I'd be happy to clarify stuff.  I really need to make my computer usable again -- that's why I swtiched to Ubuntu from Windoze...

---

### Post by Mark_in_Hollywood on 2008-10-28
Open a terminal:

Applications / Accessories / Terminal

type:

top

cut and paste the results here.

---

### Post by insert_name_here on 2008-10-28
> top - 15:33:01 up 16:20,  2 users,  load average: 4.70, 5.07, 4.93
Tasks: 152 total,   1 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.9%us,  7.9%sy,  5.6%ni, 25.8%id, 38.3%wa,  1.2%hi,  0.3%si,  0.0%st
Mem:   2074536k total,  2026660k used,    47876k free,    22240k buffers
Swap:        0k total,        0k used,        0k free,  1296132k cached

The other stuff changes, of course, here's what my process list looked like: 
> 
 5573 mysql     20   0  127m  28m 5296 S   29  1.4  82:49.94 mysqld             
  499 merrillj  20   0  153m  45m  27m S   18  2.3   6:15.32 amarokapp          
 7043 merrillj  39  19 36396  16m 2736 D   11  0.8   8:17.02 trackerd           
 6194 root      20   0  271m 107m  22m S    4  5.3  29:28.66 Xorg               
 6918 merrillj   9 -11 39816 6488 3980 S    1  0.3   1:54.78 pulseaudio         
 2657 root      15  -5     0    0    0 D    1  0.0   0:45.92 kjournald          
 6932 merrillj  20   0 15424 4976 3952 S    1  0.2   0:15.28 gnome-screensav    
 7010 merrillj  20   0 25648  17m 5948 S    1  0.9   7:25.13 compiz.real        
 8509 merrillj  20   0 74592  16m  10m S    1  0.8   0:00.44 gnome-terminal     
 7226 merrillj  20   0 36296  11m 9560 S    0  0.6   4:02.89 multiload-apple    
 7837 merrillj  20   0  247m 123m  25m S    0  6.1   0:26.65 firefox            
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.44 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.34 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:04.92 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.16 migration/1  

Edit: I realize that swap is off.  Turning swap on/off doesn't fix anything.

---

### Post by sdennie on 2008-10-28
This is probably caused by tracker/beagle.  If you don't use them, you may want to disable them with System->Preferences->Search and Indexing.  Alternatively, just let them run and walk away from your computer for a few hours to see if they settle down.

As for RAM usage reaching 100% after a few minutes, this is normal on linux.  It's usually caused by the cache and that memory isn't what people would traditionally consider "used".  It's used to prevent having to read from the disk however, if more RAM is needed by your applications, the cache will be replaced by application memory.  Having your memory usage near 100% where the majority of it is cache is not only normal but makes your system much more responsive.

---

### Post by insert_name_here on 2008-10-28
Are beagle and tracker the same thing?  I would like to be able to search for stuff...  Should I keep one on and the other off?

---

### Post by alienprdkt on 2008-10-28
I was having these same problems with a intel core-duo 3.0GHz 2GB ram, turned out it was a known bug reported within [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)



Note: the follow up bug for this is bug #229745:
 #229745 - after fix for #215728 - Committing to urlclassifier3.sqlite still causes excessive CPU usage and disk I/O (the 2nd)

===

Browsing with Firefox 3.0b5 on Hardy (All updates applied) causes Xorg to use 50-60% CPU all the time.

I just removed firefox on my LAMP server now runs great!!!

---

### Post by insert_name_here on 2008-10-28
I don't think I'm using ff 3.0b5, but rather ff 3.0.3.  It is my understanding that the issue is fixed with release versions of firefox.

---

### Post by alienprdkt on 2008-10-28
well then I guess I can install newer version of firefox :D

---

### Post by alienprdkt on 2008-10-28
ok installed firefox 3.0.3 and rebooted waited bout 5 mins. and ran system monitor.

System Monitor and Firefox are the only things running.

Why is this version of firefox using bout 70% cpu? while i have it minimized, doing nothing?

Or should I start a new topic about this?

---

### Post by Mark_in_Hollywood on 2008-10-29
I'm giving you this info but I first say, I'm at the end of my knowledge about what is going on.

You could try to uninstall & reinstall FF. I don't prefer that solution, but could you install Flock or Opera or Epiphany and check the sys mon and see your CPU %s. If they are still higher than expected, I would run the memory test in recover mode (at boot time ESC). Truly, this isn't making sense. Possibly a hardware problem. We have to go "one thing at a time" to localize it. Sorry this post isn't more helpful. I had Origami installed. It runs between keystrokes and everthing else. It got fubared and started to pull 98% system resources (it was trying to run a .exe file). I removed the package. Things are normal.

---

