---
title: "Hardware problem"
date: 2012-01-23
forum: Hardware
---

### Post by Azyx on 2012-01-23
A friend gave me a HP-machine with the motherboard mcp61pm-hm with a AMD X2 3.0GHz (6000+) processor, cos he had have problems with blue-screen and reboot on windosvista. Of cos I'm using Ubuntu (10.04LTS for now). I'm don't like to throu away thing, little of a recycling man^^, and it also the most powerful comuter I ever owned :). I found that one memory slot was broken so I leave that and run memtest86+ for 12H with no broblems :) But now I find out that I'm occasionally get logged out or the computer reboot.

I's there any test for the motherboard/processor to see where the damage are? looking in logs or something to what happen when the computer log-out or reboot?

May a upgrade of BIOS may help?

---

### Post by dargaud on 2012-01-23
Remove as much hardware as possible (all PCI/graphic cards, all memory but one, all HD, etc). Boot a liveCD and run a stress-test app. See it it fails. If it doesn't, start putting pieces back. And check your fans.

Oh, and try a different power supply: that's often the culprit in random reboots.

---

### Post by Basher101 on 2012-01-23
please write in proper english, jargon is kinda hard to read..

anyways, looking in the logs should give you hints on where the problems are. I doubt a BIOS upgrade will do anything significant, unless its bugged from a last update (which does not seem to be the case).

regards

---

### Post by Azyx on 2012-01-23
> **dargaud said:**
> Remove as much hardware as possible (all PCI/graphic cards, all memory but one, all HD, etc). Boot a liveCD and run a stress-test app. See it it fails. If it doesn't, start putting pieces back. And check your fans.

Oh, and try a different power supply: that's often the culprit in random reboots.

Do you now any stress-test?

---

### Post by Azyx on 2012-01-23
> **Basher101 said:**
> please write in proper english, jargon is kinda hard to read..

anyways, looking in the logs should give you hints on where the problems are. I doubt a BIOS upgrade will do anything significant, unless its bugged from a last update (which does not seem to be the case).

regards

I never now how I should spell 'cos' or is there more that are bad English?

Ok, about the BIOS. Waithing for next beboot, but when I disconnected the onboard NIC it has not happend :)

---

### Post by Basher101 on 2012-01-23
instead of "cos" please use "because"

and i suggested a look in the logs, i never said anything of disconnecting any hardware, _dargaud_ suggested it. 
You should follow his advice once you looked at the logs and located the problem though...

---

### Post by Azyx on 2012-01-23
> **Basher101 said:**
> instead of "cos" please use "because"

and i suggested a look in the logs, i never said anything of disconnecting any hardware, _dargaud_ suggested it. 
You should follow his advice once you looked at the logs and located the problem though...

Ok. I know, but the disconnection of the NIC was accidentally. I don't have any cable in the place I have computer now (VNC to It before) Think I need to put it in again to get any reboot....

---

### Post by Azyx on 2012-01-23
> **Basher101 said:**
> instead of "cos" please use "because"

and i suggested a look in the logs, i never said anything of disconnecting any hardware, _dargaud_ suggested it. 
You should follow his advice once you looked at the logs and located the problem though...

Now I get a frozen system, during streaming from youtube throu wireless connction. Where in the all logs do I look?

---

### Post by Basher101 on 2012-01-23
google can be your friend

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

i have no experience with log files whatsoever, so when you discovered something i won't be much of a help :/


good luck on fixing your problems


regards

---

### Post by dargaud on 2012-01-23
> **Azyx said:**
> Do you now any stress-test?

```
$ aptitude search stress
p   stress                                                 - A tool to impose load on and stress test a computer system      
p   stressapptest                                          - stress test application for simulating high load situations     

$ aptitude search bench
p   dbench                                                 - The dbench (disk) and tbench (TCP) benchmarks                   
p   lmbench                                                - Utilities to benchmark UNIX systems                             
p   lmbench-doc                                            - Documentation for the lmbench benchmark suite                   
p   namebench                                              - DNS benchmark utility                                           
p   octave-benchmark                                       - code to benchmark speed of Octave                               
p   php-benchmark                                          - Framework to benchmark PHP scripts or function calls            
p   pipebench                                              - Measures the speed of stdin/stdout communication                
p   render-bench                                           - Benchmark for the XRender extension                             
p   svn-workbench                                          - A Workbench for Subversion                                      
p   sysbench                                               - Cross-platform and multi-threaded benchmark tool                
p   tiobench                                               - Threaded I/O bench for Linux                                    
```

---

### Post by matt_symes on 2012-01-23
Hi

A couple of hardware testing distributions (There are others).

[http://www.inquisitor.ru/about/index.html](http://www.inquisitor.ru/about/index.html)

[http://www.stresslinux.org/sl/](http://www.stresslinux.org/sl/)

You can see the software they use if you don't want a full blown distribution.

I can offer no opinion on them as i have not had the chance to use them yet. I will be in the next couple of days.

Kind regards

---

### Post by MoreOrLess on 2012-01-23
Sounds like it could be overheating when using flash/youtube. Monitor CPU temps.

---

### Post by varunendra on 2012-01-24
> **dargaud said:**
> ... run a stress-test app. See it it fails.

> **matt_symes said:**
> A couple of hardware testing distributions (There are others)...
I recommend [HBCD]("http://www.hirensbootcd.org/download/"). It has some very nice testing tools (besides tons of other useful stuff). Testing from a minimal live session also has the advantage of being free from any software configuration issues that may be existing on the installed OS.

---

