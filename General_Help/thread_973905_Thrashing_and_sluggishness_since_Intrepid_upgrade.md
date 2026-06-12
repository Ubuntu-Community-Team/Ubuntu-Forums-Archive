---
title: "Thrashing and sluggishness since Intrepid upgrade"
date: 2008-11-07
forum: General Help
---

### Post by richgood on 2008-11-07
Hi,

I recently updated to Intrepid Ibex and have been suffering from serious thrashing and sluggishness, the machine is a typical Intel P4 with a 1G RAM and I had no problems under Hardy.

When running top I notice three instances of ld-linux.so.2 running chewing up all my CPU:
```
top - 12:07:10 up 2 days, 23:20,  2 users,  load average: 5.65, 5.08, 4.66
Tasks: 158 total,   5 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s): 53.0%us, 46.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1025212k total,  1009068k used,    16144k free,    31296k buffers
Swap:  1132540k total,   341964k used,   790576k free,   155352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                          
 5633 richard   20   0  110m  25m  20m R   40  2.5 811:39.48 ld-linux.so.2                                                    
20327 richard   20   0  193m  74m  21m R   39  7.4   2001:50 ld-linux.so.2                                                    
 8277 richard   20   0  105m  27m  18m R   39  2.7 643:09.86 ld-linux.so.2                                                    
 5896 root      20   0  620m 224m 8144 S   35 22.4 444:11.63 Xorg                                                             
 6298 richard   20   0 32296 3940 3148 S   20  0.4 276:49.81 pulseaudio                                                       
 8198 richard   20   0  966m 179m  28m R   14 17.9 198:42.88 firefox                                                          
 9388 richard   20   0  158m  33m  15m S    5  3.3 252:00.31 amarokapp     
```

Any ideas on why this is and how to fix it?  Besides the Intrepid upgrade and installing Open Office 3 I've made no major changes since the perfectly working Hardy installation.

Regards,
Richard.

---

### Post by richgood on 2008-11-07
Hi,

Found a solution that seems to be working at:

[http://ubuntuforums.org/showthread.php?t=754944](http://ubuntuforums.org/showthread.php?t=754944)

Seems there is an issues with Acrobat Reader 8 calling the ld-linux.so.2 process that devours the CPU.

By installing package lsb, Acrobat uses this package instead of ld-linux.so.2 and seems to have sorted out the problem.

Richard.

---

### Post by Bott on 2008-11-07
I was having similar problems with sluggishness with 8.10 starting with the 8.10 beta installed as an upgrade to 8.04.  This was particularly bad with Nautilus viewing streaming videos or anytime a wave or other sound file was played.  Getting rid of pulseaudio fixed it all for me.
[http://ubuntuforums.org/showthread.php?t=963914](http://ubuntuforums.org/showthread.php?t=963914)

---

