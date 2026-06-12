---
title: "No CPU scaling  (cpufreq) support"
date: 2008-06-19
forum: Hardware
---

### Post by cal-lito on 2008-06-19
I'm trying to enable CPU frequency scaling support on my M3A ASUS 
Motherboard with a Phenom 9850  running Ubuntu 8.04 with all upadtes 
applied.

When I install the applet, it tells me that my system does not 
support frequency scaling;  it then installs, and shows a CPU 
always running at 2.5GHz.

Through the command-line, the command cpufreq-selector responds 
with a "Frequency scaling not supported";  I indeed see nothing 
related on /sys/devices/system/cpu/cpu[0-3]

The BIOS reports that the CPU *does* support frequency scaling, 
yet it does not work.

Any ideas?  Any additional packages that I need to install? 
Play with the BIOS settings?  (I did already, but I see nothing 
that seems like a missing setting...)

Thanks for any tips!

Cal-lito
--

---

### Post by Twintop on 2008-06-21
Hi cal-lito,

There is not a K10 module available right now, but, the K8 module works in a limited capacity, letting a Phenom run at either 50% or 100%. Check out this post for some instructions: [http://ubuntuforums.org/showthread.php?t=679509&p=4721464](http://ubuntuforums.org/showthread.php?t=679509&p=4721464)

---

### Post by cal-lito on 2008-06-25
Thanks Twintop for the info!

However, it's still not working!

I already had powernowd installed;  when I try to run 
modprobe powernow-k8, I get the error:

FATAL: Error inserting powernow_k8 (/lib/modules/ ... /powenow-k8.ko):
No such device


Not sure what device it is talking about.  (would I need to 
mknode something?)

On /var/log/messages, no error is reported  (there's the line 
reporting that powernow-k8 found 1 AMD Phenom with 4 CPU cores).

Any ideas about what may be missing or misconfigured?

Thanks,

Cal-lito
--

---

### Post by Twintop on 2008-06-25
Do you have Cool'N'Quiet enabled or disabled in the BIOS? Also, are you overclocking at all? IIRC, if C'n'Q is disabled and/or you're overlocking (which means C'n'Q has to be disabled), you can't do scaling.

---

### Post by cal-lito on 2008-06-25
Wait!  Is it possible that the Cool'n'Quiet option has to be 
enabled *at installation time*??? 

I ask because it was disabled by default, and then, while 
attempting to make it work, I enabled that option  (I didn't 
know for sure, but it sounded like it might be necessary, so 
I tried enabling it --- but it still didn't work).

I also enabled the ACPI 2.0 functions  (also disabled by 
default) --- also without effect.

I'm wondering now if it may be that the installer configures 
all those entries appearing under /sys/devices/ ...  based 
on what it finds at that time?   If so  (not sure if this 
even makes sense), is there a way around it other than 
reinstalling?  (I'm guessing there should be ... )

Thanks,

Cal-lito
--

---

### Post by cal-lito on 2008-06-25
Never mind --- my silly mistake, apparently! 

It's working now;  I had disabled the Cool'n'Quiet for some 
reason;  I had enabled it and it didn't work, but it was 
because I didn't have the other stuff (the commands you 
pointed me to);  by the time I did execute those, the C'n'Q 
was back to disabled... 

Anyway, it looks pretty neat now (two-step limitation 
notwithstanding);  in fact, I encourage anyone running a 
Phenom (or any Quad-Core, for that matter) to place four of 
those little applets on the panel, and configure them to 
monitor one CPU core each --- veeeeeeery neat!  :-)

Thanks again for your patience and your help!

Cal-lito
--

---

### Post by Twintop on 2008-06-27
I have a startup script I threw together to enable the k8 powernow stuff. I can post it when I get home if you want? It is really, really simple.

---

