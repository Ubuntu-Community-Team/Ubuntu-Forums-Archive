---
title: "Jaunty keeps my PIII working hard"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by edhawk2 on 2009-05-02
I upgraded from Ibex to Jaunty last week and the system monitor shows that my Dell Latitude (PIII /1200 MgHz)'s CPU is working close to 90% just running the OS with no applications opened.  I have a gig of RAM and I'm wondering if more RAM will ease up the load on the processor. 

Any suggestions??

---

### Post by surfed on 2009-05-02
iF you run "top" what process uses all that cpu power?

---

### Post by edhawk2 on 2009-05-02
I'm very new to this linux, 

what is "top?"

---

### Post by surfed on 2009-05-03
Open a terminal (Applications/Accessories/Terminal) and enter top at the comand prompt. What are the topmost command listed and how much cpu do they use?

---

### Post by edhawk2 on 2009-05-03
This is interesting, the first lines read something like this:

USER       %CPU         %MEM        COMMAND
root       66.8         2.9           Xorg
freevo     12.9         3.7           pyth8.3on
ed          8.3         8.8           firefox
ed          6.6         1.8           gnome-system-mo

---

### Post by surfed on 2009-05-03
67% for X is too much.... what video card is in that dell? is freevo running on purpose? Gnome system monitor is using almost 7% of cpu, use top instead to save resources.
Kill all freevo processes and see if X use goes down.

---

### Post by strikeback03 on 2009-05-03
I'm having similar issues with my desktop.  This is reasonably modern hardware (E6600 C2D, P965 chipset, 4GB DDR2) and CPU usage is hovering over 80% on both cores.  Here is the result of top:

 3696 steve     20   0 23624 2996  660 R   45  0.1  22:31.02 dbus-daemon        
 3883 steve     39  19  158m  17m 5948 R   43  0.4  20:19.28 tracker-indexer    
 3822 steve     20   0  212m  20m 8976 R   39  0.5  20:11.51 python             
 3828 steve     39  19  297m  18m 5424 R   32  0.5  14:58.17 trackerd           
 8166 steve     20   0  592m 158m  26m S    3  4.1   2:19.87 firefox            
 3127 root      20   0  290m  99m  15m S    1  2.6   1:28.75 Xorg               
 3800 steve     20   0  310m  43m  15m S    1  1.1   0:25.42 compiz.real        
 3489 chipcard  20   0 27700 1956 1100 S    0  0.0   0:17.28 chipcardd4      

so dbus-daemon, tracker-indexer, python, and trackerd are all taking a lot of resources.  This didn't happen previously in 8.04.  Any ideas what is wrong?

---

### Post by surfed on 2009-05-03
> **strikeback03 said:**
> I'm having similar issues with my desktop.  This is reasonably modern hardware (E6600 C2D, P965 chipset, 4GB DDR2) and CPU usage is hovering over 80% on both cores.  Here is the result of top:

 3696 steve     20   0 23624 2996  660 R   45  0.1  22:31.02 dbus-daemon        
 3883 steve     39  19  158m  17m 5948 R   43  0.4  20:19.28 tracker-indexer    
 3822 steve     20   0  212m  20m 8976 R   39  0.5  20:11.51 python             
 3828 steve     39  19  297m  18m 5424 R   32  0.5  14:58.17 trackerd           
 8166 steve     20   0  592m 158m  26m S    3  4.1   2:19.87 firefox            
 3127 root      20   0  290m  99m  15m S    1  2.6   1:28.75 Xorg               
 3800 steve     20   0  310m  43m  15m S    1  1.1   0:25.42 compiz.real        
 3489 chipcard  20   0 27700 1956 1100 S    0  0.0   0:17.28 chipcardd4      

so dbus-daemon, tracker-indexer, python, and trackerd are all taking a lot of resources.  This didn't happen previously in 8.04.  Any ideas what is wrong?

I had similar issues with tracker, just disabled it as i dont need everything indexed....

---

### Post by fjpos on 2009-05-04
> **edhawk2 said:**
> I upgraded from Ibex to Jaunty last week and the system monitor shows that my Dell Latitude (PIII /1200 MgHz)'s CPU is working close to 90% just running the OS with no applications opened.  I have a gig of RAM and I'm wondering if more RAM will ease up the load on the processor. 

Any suggestions??

Hi  too high CPU Xorg ers.

After trying to close down a few services to perhaps see what  if anything I was using was overusing Xorg I eventually [COLOR="Red"]stopped vino-server[/COLOR] which in itself was not using a lot of the  CPU. However straight after I killed it bang my CPU usage went down 1%-4%. Vino-server is part of the gnome remote desktop. The system still did feel a little highly strung with the CPU happy to increase  with  compiz usage  which I have somewhat turned of some it's features. Note before I upgraded  all worked fine under 8.10. However 9.04 is now a how lot better as expected.  I hope this may help

---

### Post by edhawk2 on 2009-05-04
I'm in a bit over my head in all this, but here's a very interesting thing: 

I shut down the blue tooth stuff under system/admin/system services.  CPU usage went down to below 20% and the free-vo disappeared.  I opened admin's system monitor and CPU usage went back up to 80-95%.  I then opened top and closed the system monitor and CPU usage went back down to about 18%.

What is this telling me?

---

### Post by surfed on 2009-05-05
> **edhawk2 said:**
> I'm in a bit over my head in all this, but here's a very interesting thing: 

I shut down the blue tooth stuff under system/admin/system services.  CPU usage went down to below 20% and the free-vo disappeared.  I opened admin's system monitor and CPU usage went back up to 80-95%.  I then opened top and closed the system monitor and CPU usage went back down to about 18%.

What is this telling me?

So whats that process using the cpu when you open system monitor

---

### Post by a2z on 2009-05-05
I"m also experienciing  extrodinary high cpu usage all of the sudden. At 100% on one cpu.

"System monitor (Process)"  indicates only gnome-panel using 24%cpu

"Top" indicates cpu 100% 
"gkrellm" = cpu 0=0, cpu1=100%, cpu2=0, cpu3=0

It also shows 3 users? I'm assuming root is one user, me the second, but I never set up any additional users.

I hope this info helps a little in regards to getting this problem resolved.

I also commend **all** linux distro board monitors for their excellence and time sorting through literally thousands of different configurations not to  mention operator malfunctions. My hats off to you all. Thanks!

a2z

asus p5n-d
intel q6700 2 dual  quad 2.66ghz
corsair 2x2gig
wd 500gig hd
nvidia 8500gt
x86_64 Kernel Module 180.44

---

### Post by surfed on 2009-05-05
it shows 3 users as one logged into x, and one for each open terminal window.
System monitor is 24% total of all cores while gkrellm is 100% on one core of 4 cores. gnome panel should not take up all of one core, investigate.

---

