---
title: "How to put external HDD to sleep?"
date: 2023-03-27
forum: Hardware
---

### Post by egshen on 2023-03-27
Hi,

In the Disks utility, I've set the standby settings to 10 mins but the disk never stops spinning, unless I unmount it AND unplug it.

Quitting all programs doesn't help either so I don't know what keeps the disk busy.

Any idea? (I'm relatively new to Ubuntu but never had this issue on Mac OS).

---

### Post by TheFu on 2023-03-27
Check out hdparm for commands and options to control different disk parameters.  Not all parameters can be controlled for every spinning drive. Sometimes specific drive models don't support them and sometimes the connection interface doesn't.  For example, USB connections ARE NOT THE SAME as SATA, eSATA or SAS connections.  The command sets for USB is not as complete as for the other connection methods. 

The only issues I've had with MacOS were ... wanting to throw the machine against a wall when it wouldn't let me do things. Thankfully, I was able to return it before that happened. I couldn't take the frustration. The key for you and for me is that Linux isn't MacOS AND MacOS isn't Linux. They are very different OSes with completely different philosophies (and prices).

---

### Post by egshen on 2023-03-27
Thanks for the reply.

I'd never heard of hdparm until today. I've had a quick look but I'm not sure what I'm supposed to do with it :-?

As for MacOS, yes I agree. What I meant is that I didn't have the same issue so I don't think it's problem with the disk (as some people suggested to me). And yes it's a USB drive.

---

### Post by TheFu on 2023-03-27
hdparm is an admin tool, so it is fully documented in the system manpages.  Learning to read manpages is a core skill for any Linux/Unix user.

From the hdparm manpage on my system (which is probably different than yours):
```
       -B     Get/set Advanced Power Management feature, if the drive  supports
              it.  A  low  value  means  aggressive power management and a high
              value means better performance.   Possible  settings  range  from
              values  1  through  127  (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).  The highest  degree
              of  power  management  is  attained  with a setting of 1, and the
              highest I/O performance with a setting of 254.  A  value  of  255
              tells  hdparm  to disable Advanced Power Management altogether on
              the drive (not all drives support disabling it, but most do).
```
**Always** use the local manpage, since commands, options, change from package to package, so the only way to ensure you are using the documentation for the same version of the program on your system is to use the manpage on-your-system for insights.  For decades, sometimes nothing changes with a command, but then there could be huge changes ... I know **sort** has changed drastically in the last 15 yrs, adding many options that are much more convenient than before.

If the manpage isn't sufficient documentation, you can search these forums for examples using that tool ... and the internet. Be careful using examples, since they may be for a different OS and almost always will be for a different version of the command, but they do provide a way to check if the example options/usage can work on your system. 

[https://explainshell.com/](https://explainshell.com/) is a handy tool if you just have a command. It will look up the options in the manpages that website has and like diagramming a sentence for grammar, the relevant manpage options will be show.

But with USB connections especially, it may not be possible to send the required command to the disk. It depends on the USB controller - both in the computer and connected to the HDD. This assumes the HDD will honor the commands too, which isn't always the situation.  All you can do is to try and see if the desired settings work or not.

---

### Post by egshen on 2023-03-28
Thanks!

---

