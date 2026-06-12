---
title: "Overheating - Troubleshooting Tactics?"
date: 2012-09-10
forum: Hardware
---

### Post by brickedone on 2012-09-10
Anyone have any suggestions on troubleshooting tactics for an overheating problem?

**Hardware** - *Via M'Serv 2100*
CPU: VIA Nano processor (1.3+GHz @ 1.6GHz, 64-bit, 1MB, 800MHz FSB)
Chipset: VIA VX800 Unified Digital Media IGP chipset
OS: Ubuntu 12.04 LTS

**Problem**
It's supposed to just sit quietly, manage downloads (SABnzbd w SickBeard/CouchPotato/Headphones) and serve files (samba), but it keeps overheating and freezing up on me overnight (doesn't shut down, just freezes in overheated state). No idea what could be driving heavy resource utilization and causing the overheating problem.

**Troubleshooting Idea**
Would love to find a tool that (a) tracks system resource usage over time, (b) tracks temperature over time, (c) saves a user-friendly log regularly, (d) can show me a graph of temperature and system resource usage (processor, memory, storage read/write, other?) by top [e.g. 1/3/5/10/any] progs/processes in the user defined interval leading up to the last reported log entry. Ability to set user-defined email warning and shutdown temps would be helpful in the meantime.

At least that's how I'm thinking to attack the problem. Suggestions welcome...

**Packages**
The system does have embedded sensors and I have installed and configured sensors-detect, lm-sensors and ssmtp.

I have read about sensors-applet, psensor and computertemp, but it is not clear to me whether any of these packages log temperatures and high resource progs/procs vs system time for future retrieval and analysis and have the ability to set temp warnings and temp actions e.g. shutdown (only computertemp app description states ability to log temperatures).

Thanks for thoughts/suggestions.

---

### Post by TheFu on 2012-09-10
Write a script that runs **sensors **every 5 minutesand puts that data into a file.  Use a system monitor solution like SysUsage or Monitex

Some helpful articles:
* [http://www.linuxjournal.com/article/2396](http://www.linuxjournal.com/article/2396)
* [http://sixrevisions.com/tools/10-free-server-network-monitoring-tools-that-kick-***/](http://sixrevisions.com/tools/10-free-server-network-monitoring-tools-that-kick-***/)
* [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

Using those tools, like top, you can record what's in the process table periodically.  Total system monitor tools don't generally go to the specific process level.

For a media center device, the likely culprit is the media center GUI program itself.  XBMC was designed for xbox devices and manually refreshes the screen at a high rate, sucking up CPU.  This high CPU load has been mentioned many times on the XBMC forums, but it is core to the overall design so they've never considered altering it.  Setting a sleep or shutdown timer is probably the best answer for most people.  I find that XBMC uses more CPU than playback of a 1080i movie because the movie playback happens all in the GPU hardware, not the CPU.

And you could put a slow moving fan inside the case to suck air out.  Adding $2 in diodes or resisters to the fan power line will help control the noise level better.

I don't think any monitors displaying on the screen in real-time is very useful. That adds more workload to the already hot components and you can't review it later. You need log files or  better, rrd data.

I don't know what this device is that you have.  I just built a new XBMC box a few weeks ago for $130. Most of the heat was coming from the PSU, so a new 90W "picoPSU" was ordered.  97% efficient means almost no heat inside the case.  the PSU has a laptop-like floor wart, however.  It is completely silent and worth the extra $40 (total price now $170).  It plays everything - everything (except netflix or sliverslight).

For emails ... that is pretty easy too.  Have a script to watch the output from **sensors** and if the threshold is hit, send an email.  Sending email from a UNIX machine is trivial.  Install **postfix** and some simple CLI email program like **Mail**.  The email doesn't need to leave the machine, unless you need it somewhere else.

I don't know of any all-in-one tool that does everything what you want.  That isn't the Linux-way.  Linux is about having small tools that do one thing that you can put together. There are some tools that come close to doing everything, but those are complex to setup and harder to maintain.  

If all you really need is the temperatures and top processes, that is 2 scripts run every 5 minutes. ```

sensors > /tmp/heat.$datestamp
top > /tmp/processes.$datestamp
```
Anything more over complicates the issue.  You can parse those files and drop the relevant data into a spreadsheet pretty easily to make charts too.

BTW, I was searching for a monitoring tool that I'd just seen last week - monitex or something like that, but I couldn't find it.  I use SysUsage myself, but this is system-level monitoring, not really what you seem to want.

---

### Post by brickedone on 2012-09-10
TheFU - Thank you for such a solid, on-point response.  Not sure I really know how to implement everything - scripts for writing the temp and procs log files, script to query sensors and send email or shutdown at temp thresholds - but it sounds like exactly the right solution.  

I was reading a few howto's that do some of these steps (email notification or shutdown at temp level using sensors), but got bogged down in details (what temp should I set for warning vs shutdown, integration with ssmtp, etc).  Guess I have some more reading to do.

I don't have XBMC installed on the M'Serv box as I thought it would be too resource intensive for the limited server hardware.  Instead I share the media drive via samba and run xbmc from my desktop (Win 7), which has much better hardware.  So I don't think XBMC is the culprit.  I don't want to run the download manager from the desktop.

Thanks again

---

### Post by TheFu on 2012-09-10
Scripting is easy.  Whatever you type at the bash prompt, put into a script file, change the permissions to be executable (chmod +x FILE.sh) and you can run it.  That will get you started.

When you need more, [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) should cover just about anything.  I'm still learning how to make my scripts bulletproof by trapping signals, but hardly any real-world scripts are that failure prone.
```

#!/bin/bash
datestamp=`date "+%F-%T"`
SENSOR_OUT=/tmp/heat.$datestamp
TOP_OUT=/tmp/processes.$datestamp

sensors > $SENSOR_OUT
top > $TOP_OUT 
```Simple.  See how the datestamp will be identical for all the files from the same script and not the actual exact timestamp? That is by design.  You can add commands to look inside the files for certain temperatures.

```
$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +43.5°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)
```is the output from my XBMC box a few seconds ago.  This tells me that I need to look between "temp1:" and "(" for the current temperature.  That's easy with **grep** or **sed**.  There's probably a way to do it inside **bash** too.  Yep - an example [http://tldp.org/LDP/abs/html/parameter-substitution.html#EX7](http://tldp.org/LDP/abs/html/parameter-substitution.html#EX7)  Pattern matching is one of the most powerful things in scripting.
```

    A            B          C .....
temp1:        +43.5°C  (high = +70.0°C)
```We're looking for the "B" field.  Since I'm a perl guy, at this point I'd switch to Perl since it is more convenient for me and easier for me to handle.  Bash can do very complex stuff too, but I've never learned much more than this or what you can see in /etc/init.d/ files.

Be certain that you tell bash whether the contents are characters or numbers. It can handle numbers and will perform calculations and numeric comparisons, if you ask.

Anyway, I hope this all helps.  I'm certain there are lots of beginning bash scripting guides, but really just putting what you'd type into a terminal is the starting point for all scripting.

---

