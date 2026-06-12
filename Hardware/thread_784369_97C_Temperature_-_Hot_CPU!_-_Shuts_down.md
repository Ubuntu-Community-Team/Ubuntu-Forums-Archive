---
title: "97C Temperature - Hot CPU! - Shuts down"
date: 2008-05-06
forum: Hardware
---

### Post by cmavr8 on 2008-05-06
Hello everybody,

I have a Lenovo 3000 V100 Laptop with latest Ubuntu. I've been running Ubuntu for almost 2 years, and this problem exists from the first moment I installed it. (along with no webcam support and no fingerprint support)

My cpu temperature is high. I have scaling enabled, and usually limit the Frequency to 1Ghz. At normal load (cpu at 10% max) my temps read 52 and 60 for the two cores. This is degrees Celcius.

When I'm processing videos, and let the governor "ondemand" on, CPU clock goes to 2Ghz for both cores, and the temp rises. 

At some point, I can't touch the part where the HD is (below the laptop), neither the VGA-out connector on the side. CPU Fan seems to be working at good speed (not noisy) but temperature is around 90 degrees Celcius.

So, after a few minutes, critical 97 degrees is reached, and laptop is ordered to shutdown... So I loose any work!

That's not good at all...
It even happens when I have the laptop sitting on a hard surface and at an angle so that there's plenty of room beneath it.

I even get shut down when "ondemand" frequency is selected, sometimes..

Have searched and tried many things, no fix..

Any ideas? 
Thanks..

---

### Post by Bal_Zac on 2008-05-06
[IMG]http://www.crowriveraudio.com/tk/dustoff.jpg[/IMG]

                          +

[IMG]http://techrepublic.com.com/i/tr/gallery/dirtycomputers/279633767neswPf_fs.jpg[/IMG]

                          =

                         :guitar:

---

### Post by cmavr8 on 2008-05-06
Lol...
Well, not my case. My laptop was new when I first installed Ubuntu... Windows worked fine.

Here's my syslog:

> May  6 21:23:50 chris-laptop kernel: [ 6293.878742] ACPI: Critical trip point
May  6 21:23:50 chris-laptop kernel: [ 6293.878753] Critical temperature reached (97 C), shutting down.
May  6 21:23:50 chris-laptop init: tty4 main process (4808) killed by TERM signal
May  6 21:23:50 chris-laptop init: tty5 main process (4809) killed by TERM signal
May  6 21:23:50 chris-laptop init: tty2 main process (4811) killed by TERM signal
May  6 21:23:50 chris-laptop init: tty3 main process (4813) killed by TERM signal
May  6 21:23:50 chris-laptop init: tty6 main process (4815) killed by TERM signal
May  6 21:23:50 chris-laptop init: tty1 main process (6981) killed by TERM signal
May  6 21:23:50 chris-laptop pulseaudio[7115]: module-gconf.c: Unable to read or parse data from client.
May  6 21:23:52 chris-laptop gdm[6567]: WARNING: main daemon: Got SIGABRT. Something went very wrong. Going down! 
May  6 21:24:20 chris-laptop avahi-daemon[5451]: Got SIGTERM, quitting.
May  6 21:24:20 chris-laptop avahi-daemon[5451]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.1.100.
May  6 21:24:20 chris-laptop kernel: [ 6324.178041] eth2: set allmulti
May  6 21:24:22 chris-laptop rpc.statd[4673]: Caught signal 15, un-registering and exiting.
May  6 21:24:24 chris-laptop kernel: [ 6328.268293] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  6 21:24:25 chris-laptop mountd[6256]: Caught signal 15, un-registering and exiting.
May  6 21:24:25 chris-laptop kernel: [ 6329.575336] nfsd: last server has exited
May  6 21:24:25 chris-laptop kernel: [ 6329.575341] nfsd: unexporting all filesystems
May  6 21:24:26 chris-laptop exiting on signal 15

---

### Post by tonicat on 2008-05-08
I had also this problem. Some programs -such as Firefox, when viewing videos in youtube- increase my cpu frequency to the maximum value (in my Pentium M Centrino  laptop, 1.7 GHz), the machine got overheated and eventually caused a shutdown. In an emergency, I had to manually slow down cpu frequency with 

$ cpufreq-selector -f 798000

That effectively causes a fixed cpu frequency of 798 MHz that works well enough for me. No the ideal solution, but it works. Hopefully the freq scaling will be fixed soon.

---

### Post by excogitation on 2008-05-09
Bal_Zac: You could have certainly been right about your assumption - I didn't like your approach though.

tonicat: We'll - if you like going 30 in your "Ferrari" that will work for you.

Back to the problem:
There are numerous posts on temperature problems (especially with laptops) on this forum.

I haven't seen "the" solution - apart from going back to Gutsy - but
you might consider undervolting.
That definitely helps - but this doesn't fix the cause.

You could also try switching to cpufreqd (I assume you're running powernowd)
and see if you're pleased with the outcome.

---

### Post by cmavr8 on 2008-05-09
Guys, thanks for the replies..

Sorry I didn't make it clear earlier, but my scaling works fine..
It's just that I always need to have my cpus at 1ghz (50% speed) to avoid reboots.

Even if I leave it to ondemand, the system overheats and reboots...

**So, best thing for me would be speeding up the Fan!**

---

