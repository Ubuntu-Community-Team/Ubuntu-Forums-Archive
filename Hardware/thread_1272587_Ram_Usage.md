---
title: "Ram Usage"
date: 2009-09-22
forum: Hardware
---

### Post by gos1 on 2009-09-22
Hi : 
  
 I am using a MSI lap top with 2 gb ram and 1800 mhz 64 bit processor. Still cannot run programs efficiently in Ubuntu Jaunty Jackalope. I have many applications running but dont know exact explanation to all applications . 
 
  Now my problem is : 
 
   How can I know which program is using what amount of ram ? 

   Is there a place which has a description of important applications needed by Ubuntu and Gnome to run correctly ? 
 
  Thank you

---

### Post by snowpine on 2009-09-22
System->Administration->System Monitor

or with a command line tool like 'top'

Can you provide more details of the problem?

---

### Post by gos1 on 2009-09-22
Hi ; 
 
  After running the system monitor I saw that my problem is with CPU not ram. 
 
  When I try to autocomplete in eclipse it uses all my CPU . And Gnome system monitor also uses most of my CPU  
 
  How can I fix that ? 
 
   I have a 1800 MHz CPU ? Isn't it enough for Ubuntu ?

---

### Post by snowpine on 2009-09-22
Sorry but I have never used Eclipse before and can't help with that.

It is normal for the system monitor itself to be a bit of a pig. :)

1800mhz is plenty; I've run Ubuntu on a 500mhz pentium 3.

---

### Post by gordintoronto on 2009-09-22
You say you have many applications running.  What applications?

For example, if you are running Open Office Word, it won't consume any significant CPU when it does not have the focus, but Miro (RSS aggregator) will take a lot of CPU any time it is downloading or playing videos.

---

### Post by gos1 on 2009-09-22
The most of the CPU is used by the Firefox and Eclipse. 
 
  Here is the output of top command 

```

 
      PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4349 cem       20   0  185m  64m  22m S  9.3  3.4   0:14.44 firefox            
 4626 cem       20   0 33888  14m 9652 S  4.3  0.8   0:00.89 gnome-terminal     
 3153 root      20   0 94356  40m  13m R  3.6  2.1   0:08.38 Xorg               
 4000 cem       20   0 69348  36m  11m S  1.0  1.9   0:02.90 compiz.real        
 3740 chipcard  20   0  4696 1608 1168 S  0.7  0.1   0:00.85 chipcardd4         
 2524 mysql     20   0  126m  23m 5132 S  0.3  1.2   0:00.67 mysqld             
 4336 cem       20   0 16680 2748 1400 S  0.3  0.1   0:00.35 gnome-screensav    
 4656 cem       20   0  2448 1192  912 R  0.3  0.1   0:00.05 top                
    1 root      20   0  3084 1884  564 S  0.0  0.1   0:01.15 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0    PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4349 cem       20   0  185m  64m  22m S  9.3  3.4   0:14.44 firefox            
 4626 cem       20   0 33888  14m 9652 S  4.3  0.8   0:00.89 gnome-terminal     
 3153 root      20   0 94356  40m  13m R  3.6  2.1   0:08.38 Xorg               
 4000 cem       20   0 69348  36m  11m S  1.0  1.9   0:02.90 compiz.real        
 3740 chipcard  20   0  4696 1608 1168 S  0.7  0.1   0:00.85 chipcardd4         
 2524 mysql     20   0  126m  23m 5132 S  0.3  1.2   0:00.67 mysqld             
 4336 cem       20   0 16680 2748 1400 S  0.3  0.1   0:00.35 gnome-screensav    
 4656 cem       20   0  2448 1192  912 R  0.3  0.1   0:00.05 top                
    1 root      20   0  3084 1884  564 S  0.0  0.1   0:01.15 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0


```

 Do you see a problem ?

---

### Post by snowpine on 2009-09-22
Looks normal to me... no single process is using more over 10% of your CPU or 5% of your ram... I guess I still don't really understand what your question is?

---

### Post by gos1 on 2009-09-23
I cannot use Eclipse and Firefox Efficiently ? My question is is my system configuration is too low for these applications or is there a problem with my Ubuntu ? p,/

---

### Post by snowpine on 2009-09-23
Like I said, I have no experience with Eclipse.

Firefox is only using 9.3% of your CPU and 3.4% of your ram. That looks normal to me. If you aren't satisfied with its performance, you could experiment with faster web browsers (opera, epiphany-browser, midori, kazehakase, etc).

---

### Post by kunst on 2009-10-07
I also have this problem. for example, in eclipse, i type a point ("."), the system will stay and grey for a while. I kown eclipse want to find out all the posible member or methods of the class in front of that point. But in other system, I need not to wait at all. I dont think it is a problem in eclipse. 

If someone has an idea, please discuss. Dont answer if you even not know what eclipse is.

---

