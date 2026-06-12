---
title: "ubuntu 11.04...system slow"
date: 2011-05-26
forum: Hardware
---

### Post by donny.davis on 2011-05-26
i installed ubuntu 11.04 on my comp
my comp is 7-8 yrs old

Here is my system info:

OS : Ubuntu 11.04 (natty)
Kernel  : 2.6.38-8-generic
CPU : Intel(R) Pentium(R) 4 CPU 2.40GHz
RAM : 512 + 256 MiB
HardDisk : 160GB
Motherboard : Advik motherboard 845 GL (intel chipset based) 
BIOS : AwardBios
Display : Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (VGA Controller)  64MB

i also hv windows xp installed on my system(separate partition)

the problem is that the new untiy desktop does not run properly in my system
also the CPU usage % is always 100%
even if i run a video in VLC it uses 100% of my CPU
same case with games n other things
also the system is a little slow n slaggy

can any one tel me what is the problem
Is the Intel Pentium 4...the problem, becoz the cpu usage is mostly 100%
can u'll also suggest me which ubuntu version will be suitable for my system

---

### Post by Joe of loath on 2011-05-26
Does the problem persist if you log in using the 'classic desktop' option?

---

### Post by ivanovnegro on 2011-05-26
I would suggest you to really go with Lubuntu.
It should run like a dream on your hardware. :)

---

### Post by donny.davis on 2011-05-27
but is ubuntu 11.04 not compatible with pentium 4 ???

---

### Post by jbowen7 on 2011-05-27
Open up a terminal, copy and paste the following then post the result.

ps aux | awk '{print $3, $11}' | sort

---

### Post by jbowen7 on 2011-05-27
Don't use the last command use this instead:

ps aux | awk '{print $3, $11}' | sort | tail

---

### Post by mastablasta on 2011-05-27
> **donny.davis said:**
> but is ubuntu 11.04 not compatible with pentium 4 ???
 
 
it is compatible but poor intel graphics card driver and poor card in general prevent it from performing well.
 
using Xubuntu or even Lubuntu will reduce the need for graphics card to draw complex environment. as these two DE's are fairly simple.
 
but you may still have slow response when you use some more demanding programmes. it's because graphics card is crappy and so are the linux drivers for it. :-)

---

### Post by donny.davis on 2011-05-27
> **jbowen7 said:**
> Don't use the last command use this instead:

ps aux | awk '{print $3, $11}' | sort | tail


0.7 metacity
0.7 mono
13.5 vlc
1.4 /usr/lib/firefox-4.0.1/plugin-container
2.0 ps
35.2 /usr/bin/python
35.3 /usr/bin/X
3.8 /usr/bin/pulseaudio
4.8 /usr/lib/firefox-4.0.1/firefox-bin
%CPU COMMAND


also here is the output of $ top (when i tired to run a video in vlc)
cpu%  mem%   process
 76.5     10.3   Xorg               
 10.9      8.1     vlc

---

### Post by donny.davis on 2011-05-27
> **mastablasta said:**
> it is compatible but poor intel graphics card driver and poor card in general prevent it from performing well.
 
using Xubuntu or even Lubuntu will reduce the need for graphics card to draw complex environment. as these two DE's are fairly simple.
 
but you may still have slow response when you use some more demanding programmes. it's because graphics card is crappy and so are the linux drivers for it. :-)


so should i remove ubuntu 11.04 and install lubuntu

---

### Post by ivanovnegro on 2011-05-27
> **donny.davis said:**
> so should i remove ubuntu 11.04 and install lubuntu

I would give it a try.

---

### Post by donny.davis on 2011-05-29
i'll install lubuntu but only after fewdays.. but will my machine get affected if i continue to use ubuntu 11.04

---

### Post by donny.davis on 2011-05-31
i have few questions about lubuntu

will i be able to use all the softwares tht i was using on ubuntu.. i know it is open source but just wanted to confirm ??

---

### Post by ivanovnegro on 2011-05-31
> **donny.davis said:**
> i have few questions about lubuntu

will i be able to use all the softwares tht i was using on ubuntu.. i know it is open source but just wanted to confirm ??

Yes, you will.

---

### Post by Yellow Pasque on 2011-05-31
> can anyone tell me what is the problem
.. Found it!
> CPU : Intel(R) Pentium(R) 4 CPU 2.40GHz
RAM : 512 + 256 MiB
Display : Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (VGA Controller) 64MB
Sorry to burst your bubble, but you need better hardware. The intel i8xx series was meant for office work, not media. And a P4 @ 2.4 Ghz isn't up to the task.

---

### Post by donny.davis on 2011-06-01
so its a good decision to install Lubuntu...
Thank you...

---

### Post by donny.davis on 2011-06-01
should i install a fresh copy of lubuntu or from ubuntu itself shift to lubuntu.... becoz for a fresh installation again i need to format my disk..

---

### Post by mastablasta on 2011-06-01
you can try just installing LXDE to your curreent install and then removing Gnome from it (so you don't have doubled programmes). for example here is how you install XFCE: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
 
you can try this first. it will show in the login menu. XFCE has two options - one is Xubuntu (a bit nicer and graphically more intense) and XFCE session a bit lighter and simpler. give them a try before Lubutnu (LXDE). they might be working just fine and Xubuntu (XFCE) is a more mature desktop environment).
 
you can then easilly remove Gnome (just look on same web page left side menu->Pure XFCE)

---

### Post by Yellow Pasque on 2011-06-01
> **donny.davis said:**
> so its a good decision to install Lubuntu...
Thank you...
That helps with general usability, but it won't make video playback better.

---

### Post by donny.davis on 2011-06-02
im now working on pure xfce..everything is working fine(except the video problem) but still the machine does not shut down properly..same scenario with log out
the fan is still working... the yellow LED light on the cabinet is still glowing
and also the system hangs with a black screen..

i had the same problem with ubuntu

---

### Post by donny.davis on 2011-06-04
can anyone help me with the shut down problem

---

### Post by donny.davis on 2011-06-06
chk out the .png file
xorg is using almost my full cpu when i try to run a video or even firefox
it goes down only if i close it or minimize it

---

