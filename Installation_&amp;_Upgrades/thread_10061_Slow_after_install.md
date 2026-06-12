---
title: "Slow after install"
date: 2005-01-04
forum: Installation &amp; Upgrades
---

### Post by larryn06780 on 2005-01-04
I just did the clean install onto a PIII 800 machine with 128 Mb ram and a 10Gb HDD. The install went well and it all the hardware functions (mouse, Video, Network, sound card, and all drives). The problem that I have is that EVERYTHING that runs is incredibly slow to load. When I open a terminal window it takes 1 minute to get the window with a prompt. OpenOffice takes 3 minutes and 56 seconds to open the word processor, and Mozilla takes 1 minute and 16 seconds to open the browser window. Looking at the system requirements for the install I should be well within limits. Is this purely a RAM issue or is something else going on? I am not opposed to re-installing with more minimal components if that will help. Any assistance would be appreciated.
Thanks...........

---

### Post by rbran100 on 2005-01-04
What % of the ram is taken up on boot?  i know i am using every bit of mine and i have more than you.  But i guess it just depends on what you have running concurrently.  does it speed up as you kill stuff off?   :-&

---

### Post by larryn06780 on 2005-01-04
When the system is sitting there with nothing else running after boot up the system monitor says I am using about 60 Mb of physical memory and 40Mb of swap.

---

### Post by larryn06780 on 2005-01-06
I have a Maxstor 15 Gb drive set to be primary master and when I issue the " sudo hdparm -t /dev/hda " command it comes back with about 240Kb/sec of data read every time. The option jumper on the drive is set to master as well. Everything else with the install went well and runs o.k.  it's just with this HD performance it takes forever to load up anything. Any suggestions would be greatly appreciated.
The PC is;
HP Kayak XM600 with 128 Mb RAM ( PIII 800 Mhz )

---

### Post by wallijonn on 2005-01-06
240KB is too slow. I think it's time for you to start looking at /var/log/kern.log

Here's my WD80GB: Timing buffered disk reads:   80 MB in  3.05 seconds =  26.26 MB/sec

---

