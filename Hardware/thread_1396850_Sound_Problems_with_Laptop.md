---
title: "Sound Problems with Laptop"
date: 2010-02-02
forum: Hardware
---

### Post by ThomAthom on 2010-02-02
Running Jaunty

Hello... I am new to Ubuntu and having problems with a windows native sound-card.  I've read a ton of reasons to use Ubuntu and would like to continue to use it but if I can't get the sound to work I have an issue.  The most recent article has had me down a rabbit hole for about an hour.  I know it is something that I am doing wrong but what it could be I am not sure.  Here is the documentation that I've read:

This is the model I am using:
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

Debugging Sound Problems
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

   1. Basic troubleshooting
         1. Identifying your hardware
A.
Command used -->lspci -v | less
Outflow of data ----> 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Device 2066
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
Outflow of data ----> 


B.  Attempting to grep the sound cards
        Greps did not work in a console

Tried:
grep "^Codec\|^Vendor Id\|^Subsystem Id\|^Revision Id" /proc/asound/card*/*codec*{,/*} | grep -B2 -A1 $(lspci -nv | grep -A1 0403 | grep Subsystem | sed 's/://g' | awk '{ print $2 }')

C. Tried to put the commands into a script sh.
        Puting command into a sh file

Got the error both times
grep: /proc/asound/card*/*codec*{,/*}: No such file or directory

-----  This is as far as I have gotten...  

Here are the rest of the steps to go through

         2. Preliminary checks
         3. Checking volume levels
         4. Checking sound device assignment
         5. Checking permissions and resources
   2. Reporting Sound Bugs
         1. Automatic Sound Information Collection
   3. Further sound troubleshooting


If ANYONE can direct me somewhere so that I can get the sound to work on my laptop that would be super fantastic!

Thanks,
  Thom A Thom

---

### Post by ThomAthom on 2010-02-03
Updated to Karmic Koala... and still the sound doesn't work... Probably due to the modem or something stupid like that... any suggestions would be super.

---

### Post by IcarusR on 2010-02-03
Sorry posted to wrong thread.

Fee bump !

---

