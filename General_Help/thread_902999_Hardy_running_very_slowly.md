---
title: "Hardy running very slowly"
date: 2008-08-27
forum: General Help
---

### Post by Seamyst on 2008-08-27
I run Hardy on my 1st-gen MacBook with no problems.  However, I just acquired an old Gateway 300S desktop (roughly six years old), and Hardy is running very slowly on the Gateway.  I have System Monitor open and with the computer just sitting there, no programs running except System Monitor, CPU usage is at 30%.  Opening any program, even something as simple as TextEdit, shoots the usage up to 100% while it's loading.  Opening OpenOffice Writer or Amarok, and then letting them sit, brings the usage up to 50-60%.  Opening Firefox and letting it sit at a page that doesn't refresh itself (like, for instance, google.com) has a CPU usage of 60-70%.  If it's loading any page, however, usage goes up to 100%.

Is this normal for an older computer?  Is it a problem with the Gateway series?  Would I get better usage if I downgraded?  If so, what version should I install?  I should note that I got the computer with 512MB of RAM and upgraded it to 1GB - there's no discernible change in speed.  All updates have been applied.

Specs:
Memory: 1009.4 MiB
Processor:  Intel Celeron CPU 1.80 GHz

---

### Post by mssever on 2008-08-27
> **Seamyst said:**
> I run Hardy on my 1st-gen MacBook with no problems.  However, I just acquired an old Gateway 300S desktop (roughly six years old), and Hardy is running very slowly on the Gateway.  I have System Monitor open and with the computer just sitting there, no programs running except System Monitor, CPU usage is at 30%.  Opening any program, even something as simple as TextEdit, shoots the usage up to 100% while it's loading.  Opening OpenOffice Writer or Amarok, and then letting them sit, brings the usage up to 50-60%.  Opening Firefox and letting it sit at a page that doesn't refresh itself (like, for instance, google.com) has a CPU usage of 60-70%.  If it's loading any page, however, usage goes up to 100%.

Is this normal for an older computer?  Is it a problem with the Gateway series?  Would I get better usage if I downgraded?  If so, what version should I install?  I should note that I got the computer with 512MB of RAM and upgraded it to 1GB - there's no discernible change in speed.  All updates have been applied.

Specs:
Memory: 1009.4 MiB
Processor:  Intel Celeron CPU 1.80 GHz
Xubuntu is good for older computers. But what's taking up the 30% CPU? System Monitor itself takes up quite a bit, especially in Hardy. My favorite app for these purposes is htop.

Firefox is a CPU hog. Consider using Epiphany.

---

### Post by lswb on 2008-08-27
That system should run fine, I get good performance from hardy on a Pentium 3 650Mhz with 512MB memory. Run the "top" command in a terminal (or a similar program)  and see if there is a particular program hogging memory. Depending on the video system of the gateway, you may want to try open Main Menu/System/Preferences/Appearance/Visual effects and select the "none" setting. ANother thing that will make any system run slow is if it is using the VESA video driver instead of one for the specific video adapter installed in the system.

---

### Post by Seamyst on 2008-08-28
I installed Xubuntu over my existing Ubuntu installation, but it seems to have made no difference.  Should I do a fresh install instead?

Running top in Terminal brings up something interesting - approximately 25% of the CPU usage is taken up with Xorg.  Any ideas why that would take up so much?  I haven't even edited it.

**lswb** - How would I determine what video driver is in use?  If it's VESA, how would I change it to one for my specific video adapter (which is on the motherboard)?

---

### Post by Crafty Kisses on 2008-08-28
Post results of > top

---

### Post by lswb on 2008-08-28
I think the command "xvinfo" run in a terminal will tell you a general vender name of some kind, or mention VESA in the first few lines of output. (Run as "xvinfo|more" to keep it from scrolling off the screend) You can also take a look at /var/log/Xorg.0.log for a driver name and to see if there are any errors reported when X starts up. 

For reconfiguring, the first thing I would recommend trying for hardy is booting into recovery mode and selecting the "repair X server" or similarly worded option, or from a command line,  

"sudo dpkg-reconfigure -phigh xserver-xorg"

Do you know what video adapter is installed in the system? look at the output of the lspci command for an adapter name and you can try googling or searching the forum for specific help on that adapter.

---

### Post by Seamyst on 2008-08-30
@ **Codename**:
```
top - 19:49:28 up 1 day, 21:36,  2 users,  load average: 1.31, 0.93, 0.49
Tasks: 105 total,   2 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 35.9%us,  4.0%sy,  0.0%ni, 60.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1033644k total,   830608k used,   203036k free,    52964k buffers
Swap:  1502036k total,    39588k used,  1462448k free,   450220k cached
```

@ **lswb**:  According to xvinfo, it's an Intel Video Overlay.  VESA isn't mentioned at all, so that's good.  Looking at lspci shows (among other lines):
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

That's what I'm looking for, yes?  Sorry for the dumb question, but it's been awhile since I had to deal with non-Mac parts on my personal computer.

---

### Post by retrovertigo on 2008-08-30
Where's the rest of the top output?  Please run top again and post the first several lines after the "swap" line.

---

### Post by Seamyst on 2008-08-30
Sorry - I couldn't figure out how to copy the rest of it before.  Here it is:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12017 jessica   20   0  229m  94m  26m R  4.0  9.4   6:52.97 firefox            
11696 root      20   0  258m  46m 7144 S  3.7  4.6   8:19.22 Xorg               
12182 jessica   20   0 75804  18m  11m S  2.0  1.8   0:00.92 gnome-terminal     
11879 jessica   20   0 15724 5616 4428 S  0.7  0.5   0:06.46 gnome-screensav    
11951 jessica   20   0 18236 9808 6120 S  0.7  0.9   0:04.56 emerald            
12202 jessica   20   0  2308 1108  852 R  0.7  0.1   0:00.06 top                
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.80 init     
```

One thing I've noticed is that Xorg is much more resource-hogging shortly after I restart X or reboot.  Now, maybe an hour and a half to two hours later, it's much less so.  The others seem to be about the same regardless of when I run top, give or take a few percentage points.

---

### Post by mb_webguy on 2008-08-30
Xorg is also going to briefly use more resources when you switch from one window or workspace to another...

However, I have noticed several threads on this board in the last week that involve Xorg using an inordinate amount of system resources over longer periods of time than can be explained by normal operation.  Unfortunately, I haven't read anything about causes or solutions.

---

### Post by Seamyst on 2008-08-30
> **mb_webguy said:**
> Xorg is also going to briefly use more resources when you switch from one window or workspace to another...

I don't switch workspaces unless I accidentally scroll while the mouse pointer's on the desktop and not in Firefox or another program.  Oh well... looks like it may not be just me, then.  I'm trying to download Xubuntu again (downloading via torrent resulted in a corrupt or incomplete ISO, for some reason) and will try a clean install.

*Edited for clarity.*

---

### Post by retrovertigo on 2008-08-30
> **Seamyst said:**
> Sorry - I couldn't figure out how to copy the rest of it before.  Here it is:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12017 jessica   20   0  229m  94m  26m R  4.0  9.4   6:52.97 firefox            
11696 root      20   0  258m  46m 7144 S  3.7  4.6   8:19.22 Xorg               
12182 jessica   20   0 75804  18m  11m S  2.0  1.8   0:00.92 gnome-terminal     
11879 jessica   20   0 15724 5616 4428 S  0.7  0.5   0:06.46 gnome-screensav    
11951 jessica   20   0 18236 9808 6120 S  0.7  0.9   0:04.56 emerald            
12202 jessica   20   0  2308 1108  852 R  0.7  0.1   0:00.06 top                
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.80 init     
```

One thing I've noticed is that Xorg is much more resource-hogging shortly after I restart X or reboot.  Now, maybe an hour and a half to two hours later, it's much less so.  The others seem to be about the same regardless of when I run top, give or take a few percentage points.

Was the CPU usage still up at 30+% when you most recently ran top?  What I would do is run top whenever you notice it running slowly, or if it runs slowly when you do certain things, then open a terminal and run top, then do whatever it was you were going to do and monitor what happens.

---

### Post by lswb on 2008-08-30
The laptop I'm using right now has an Intel 80855 graphics chip, and a 1.4MHz Pentium M, (a Gateway 200ARC as a matter of fact) so I imagine your laptop should have similar performance if everything is working OK. Besides, I get acceptable performance on a much older system with only a 650MHz Pentium 3. You can check for sure what driver your system is using by examining /var/log/Xorg.0.log Look for some lines something like this:

(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device

You might see "i810" instead of "intel" at the start of the 1st line. Either should provide acceptable performance but the "intel" driver is newer and supposedly better.


Let me ask you, though; are you having performance related problems, or are you just concerned about the high cpu %. As mb_webguy pointed out, the cpu % used by X will shoot up momentarily when opening a window, starting another program, or even just moving the mouse around quickly. If there is no slowness in response, slow graphics, etc. I wouldn't worry about it.

---

### Post by Seamyst on 2008-09-02
I've had Xubuntu installed and running for three days now and it's going just fine!  It's every bit as fast as my newer MacBook and I figured out the two main problems I was having in switching over from Ubuntu (namely, themes and adding launchers).  Thanks for all your help!

---

