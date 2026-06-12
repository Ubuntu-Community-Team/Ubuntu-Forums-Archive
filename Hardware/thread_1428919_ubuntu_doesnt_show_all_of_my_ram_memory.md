---
title: "ubuntu doesnt show all of my ram memory"
date: 2010-03-13
forum: Hardware
---

### Post by jamoncillo on 2010-03-13
I have a compaq CQ40-320LA notebook, with 1gb of ram

it came with vista, and I immediately installed Linux Mint Helena

However, it only shows around 750 of my 1gb ram!

my bios says its 1gb, and so did vista and xp. any help??

---

### Post by Sef on 2010-03-13
Applications > Accessories > Terminal

Then copy and paste (or type) in this code:

```
top
```

Copy and paste the results in here.

---

### Post by efflandt on 2010-03-13
What does **free -m** show?  It may depend upon shared video RAM, whether a specific amount is set in BIOS, or if that is dynamic (as needed), and your video resolution.

---

### Post by jamoncillo on 2010-05-07
truly sorry for the delay, had some trouble accessing the other computer.

top gives:

```

top - 23:43:17 up 38 min,  2 users,  load average: 0.06, 0.30, 0.33 
Tasks: 148 total,   2 running, 146 sleeping,   0 stopped,   0 zombie 
Cpu(s): 24.5%us,  3.3%sy,  0.0%ni, 70.5%id,  1.7%wa,  0.0%hi,  0.0%si,  0.0%st 
Mem:    765836k total,   756164k used,     9672k free,    20260k buffers 
Swap:  1076312k total,    14356k used,  1061956k free,   246700k cached 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1093 root      20   0  154m  91m  22m S 13.9 12.2   3:18.67 Xorg               
 3005 jamon     20   0  409m  46m  21m S  5.0  6.3   1:14.44 rhythmbox          
 2215 jamon     20   0 82000  35m  18m S  1.7  4.7   0:15.35 gnome-do           
 3419 jamon     20   0  111m  54m 9804 S  1.7  7.2   0:54.43 wish8.5            
 3285 jamon     20   0  304m  98m  27m S  1.3 13.2   4:04.27 firefox            
 2180 jamon     20   0 35624  25m 6884 S  1.0  3.4   0:14.94 compiz.real        
 1941 jamon     20   0  164m 5516 4332 S  0.7  0.7   0:37.45 pulseaudio         
 4747 jamon     20   0  2472 1176  884 R  0.7  0.2   0:00.18 top                
  726 syslog    20   0 33832 1188  976 S  0.3  0.2   0:00.05 rsyslogd           
 2181 jamon     20   0 48704  17m  12m S  0.3  2.3   0:08.60 gnome-panel        
 2322 jamon     20   0 19904 9564 7656 S  0.3  1.2   0:02.70 gtk-window-deco    
    1 root      20   0  2532 1128 1128 S  0.0  0.1   0:00.95 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 events/0 

```



while free -m  gives:

```

 total       used       free     shared    buffers     cached
Mem:           747        716         31          0         11        235
-/+ buffers/cache:        469        278
Swap:         1051         15       1035

```

---

### Post by garvinrick4 on 2010-05-07
Are you running virtual, you are using  a lot of memory just to run OS.

---

### Post by jamoncillo on 2010-05-12
nope, just Mint. I have desktop effects enabled
in fact my other machine (running Lucid) gives (to those same commands):


TOP
```

top - 16:25:43 up  1:13,  2 users,  load average: 1.21, 1.12, 1.18
Tasks: 196 total,   2 running, 194 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.2%us, 23.8%sy,  3.4%ni, 55.7%id,  2.5%wa,  0.3%hi,  0.1%si,  0.0%st
Mem:   2052404k total,  1663536k used,   388868k free,    36688k buffers
Swap:  1228932k total,     2232k used,  1226700k free,  1046208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1148 root      20   0 74668  31m  15m S   10  1.5   7:10.96 Xorg               
 1282 jamon     20   0  312m  74m  33m S    6  3.7   5:09.86 rhythmbox          
 3012 jamon     20   0  414m 121m  37m S    4  6.1   2:02.13 firefox-bin        
 1214 jamon     20   0  3780 2008  688 S    2  0.1   0:09.82 dbus-daemon        
 1237 jamon     20   0  101m  39m 9328 S    2  2.0   2:20.23 compiz             
 1243 jamon      9 -11  157m  11m  10m S    2  0.6   2:01.17 pulseaudio         
 1254 jamon     20   0  117m  39m  16m S    2  2.0   2:30.43 emesene            
 1301 jamon     20   0  111m  50m  21m S    2  2.5   0:37.05 gnome-do           
 3889 jamon     20   0  2540 1132  812 R    2  0.1   0:00.02 top                
    1 root      20   0  2800 1580 1200 S    0  0.1   0:00.58 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         


```

FREE -M
```

jamon@jamuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1628        375          0         35       1028
-/+ buffers/cache:        564       1439
Swap:         1200          2       1197

```

and doing nothing but listening to music, chatting and checking the forum

So, I think they're more less the same, right?
the only difference is Mint sees only 750Mb out of 1gb in ram, while my other notebook has 2gb

Or what memory are you talking about?

thanks again for all your help

---

### Post by dino99 on 2010-05-12
maybe some ram shared with the graphic chipset

---

### Post by jamoncillo on 2010-05-13
> **dino99 said:**
> maybe some ram shared with the graphic chipset

how do I check if that's the case? /=

---

### Post by happycube on 2010-05-13
I pulled up the specs from HP, and yeah it's got integrated video/shared memory.  You should be able to drop the amount in the BIOS.

---

### Post by jamoncillo on 2010-05-13
> **happycube said:**
> I pulled up the specs from HP, and yeah it's got integrated video/shared memory.  You should be able to drop the amount in the BIOS.

uhm.. I don't quite get it. I mean, I do understand, it's an easy concept to grab. If you don;t have a graphic card and instead have integrated graphics, you need to use ram. But why does Mint says it's only 750gb instead of the whole 1gb? and why, if I have a HP desktop PC that also has integrated graphics it doesn't shows less ram?? [this one I can't confirm right now, I lent the PC]

So, lets say that's the thing. I should just drop the amount dedicated to video to, like 128mb and that should do the trick? 'cause I have compiz running and it makes the computer laggy sometimes =/

---

### Post by Yellow Pasque on 2010-05-13
> **jamoncillo said:**
> But why does Mint says it's only 750gb instead of the whole 1gb?
..because it makes sense? Or would you like Linux to lie to you like Windows?
If you want to see the amount of physical RAM, use:
```
sudo dmidecode
```

---

### Post by jamoncillo on 2010-05-13
> **Temüjin said:**
> ..because it makes sense? Or would you like Linux to lie to you like Windows?


jajjaa. Yeah, it does make sense. Sorry, I'm still used to the way windows showed my RAM, thought I've been using only Ubuntu for long. I'll check it tonight and let you know. 

By the way, is there a command to show how much memory is assigned to video? that way, if video + ram equals 1gb, then it would all make sense

thanks

---

### Post by dino99 on 2010-05-13
anyway you cant use compiz (which eat lot of ram) and ask the same results given by a recent card with lot ram :(

let ubuntu deal with your ram for better compromise

---

