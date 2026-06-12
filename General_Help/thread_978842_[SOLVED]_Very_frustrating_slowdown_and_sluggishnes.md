---
title: "[SOLVED] Very frustrating slowdown and sluggishness"
date: 2008-11-11
forum: General Help
---

### Post by tipiglen on 2008-11-11
Quite frequently my system becomes unresponsive and sluggish. 
I have Firefox 3 running most of the time, and Flash installed

Just sometimes the whole thing seems to go on holiday, not a total freeze-up but that sometimes happens (a lot less often).  Eventually it comes back, and does whatever clicks and touchpad movements tried in frustration while waiiting, so the screen jumps up and down and firefox probably switches (finally) to another tab....I'm sure some folk out there know what I'm describing.

It all began with Hardy.  Here is a copy of the top of a top display:

top - 18:22:32 up  1:42,  2 users,  load average: 0.83, 0.39, 0.37
Tasks: 119 total,   2 running, 115 sleeping,   2 stopped,   0 zombie
Cpu(s):  4.5%us,  1.1%sy,  0.0%ni, 94.0%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    514112k total,   501460k used,    12652k free,     4100k buffers
Swap:        0k total,        0k used,        0k free,   121100k cached


What I note is that almost ALL of my RAM seems to be constantly occupied.  Is this the problem?  Is it just that Hardy is so new and modern that it assumes nobody would be so bold as to try to get by with only half a gig of RAM?

Any suggestions as to how to get my laptop back to the slick operator it was, or should I just go back to an earlier release...?

In frustration
ed

---

### Post by GROMS on 2008-11-11
> **tipiglen said:**
> Quite frequently my system becomes unresponsive and sluggish. 
I have Firefox 3 running most of the time, and Flash installed

Just sometimes the whole thing seems to go on holiday, not a total freeze-up but that sometimes happens (a lot less often).  Eventually it comes back, and does whatever clicks and touchpad movements tried in frustration while waiiting, so the screen jumps up and down and firefox probably switches (finally) to another tab....I'm sure some folk out there know what I'm describing.

It all began with Hardy.  Here is a copy of the top of a top display:

top - 18:22:32 up  1:42,  2 users,  load average: 0.83, 0.39, 0.37
Tasks: 119 total,   2 running, 115 sleeping,   2 stopped,   0 zombie
Cpu(s):  4.5%us,  1.1%sy,  0.0%ni, 94.0%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    514112k total,   501460k used,    12652k free,     4100k buffers
Swap:        0k total,        0k used,        0k free,   121100k cached


What I note is that almost ALL of my RAM seems to be constantly occupied.  Is this the problem?  Is it just that Hardy is so new and modern that it assumes nobody would be so bold as to try to get by with only half a gig of RAM?

Any suggestions as to how to get my laptop back to the slick operator it was, or should I just go back to an earlier release...?

In frustration
ed
How did you get the "top of a top display"?
I've just noticed a slugishness with this site.

---

### Post by Cracauer on 2008-11-11
You are using the NVidia binary driver?

And please stir around with the mouse between firefox and something else and tell us how big firefox and "X" are according to top(1).

---

### Post by Cracauer on 2008-11-11
Wait, you have 512 MB and no swapspace and use firefox?

You need to add some swapspace, man.

---

### Post by tipiglen on 2008-11-11
1. (Groms) You get top by typing top into a terminal.

2.  ( Cracauer) I just looked at the partition editor and found the swap partition was there, but it offered ""swapon" and now my "top" shows swap in use!!!  I feel a bit stupid, but have no idea how it got turned off....doh!  Thanks! 

When the thing has gone 'on vacation', the pointer sometimes gets so slow I can't toggle onto another application (or even get the 'top' terminal to show....

But, now that I've got swap working again, we'll see   Thanks again

Virtual drinks are on me!  Slainte!
ed

---

### Post by tipiglen on 2008-11-11
On rebooting, I find the swap partition has reverted to swapoff.  Any suggestions?  

Meanwhile, I've switched it back on, and will check out /etc/fstab. Nothing obvious there.  Did a soft reboot (ctrl/alt/backspace) and swap is still on, so I'm still in the dark.

Any ideas, anyone?

A puzzled ed

---

### Post by aaaantoine on 2008-11-11
I'll be watching this thread because I, too, am having issues with unresponsiveness.  It especially seems to occur when the CPU is in use by a not nice process (I specify not nice because Folding@Home doesn't appear to slow anything down).

Occasionally my screen will freeze; sometimes for a second, sometimes for several minutes.

---

### Post by tipiglen on 2008-11-12
I think I've solved at least aprt of tthe problem of swap not being activated at boot.

I had to edit /etc/fstab because it seems the UUID of my swap partition was wrong (possibly to having re-sizing the partition???- don't remember)

I simply edited fstab to use the /dev/sda4 identifier rather than UUID.  Now swap is on after bootup.

I found this idea here:
[http://ubuntuforums.org/showthread.php?t=951269&highlight=swap+problem](http://ubuntuforums.org/showthread.php?t=951269&highlight=swap+problem)

Thanks to all, and we'll see if this fully solves my problem (no slowdowns so far)

patient ed

---

### Post by mkvnmtr on 2008-11-12
I seem to be having the same problem. It started yesterday. Twice it has frozen in Firefox and it seems if I wait long enough it will work itself out. I am not able to go to top but I do see max cpu usage. This is rare with my Firefox. It has been very fast and low cpu usage. Today I am running with less windows open and have not had the problem again. Now to the point of my post. I checked my swap and it is on. It doesn't turn off on the restart. Maybe it is another problem. Please keep us informed.

---

### Post by tipiglen on 2008-11-14
Sad to say, though less frequent, I'm still getting slowdowns and 'freezes', Usually the disk access light is on continuously when thiis happens,  and now I'm getting spontaneous shutdowns.

Typical "top":

top - 18:22:52 up 8 min,  2 users,  load average: 0.50, 0.78, 0.49
Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.7%us,  1.9%sy,  0.0%ni, 73.0%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    514112k total,   505068k used,     9044k free,    31332k buffers
Swap:  2088440k total,     1792k used,  2086648k free,   129716k cached
   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5618 ed        20   0  277m 149m  28m R   51 29.7   2:58.97 firefox            
 5122 root      20   0  353m  23m 7304 S    3  4.7   0:19.02 Xorg               
 5390 ed        20   0 13668 4632 3688 S    2  0.9   0:06.70 at-spi-registry    
 5080 root      20   0 14752 2644 2188 S    1  0.5   0:00.20 NetworkManager     
 5421 ed        20   0 21976 3276 1800 S    1  0.6   0:01.02 gnome-screensav    
 5821 ed        20   0 80684  23m  12m S    1  4.7   0:02.98 gnome-terminal     
 5847 ed        20   0  2416 1148  884 R    1  0.2   0:00.38 top                
    1 root      20   0  3056 1888  564 S    0  0.4   0:02.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.02 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1    


Any suggestions welcome

Frustrated ed

---

### Post by Cracauer on 2008-11-14
That looks normal.

Then you need the output of
`vmstat 3`

during the slowdown period.

---

### Post by tipiglen on 2008-11-14
Cracauer,  Thanks for the response.> Then you need the output of
`vmstat 3`

during the slowdown period. 
here you go.  I also noted it tends to occur after a period of not using the keyboard or touchpad.  Sort of like it's trying to spot an idle period to do whatever caching/stashing work it has on a task list...

Is this the sqlite process?


>  0  0   5848  30256   7680  87356    0    0     1     0  462 1654 13  1 86  0
 4  0   5848  30256   7680  87356    0    0     0     8  528 1612 12  2 87  0
 1  0   5848  30256   7680  87356    0    0     0     0  458 1584 12  2 86  0
 1  0   5848  30256   7680  87356    0    0     0     0  468 1526 12  2 86  0
 1  0   5848  30216   7688  87280    0    0     0     7  538 1734 15  3 82  0
 0  0   5848  30192   7692  87416    0    0     0     0  819 2125 26  4 71  0
 1  0   5848  30192   7708  87416    0    0     0    31  832 2024 38  3 59  0
 0  0   5848  30192   7708  87416    0    0     0     0  564 1734 17  2 81  0
 0  0   5848  30192   7720  87416    0    0     0    24  468 1583 13  2 85  0
 0  1   5848  29468   7760  88132    0    0   260     0  451 1370  6  2 61 30
 0  1   5848  28204   7764  89420    0    0   427     0  763 1685  4  2 50 44
 0  1   5848  26396   7772  91252    0    0   604     5  876 1772  3  3 52 43
 1  1   5848  24008   7776  93224  120    0   793     0  787 1720  6  3 49 42
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  1   5848  20068   7776  97200    0    0  1307     0  478 1413  7  2 51 40
 0  1   5848  13868   7780 103404    0    0  2081    61  602 1709  7  2 51 40
 2  2   5876   6360   7032 111220    0   28  3397    28  890 1920 10  4 35 51
 0  1   7864   6236   6232 113024   17  381  4151   515 1192 2011  9  4 34 53
 0  1   8424   6724   5060 114312    0  179  3888   245  862 1900 14  3 22 61
 0  2   8440   5640   4416 116160    0    0  5139     0  885 1867 15  4  6 75
 1  1   8440   5024   4404 116748    0    1  5940     1  831 1729 21  3  0 76
 1  1   8440   4984   4308 117876    0  289  6563   289 1081 2111 11  5 29 56
 0  2   8440   6100   4256 116972    0    5  5588     5  788 1824  9  3  9 78
 0  2   8440   5652   4256 117516    0    0  4832     0  758 1890  9  3  1 87
 0  2   8440   6872   4256 116272    0    0  2509     0  605 1494 10  3 12 74
 0  2   8440   5792   3792 117912    0    0  2941     0  795 1847  7  3 16 74
 0  2   8440   5156   3248 119240    0    0  4013     0 1093 2055 12  4 20 63
 0  1   8440   6344    612 120876    0    0  2329     0  615 1428 13  3 11 72
 1  0   8440   6740    532 120860    0    0   312    31  512 1633 14  2 46 38
 0  0   8440   9264    472 118776    0    0    31     0  757 2058 34  4 56  6
 1  0   8440   9368    484 118776    0    0     0    28  672 2135 14  3 83  0
 0  0   8440   9400    536 118824    0    0    33     0 1024 2393 15  4 75  6

Thanks again for any suggestions.

Puzzled ed

---

### Post by Cracauer on 2008-11-14
Yeah, so what you see there is very high "bi" which is "block in" which means something is reading from disk like hell.

While this is happening there is also some "so" which is "swap out", which means that the above input activity is kicking your Firefox and X out of memory. That ain't pretty.

Very basically if the "wa" (= wait) colum is big, as opposed to "id" (= idle), your system is dying from disk activity. 50% wait is bad, 78% is insane.

But alas, whoever is reading a TON of data is at fault. I think that this might be a cronjob such as the locatedb or some random mysql doing ... stuff in the background. 

You need to observe `top` more and try to spot it. Unfortunately top doesn't have an easy way to identify disk hogs and can't sort by disk activity, but something in the background is killing you. It's definitely not Firefox or X.

---

### Post by tipiglen on 2008-11-15
Cracauer,  Thanks again for sharing my puzzlement.> You need to observe `top` more and try to spot it. Unfortunately top doesn't have an easy way to identify disk hogs and can't sort by disk activity, but something in the background is killing you. It's definitely not Firefox or X.heree'a a dump of several 'top' sections...all during one of the periods of excess hdd activity...> ed@ubuntu:~$ top

top - 10:48:49 up 41 min,  2 users,  load average: 0.22, 0.55, 0.51
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.5%us,  0.8%sy,  0.0%ni, 78.7%id, 11.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514112k total,   506588k used,     7524k free,    20452k buffers
Swap:  2088440k total,     6744k used,  2081696k free,   112808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5602 ed        20   0  321m 176m  27m D   21 35.1   9:46.31 firefox            
 5100 root      20   0  353m  23m 7956 S    2  4.7   1:28.21 Xorg               
 5374 ed        20   0 13764 4564 3608 S    1  0.9   0:05.68 at-spi-registry    
 6445 ed        20   0 99.1m  24m  13m S    1  4.9   0:02.08 gnome-terminal     
 6471 ed        20   0  2416 1156  884 R    1  0.2   0:01.00 top                
 5910 ed        20   0 58652  22m  12m S    0  4.4   0:09.75 gedit              
    1 root      20   0  3056 1884  564 S    0  0.4   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.12 kblockd/0          
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
  139 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod            
  182 root      20   0     0    0    0 S    0  0.0   0:00.06 pdflush            
  183 root      20   0     0    0    0 S    0  0.0   0:00.18 pdflush            
  184 root      15  -5     0    0    0 S    0  0.0   0:00.64 kswapd0            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1116 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1130 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 1178 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1179 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
ed@ubuntu:~$ top

top - 10:49:05 up 41 min,  2 users,  load average: 0.54, 0.60, 0.53
Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.2%us,  1.9%sy,  0.0%ni, 31.1%id, 61.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514112k total,   508604k used,     5508k free,    15312k buffers
Swap:  2088440k total,     6820k used,  2081620k free,   115068k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5602 ed        20   0  327m 181m  27m D   12 36.2   9:47.07 firefox            
 5100 root      20   0  353m  23m 7956 S    1  4.7   1:28.52 Xorg               
  184 root      15  -5     0    0    0 D    1  0.0   0:00.68 kswapd0            
 6474 ed        20   0  2416 1152  884 R    1  0.2   0:00.06 top                
    1 root      20   0  3056 1884  564 S    0  0.4   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.14 kblockd/0          
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
  139 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod            
  182 root      20   0     0    0    0 S    0  0.0   0:00.06 pdflush            
  183 root      20   0     0    0    0 S    0  0.0   0:00.18 pdflush            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1116 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1130 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 1178 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1179 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1255 root      15  -5     0    0    0 S    0  0.0   0:00.18 ata/0              
 1272 root      15  -5     0    0    0 S    0  0.0   0:00.18 ata/1              
 1273 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
ed@ubuntu:~$ top

top - 10:49:25 up 42 min,  2 users,  load average: 0.88, 0.68, 0.56
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.1%us,  2.2%sy,  0.0%ni,  0.1%id, 85.3%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:    514112k total,   508392k used,     5720k free,      696k buffers
Swap:  2088440k total,     6936k used,  2081504k free,   128140k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5602 ed        20   0  332m 186m  27m D   30 37.2   9:51.86 firefox            
  184 root      15  -5     0    0    0 D    1  0.0   0:00.78 kswapd0            
 5100 root      20   0  353m  23m 7956 S    1  4.7   1:28.80 Xorg               
 6445 ed        20   0 99.1m  24m  13m S    1  4.9   0:02.26 gnome-terminal     
    1 root      20   0  3056 1884  564 S    0  0.4   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.14 kblockd/0          
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
  139 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod            
  182 root      20   0     0    0    0 S    0  0.0   0:00.06 pdflush            
  183 root      20   0     0    0    0 S    0  0.0   0:00.18 pdflush            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1116 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1130 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 1178 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1179 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1255 root      15  -5     0    0    0 S    0  0.0   0:00.18 ata/0              
 1272 root      15  -5     0    0    0 S    0  0.0   0:00.18 ata/1              
 1273 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
ed@ubuntu:~$ top

top - 10:49:46 up 42 min,  2 users,  load average: 1.06, 0.73, 0.57
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.4%us,  0.7%sy,  0.0%ni, 48.5%id, 46.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514112k total,   507696k used,     6416k free,      420k buffers
Swap:  2088440k total,     6940k used,  2081500k free,   128148k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5602 ed        20   0  333m 187m  27m D    9 37.3   9:54.73 firefox            
 5100 root      20   0  353m  23m 7956 S    1  4.7   1:29.01 Xorg               
 4721 messageb  20   0  3004 1264  732 S    1  0.2   0:00.68 dbus-daemon        
 6476 ed        20   0  2416 1152  884 R    1  0.2   0:00.06 top                
    1 root      20   0  3056 1884  564 S    0  0.4   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.14 kblockd/0          
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
  139 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod            
  182 root      20   0     0    0    0 S    0  0.0   0:00.06 pdflush            
  183 root      20   0     0    0    0 S    0  0.0   0:00.18 pdflush            
  184 root      15  -5     0    0    0 S    0  0.0   0:00.86 kswapd0            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1116 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1130 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 1178 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1179 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1255 root      15  -5     0    0    0 S    0  0.0   0:00.20 ata/0              
 1272 root      15  -5     0    0    0 S    0  0.0   0:00.20 ata/1              
ed@ubuntu:~$ Any thoughts, anyone?  recognise anything?

Still puzzled; still patient
ed

---

### Post by Cracauer on 2008-11-15
Nothing obvious.

killall -9 at-spi-registry 

seems like a good next step, but the evidence is weak.

But something is reading large amounts of data and you need to catch it.

---

### Post by tipiglen on 2008-11-16
OK. I installed sysstat and it has a command pidstat, which identifies which command (task/PID) is generating disk reads and writes, thus, during one of the heavy i/o periods:
```
ed@ubuntu:~$ pidstat -d 3
Linux 2.6.27-7-generic (ubuntu) 	11/16/2008 	_i686_

07:48:02 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:48:05 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:08 PM      5754      0.00     45.33     45.33  firefox

07:48:08 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:11 PM      2145      0.00      1.33      0.00  kjournald
07:48:11 PM      5754      0.00     45.33      0.00  firefox

07:48:11 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:48:14 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:48:17 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:20 PM      5754      0.00     45.33     45.33  firefox

07:48:20 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:23 PM      5754      0.00     29.33      0.00  firefox

07:48:23 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:48:26 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:29 PM      5754      0.00     46.67     45.33  firefox

07:48:29 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:32 PM      5754      0.00     37.33      0.00  firefox

07:48:32 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:48:35 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:38 PM      2145      0.00      5.33      0.00  kjournald
07:48:38 PM      5754      0.00     46.67     45.33  firefox

07:48:38 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:41 PM      5754     26.67      0.00      0.00  firefox

07:48:41 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:44 PM      5754    372.00      0.00      0.00  firefox

07:48:44 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:47 PM      5754    381.33      0.00      0.00  firefox

07:48:47 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:50 PM      2145      0.00     13.33      0.00  kjournald
07:48:50 PM      5754   2004.00      0.00      0.00  firefox

07:48:50 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:53 PM      5754   3560.00      0.00      0.00  firefox

07:48:53 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:56 PM      5754   2402.67      0.00      0.00  firefox

07:48:56 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:48:59 PM      5754   5025.33      0.00      0.00  firefox

07:48:59 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:02 PM      5070      0.00      1.33      0.00  wpa_supplicant
07:49:02 PM      5174      1.33      0.00      0.00  cron
07:49:02 PM      5754   5980.00      0.00      0.00  firefox

07:49:02 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:05 PM      5754   6254.67      0.00      0.00  firefox

07:49:05 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:08 PM      5754   6805.33      0.00      0.00  firefox

07:49:08 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:11 PM      2145      0.00      1.33      0.00  kjournald
07:49:11 PM      5754   4684.00      0.00      0.00  firefox

07:49:11 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:14 PM      5754   4218.67      0.00      0.00  firefox

07:49:14 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:17 PM      5754   2489.33      0.00      0.00  firefox

07:49:17 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:20 PM      5754   2769.33      0.00      0.00  firefox

07:49:20 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:23 PM      4647      4.00      1.33      0.00  syslogd
07:49:23 PM      5754   3693.33      0.00      0.00  firefox

07:49:23 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:26 PM      2145      0.00      1.33      0.00  kjournald
07:49:26 PM      5754   3326.67      0.00      0.00  firefox

07:49:26 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:29 PM      5754    749.33     22.67      9.33  firefox

07:49:29 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:32 PM      5754    370.67      0.00      0.00  firefox

07:49:32 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:35 PM      2145      0.00     18.67      0.00  kjournald
07:49:35 PM      5754    174.67    141.33      6.67  firefox

07:49:35 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:38 PM      2145      0.00     17.33      0.00  kjournald
07:49:38 PM      5754     86.67     33.33      0.00  firefox

07:49:38 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:41 PM      5754     37.33     34.67      0.00  firefox

07:49:41 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:44 PM      5754     36.00     85.33     45.33  firefox

07:49:44 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
07:49:47 PM      2145      0.00      1.33      0.00  kjournald
07:49:47 PM      5754      0.00     29.33      0.00  firefox
07:49:47 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

07:49:50 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command


```
So it seems the problem is within Firefox...The next step is to try disabling the phishing protection, which I read somewhere may be the problem...I also have a lot of bookmarks, and if firefox is constantly stashing them, that may be part of the problem, as may be the general ability of firefox to re-start with everything as it eas, including even partially completed entry forms...

Details later

Slow and steady ed

---

### Post by tipiglen on 2008-11-16
For what it's worth, Another possible work around:
[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/](http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/)

I have disabled phishing and forgery warnings, and deleted the urlclassifier files.  We'll see what happens

No slowdowns or hyperactive i/o so far...

Patient ed

---

### Post by tipiglen on 2008-11-16
> I have disabled phishing and forgery warnings, and deleted the urlclassifier files. We'll see what happens

No slowdowns or hyperactive i/o so far...Spoke too soon! 
```
08:40:20 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:23 PM      2145      0.00     16.00      0.00  kjournald
08:40:23 PM      5754      0.00     29.33      0.00  firefox

08:40:23 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

08:40:26 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

08:40:29 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:32 PM      5754    353.33      0.00      0.00  firefox

08:40:32 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:35 PM      5754    381.33      0.00      0.00  firefox

08:40:35 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:38 PM      5754   1973.33      0.00      0.00  firefox

08:40:38 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:41 PM      5754   2537.33      0.00      0.00  firefox

08:40:41 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:44 PM      5754   3392.00      0.00      0.00  firefox

08:40:44 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:47 PM      5754   4833.33      0.00      0.00  firefox

08:40:47 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:50 PM      5754   5264.00      0.00      0.00  firefox

08:40:50 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:53 PM      5754   6468.00      0.00      0.00  firefox

08:40:53 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:56 PM      5754   6573.33      0.00      0.00  firefox

08:40:56 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:40:59 PM      5754   5545.33      0.00      0.00  firefox

08:40:59 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:02 PM      5174      2.67      0.00      0.00  cron
08:41:02 PM      5754   3881.33      0.00      0.00  firefox

08:41:02 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:05 PM      2145      0.00      1.33      0.00  kjournald
08:41:05 PM      5070      1.33      1.33      0.00  wpa_supplicant
08:41:05 PM      5754   2856.00      0.00      0.00  firefox

08:41:05 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:08 PM      5754   3054.67      0.00      0.00  firefox

08:41:08 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:11 PM      5754   4222.67      0.00      0.00  firefox

08:41:11 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:14 PM      5754   3066.67      0.00      0.00  firefox

08:41:14 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:17 PM      2145      0.00      2.67      0.00  kjournald
08:41:17 PM      5754    280.00     97.33     13.33  firefox

08:41:17 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:20 PM      5754     13.33     17.33      0.00  firefox

08:41:20 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:23 PM      2145      0.00     24.00      0.00  kjournald
08:41:23 PM      5754    272.00      0.00      0.00  firefox

08:41:23 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:26 PM      2145      0.00      1.33      0.00  kjournald
08:41:26 PM      5754    218.67     48.00      0.00  firefox

08:41:26 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:29 PM      5754      0.00     45.33     45.33  firefox

08:41:29 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:32 PM      2145      0.00      1.33      0.00  kjournald
08:41:32 PM      5754      2.67     37.33      0.00  firefox

08:41:32 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command

08:41:35 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:38 PM      5754      0.00     45.33     45.33  firefox

08:41:38 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
08:41:41 PM      2145      0.00     18.67      0.00  kjournald
08:41:41 PM      5754      0.00     38.67      0.00  firefox

08:41:41 PM       PID   kB_rd/s   kB_wr/s kB_ccwr/s  Command
^Z
[6]+  Stopped                 pidstat -d 3
ed@ubuntu:~$ 

``` Oh well, back to seeking the cause...

---

### Post by tipiglen on 2008-11-16
From this thread, 

[http://ubuntuforums.org/showthread.php?p=6193285#post6193285](http://ubuntuforums.org/showthread.php?p=6193285#post6193285)

there is the suggestion to delete the places.sqlite file from my mozilla profile (after backing up the entire profile).  I have done as suggested, and we'll see...

---

### Post by Cracauer on 2008-11-16
Why don't you use a freshly created profile with no extensions for a while?

Do you really need physhing protection?

---

### Post by tipiglen on 2008-11-16
Phishing and forgery warnings re-enabled.

/home/ed/.mozilla/firefox/------.default/places.sqlite is now 1.2Mb instead of 250Mb, and firefox has been running perfectly for at least two hours without a single episode of manic i/o.

I think I can label this as solved, but I'll give it a couple of days.

Hopeful ed

---

### Post by Cracauer on 2008-11-17
Ouch. If it's checking 250 MB worth of URLs on your 500 MB computer that's gotta hurt.

Why do you think you need it?

---

### Post by josephellengar on 2008-11-17
> **tipiglen said:**
> Quite frequently my system becomes unresponsive and sluggish. 
I have Firefox 3 running most of the time, and Flash installed

Just sometimes the whole thing seems to go on holiday, not a total freeze-up but that sometimes happens (a lot less often).  Eventually it comes back, and does whatever clicks and touchpad movements tried in frustration while waiiting, so the screen jumps up and down and firefox probably switches (finally) to another tab....I'm sure some folk out there know what I'm describing.

It all began with Hardy.  Here is a copy of the top of a top display:

top - 18:22:32 up  1:42,  2 users,  load average: 0.83, 0.39, 0.37
Tasks: 119 total,   2 running, 115 sleeping,   2 stopped,   0 zombie
Cpu(s):  4.5%us,  1.1%sy,  0.0%ni, 94.0%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    514112k total,   501460k used,    12652k free,     4100k buffers
Swap:        0k total,        0k used,        0k free,   121100k cached


What I note is that almost ALL of my RAM seems to be constantly occupied.  Is this the problem?  Is it just that Hardy is so new and modern that it assumes nobody would be so bold as to try to get by with only half a gig of RAM?

Any suggestions as to how to get my laptop back to the slick operator it was, or should I just go back to an earlier release...?

In frustration
ed

Linux almost always uses all of the RAM, no matter how much you have and what you are running, because it tries to maximize use of available resources.
Some suggestions:
I had the same problem with the swap partition not turning on.  I deleted my swap partition and made a new swap _file_, rather than a partition per this link: [http://www.usenet-forums.com/linux-general/84802-how-add-back-ubuntu-swapfile.html](http://www.usenet-forums.com/linux-general/84802-how-add-back-ubuntu-swapfile.html)
Now it works and does swapon at boot.  More ram would help of course, but the swap might be enough.
Also, are you fully updated?

---

### Post by tipiglen on 2008-11-17
> If it's checking 250 MB worth of URLs on your 500 MB computer that's gotta hurt.That's Firefox 3 for you!  The whole bookmarks.html file (automatically saved on exit) is only 100Kb...

I like my bookmarks, and I like it that ff will find any one I want really quickly...

Everything is working just fine now, so I'm labelling th thread solved.

Happy ed:)

---

