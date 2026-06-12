---
title: "RAM overload? processor overload? 450sx4"
date: 2008-10-01
forum: Hardware
---

### Post by Sabreful on 2008-10-01
Having a problem that I'm not completely sure where to go to figure it out. This problem happens about 50% of the time I boot my laptop up, and usually happens about 15 minutes into any type of download from torrent or video playback (VLC usually .avi files) when Ubuntu boots up correctly. 
Basically when I'm downloading via Deluge, occasionally just surfing the web, watching videos, even listening to music, and even just random points in browsing my file system my computer just overloads. Everything gets sluggish, slow, things don't open, video playback just stops or gets extremely choppy and repeating the same 1/5 of a second over and over. And that's when Ubuntu boots up correctly. When it doesn't boot up correctly it's the same way without being able to open anything.
I have added a system monitor to my taskbar just to see if anything popped up, and that's when I noticed that my computer pretty much spikes, it's either using all the available resources, or none at all (when i'm just staring at something, no doing anything even moving the mouse) when I hang my mouse over the graph it says that the Processor is %100 in use when it's 'frozen'. I've checked the processes and what not and there doesn't seem to be anything that shouldn't be in there running. 
Kind of an odd problem but still, it's a problem. I've tried a fresh install as well (twice) and the problem is still there. I know I don't have the best laptop(actually it's not really that good at all) but I hadn't ever had any problems like this when it was running only XP (and I did a whole lot more with XP because I haven't had enough time to fully play with all the awesome features of Ubuntu just yet)
In any case, the specs for my laptop are listed as followed;

Gateway 450sx4
Intel Pentium 4 1.6Ghz
512MB (DDR SDRAM) Originally only 256MB
RAM Speed  	 200 MHz 
Bus Speed  	 400 MHz 
19 GB Hard Drive
ATI M6-P (AllinWonder Radeon 7500 series)
Video Memory 32-MB DDRAM

I currently have 2 partitions, 13 GB for Ubuntu as it is my main OS, and Windows XP (5.5GB) due to the fact that it isn't very feasible to run XP programs through WINE due to the very basic Pentium 4 (for instance starcraft). 



Any other info will be happy to let you know, just ask.
I definitely know there are MUCH better laptops out there now, but something doesn't seem right, shouldn't I be able to just do the basics of watching simple movies, music, or regular torrent files? or does Hardy Heron need more than a Pentium 4 with 512 RAM to run smoothly on the 'NONE' graphics settings?


Thanks in advance everyone

---

### Post by SeanHodges on 2008-10-01
My first suspicion would be the Tracker indexing service, which can be a resource hog on slow machines.

System -> Preferences -> Sessions

Untick the "Tracker" item. Perhaps the "Tracker Applet one as well (no point it being on if the indexer is not running). Then reboot.

At the moment there isn't a lot to go on, but turning it off shouldn't cause you any problems unless you depend on the Tracker search utility. Worth a shot.

---

### Post by Kevbert on 2008-10-01
Two possible things you could try.  
If possible add more ram.  I had a similar problem until I increased the memory on my laptop from 512Mb to 1.25Mb. Compiz would run slowly and DVDs would occasionally stutter for no apparent reason.
Try Xubuntu.  It's a cut down, streamlined version of Ubuntu which runs a lot faster.

---

### Post by michaelkahl on 2008-10-01
It's always difficult to advice on an issue like this.  It sounds more like processor utilization is what you are seeing on your panel.  On a slower CPU, especially being a single core CPU I think you will see more utilization.  My advice is check your processes in system monitor.  You can find this listed under administrative tools.  
You can also run the command:
top
This isn't as pretty as the GUI application, but you can see whats eating up that CPU usage.  You can also see your Memory(ram) usage with both of these applications.

---

### Post by Sabreful on 2008-10-01
Firstly, what does the Tracker and Tracker Client do? And how would I depend on it?
And unfortunately, 512MB of RAM is the max that this laptop will handle, if i put in any more than that the BIOS won't recognize it AND will NOT even boot through the BIOS, meaning I can't even get into my operating system and unless there's a way around that, I'm at a loss. I do happen do have an extra ddr2 slot available though, and an extra 512MB RAM just sitting around, but if I add it, for some reason just won't boot.
With Xubuntu, is there anything that Xubuntu can't do that Ubuntu can?
Lastly, ran 'top' to see what was eating my processes and when I have firefox open (like now) it's pretty much at the top, changing from second to top occasionally is something called 'Zorg' and thirdly and fourthly is gnome-terminal and gnome-panel. metacity and nm-applet also appear occasionally.

here's what is being said at the current moment 

Tasks:  99 total,   2 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s): 29.3%us,  3.7%sy,  0.0%ni, 67.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515060k total,   505984k used,     9076k free,    14816k buffers
Swap:   626492k total,        0k used,   626492k free,   288560k cached
Maximum tasks = 0, change to (0 is unlimited):   
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5198 root      20   0  107m  18m 8196 S 14.3  3.7   1:00.46 Xorg               
 5811 requiem   20   0  189m  80m  24m R 11.6 16.0   2:34.53 firefox            
 5557 requiem   20   0 20940  12m 7600 S  2.0  2.4   0:03.14 metacity           
 4639 root      15  -5     0    0    0 S  0.7  0.0   0:03.80 kondemand/0        
 5552 requiem   20   0 15324 2560 1688 S  0.7  0.5   0:03.00 gnome-screensav    
 5559 requiem   20   0 37156  20m  12m S  0.7  4.1   0:04.58 gnome-panel        
 5585 requiem   20   0 26104  13m 9040 S  0.7  2.7   0:02.32 nm-applet          
 6481 requiem   20   0 74664  19m  10m S  0.7  4.0   0:01.16 gnome-terminal     
 6501 requiem   20   0  2308 1100  852 R  0.7  0.2   0:00.54 top                
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:01.98 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0      

Anything I can do about the max amount of RAM? And why is it that I hadn't ever encountered any problems like this with XP? 
Thanks again everyone

---

### Post by Kevbert on 2008-10-02
Are both sticks of memory the same or are they different speeds, ECC/non ECC etc.  You shouldn't mix and match memory.  Have you tried just using the new memory instead of what's currently installed ?  It may be faulty or the socket may be faulty.  You could also check that the bios allows additional memory to be fitted (without changing any settings) and also try resetting via the link to the battery.

---

### Post by Sabreful on 2008-10-02
Both peices are the same, same brand, same manufacturer, same type, same amount. the original amount in my computer was 512RAM with 2 different 256MB using both slots. I didn't want just the 256 so I got 2 two 512MB DDR2 thinking to upgrade to a GB would drastically help everything I did with XP, this was many months ago. In any case I tried many things. First off I had both of the 512MB RAM installed, and the computer didn't boot into BIOS. So I took one stick out and it worked just fine. Shut down and switched sides just to make sure that both available slots were working. It was. Tried again with both 512 and still didn't work. Just trying out different things tried using a 512MB stick and a 256MB stick. The computer booted up just fine, only that it wouldn't recognize anything past the 512MB of ram. 

How would I see if my BIOS would allow additional memory? Secondly, are there any changes that I COULD make that would allow additional memory?
And what would I be resetting via link to the battery?

---

