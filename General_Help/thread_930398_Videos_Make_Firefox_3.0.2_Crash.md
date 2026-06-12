---
title: "Videos Make Firefox 3.0.2 Crash"
date: 2008-09-26
forum: General Help
---

### Post by liquidypoo on 2008-09-26
This is starting to get really annoying.  Whenever I pull up a website that has some sort of video embedded, or even some Java application embedded, there's a 50/50 chance that Firefox will just flat out disappear, and I have to restart it.

Luckily it gives me the chance to reload the previous page, so I can usually get right back to the video I was trying to watch, but it's still a complete hassle whenever I'm just surfing Youtube, since about half the things I click will crash Firefox.  Even really advanced advertisements can make Firefox crash unexpectedly!  Can anybody help with this?

---

### Post by neu2buntu on 2008-09-27
im having the same prob..did you get it sorted at all?   it only started when i installed backtrack to new partition<  firefox can run well for ages then it just crashes especially when on youtube bebo etc..im the same my settings are to save last session on firefox...hope u can help!!?

---

### Post by liquidypoo on 2008-09-27
Bumping because the issue still isn't resolved.

I upgraded to Firefox 3.0.3, and videos still make Firefox crash.  It didn't really make a difference.

---

### Post by sleepingdragon on 2008-09-27
Try this post.[http://ubuntuforums.org/showthread.php?t=904719]("http://ubuntuforums.org/showthread.php?t=904719")

---

### Post by liquidypoo on 2008-09-28
Thanks.  I kinda wish I knew the proper terms for all of this so that using the search would actually pull up 4 week old threads.

EDIT:  munshi pretty much said it, but yes, the first youtube video I attempted to load crashed Firefox instantly.  Are there any other solutions?

EDIT 2:  Those fixes actually seemed to have made it worse.  Firefox has never crashed on a restart before now.  I'm changing those settings back to their defaults.

---

### Post by munshi on 2008-09-28
tried the fix in the other topic but with 3 youtubes loading firefox crashed again.any more ideas

---

### Post by munshi on 2008-09-28
i just came back from the IRC channel and there bobertdos recommended removing all flash packages and installing the nonfree again and it seems to do mircales.try it

---

### Post by Amarsingh0793 on 2008-09-28
Install No-script (Firefox Addon). At least then it protects you, aswell as warns you about harmful scripts on a webpage.

---

### Post by liquidypoo on 2008-09-30
Thanks for those suggestions, guys.  Just took care of all of that, so all that's left is to test it out.

EDIT:  Ugh, reinstalling the nonfree didn't seem to fix it.  I guess I'll just have to live with it.  Thanks for trying, everyone.

---

### Post by Crafty Kisses on 2008-09-30
It could be a resource issue, while Firefox is open, go in the Terminal and do the following:
```
top
```
Then post the results here.

---

### Post by liquidypoo on 2008-10-02
I had a little trouble getting this, since it was one of those things that was constantly changing and updating, but here's what I managed to copy:

```
top - 15:31:00 up 3 days, 19:28,  2 users,  load average: 0.27, 0.28, 0.27
Tasks: 118 total,   2 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.5%us,  0.3%sy,  0.0%ni, 91.9%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1026156k total,   989800k used,    36356k free,   111520k buffers
Swap:  3004112k total,    39752k used,  2964360k free,   409188k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9095 ed        20   0  218m  98m  24m S  3.8  9.8   4:23.06 firefox            
 5266 root      20   0  402m  61m  10m S  1.7  6.1 154:08.13 Xorg               
 5936 ed        20   0  189m  74m  27m R  0.6  7.4  49:51.94 amarokapp          
10642 ed        20   0 96512  19m  11m S  0.6  1.9   0:00.24 gnome-terminal     
10662 ed        20   0  2308 1120  856 R  0.6  0.1   0:00.02 top                
 4673 root      15  -5     0    0    0 S  0.3  0.0   4:06.48 kondemand/0        
 6219 ed        20   0 22072  14m 5828 S  0.3  1.4  10:41.89 compiz.real        
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.24 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:12.92 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.14 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.60 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kacpi_notify       


```

One thing that's kind of confusing me is why it says "2 users" as opposed to just one.  Any way I could have managed to accidentally log myself in twice in a row?

---

