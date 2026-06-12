---
title: "[SOLVED] CPU Speed being scaled to half speed?"
date: 2008-07-10
forum: Hardware
---

### Post by Doc Hoss on 2008-07-10
I am using a Pentium D 3.0 GHz (dual core), and the CPU Frequency Scaling Monitor applet is showing that it is running at or about 1.40 GHz, reporting it is being scaled to 93%.  This math makes 1.50 GHz 100%.  It does show that I have two cpu's, but they both only report up to 1.50 GHz. The System tab in the system monitor shows Processor 0 and Processor 1 both as 3.0GHz. Am I confused about how a dual-core processor works?  

It also shows this in cpufreq-info:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.40 GHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.40 GHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 1.40 GHz and 1.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.40 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.40 GHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.40 GHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 1.40 GHz and 1.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.40 GHz.

```

How do I change this to be a full 3.0 GHz per core?

---

### Post by Doc Hoss on 2008-07-12
2-day bump... ;)  Anyone?

---

### Post by ljonesj on 2008-07-12
there may be something as easy as a bios file called edst i think that needs to be changed in bios or the program i think in ubuntu cpuscale i think may need to be installed i dont have a dual core ubuntu system just my vista one, as my ubunut is a 2ghz single core celeron that i think is froma core solo seires

---

### Post by Doc Hoss on 2008-07-12
Ok.  I have to move this week, but I'll see what I can do about getting cpuscale installed.  Thanks for the tip!

Anyone else have other opinions on what this might be, in case ljonesj's solution doesn't work?

---

### Post by Doc Hoss on 2008-08-16
Well, after moving across the country and trying to get this thing working now, I find that I have cpuscale installed, as well as cpufreq-utils and powernowd.  All of these seem to be reporting that my processor cores are topping out at 1.50 Ghz.  Can anyone else give me some advice?

---

### Post by Doc Hoss on 2008-08-16
Ok...if I "modprobe -r acpi-cpufreq" the frequencies are reported correctly.  So it's a problem with acpi-cpufreq.  Any idea how I can fix this module?

---

### Post by Sylchat on 2008-08-18
Hi Doc,

What gives:
$ cat /proc/cpuinfo

and:
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

I was running at 800MHz for both cores of my 1.6GHz core2duo proc and did this:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1600000 1333000 1067000 800000

sudo /usr/bin/cpufreq-selector -f 1600000

Now my proc is running at full:
$ diff proc-cpuinfo.1 proc-cpuinfo.2
7c7
< cpu MHz		: 800.000
---
> cpu MHz		: 1600.000
31c31
< cpu MHz		: 800.000
---
> cpu MHz		: 1600.000


Hope this helps!
Sylchat

---

### Post by darco on 2008-08-18
is this a bug? I have an Intel Q6600 Quad Core and this is my output ( I am purposely only posting  1 cpu) 

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4779.72
clflush size	: 64

also
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2394000 1596000 

Will I cause damage if I run the cpu selector comand and choose 2394000?????
thxs
darco

---

### Post by Sylchat on 2008-08-20
> **darco said:**
> is this a bug? I have an Intel Q6600 Quad Core and this is my output ( I am purposely only posting  1 cpu) 


model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
cpu MHz		: 1596.000

also
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2394000 1596000 

Will I cause damage if I run the cpu selector comand and choose 2394000?????
thxs
darco

I don't know if this cause damage.

But this is similar to my Core2Duo 1.6, reported as running at 800 MHz.
After setting it to 1.6 with the freq selector, it reports to 1.6 GHz.

But according to the global setting set to "ondemand" by default, it will lower back to 800 if low on charge.
You may want to read this: [http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

cheers,
Sylchat

---

### Post by Krupski on 2008-08-20
> **Doc Hoss said:**
> I am using a Pentium D 3.0 GHz (dual core), and the CPU Frequency Scaling Monitor applet is showing that it is running at or about 1.40 GHz, reporting it is being scaled to 93%.  This math makes 1.50 GHz 100%.  It does show that I have two cpu's, but they both only report up to 1.50 GHz. The System tab in the system monitor shows Processor 0 and Processor 1 both as 3.0GHz. Am I confused about how a dual-core processor works?  

It also shows this in cpufreq-info:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.40 GHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.40 GHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 1.40 GHz and 1.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.40 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.40 GHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.40 GHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 1.40 GHz and 1.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.40 GHz.

```

How do I change this to be a full 3.0 GHz per core?


There's nothing wrong with the CPU running slower than max... but you DO seem to have a problem with the top end.

Is your CPU heatsink and fan working? Intel dual core and quad core CPU's throttle down their clock speeds when they overheat. Make sure yours is getting the proper cooling.

I just checked my NAS box which is running a Core 2 Duo E6700 CPU at 2.66 GHz... the numbers are what I expected:

```

root@storage:/# cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.60 GHz - 2.66 GHz
  available frequency steps: 2.66 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.66 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.60 GHz - 2.66 GHz
  available frequency steps: 2.66 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.66 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).

```

Note that it's running at 1.6 GHz because it's got nothing to do right now, but the max speed is correctly reported as 2.66 Ghz.

Here's a small piece of /proc/cpuinfo:

```

root@storage:/# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
..............

```


Again, looks right.

Check if your CPU is being cooled properly.

-- Roger

---

### Post by Sylchat on 2008-08-21
Also, you may want to check this key in gconf-editor:
/apps/gnome-power-manager/cpufreq

Try setting 'performance' instead of 'ondemand' for policy_ac, and see if you have the top frequence when ac is plugged in.

Also, try running several applications and see if the frequence is upscaled accordingly.

---

### Post by Doc Hoss on 2008-08-22
Here's the output...

```
XXX@XXX-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 1500.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6110.90
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 1400.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6105.28
clflush size    : 64

```

And the available speeds...

```
XXX@XXX-desktop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1500000 1400000

```

The temperature should be fine.  It wasn't before, so I took your advice and looked at the cpu and fan (both caked with dirt, of course) and fixed them.  Now I get no heat alarms, as I did before, but the frequencies are still wrong.  

> Also, you may want to check this key in gconf-editor:
/apps/gnome-power-manager/cpufreq

Try setting 'performance' instead of 'ondemand' for policy_ac, and see if you have the top frequence when ac is plugged in.

Also, try running several applications and see if the frequence is upscaled accordingly. 

I tried this suggestion, but to no avail.  Apparently that's not the solution  :(  Thanks though!

Anyone got ideas?

Edit: I also tried this...

> I was running at 800MHz for both cores of my 1.6GHz core2duo proc and did this:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1600000 1333000 1067000 800000

sudo /usr/bin/cpufreq-selector -f 1600000


No dice.  Apparently did nothing... *shrug*

---

### Post by Doc Hoss on 2008-09-05
Anyone else have ideas how I can get cpufreq to behave?

---

### Post by karlrt on 2008-11-20
Hm, i dont know any answer, but i just got the same problem:

I have a intelcore2duo:

```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips	: 4394.08
clflush size	: 64

```

with these frequences available: ```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2201000 2200000 1600000 1200000 800000
``` And it never lets me go higher then 1,2 Ghz! 

And the funny thing is: i use ubuntu on the pc now for half a year, and it allways worked! (until now) I also use the cpu-scaling applet, not to change the values but rather to control my cpu (sometimes flash takes all the cpu, and this makes the thinkpad hot)

I also control the temp, right now its at abotu 46° so it shouldnt downscale by default (sometimes the cpu for a short time got upto 70° while the cpu used the 2,2GHz!

Its a really odd behaviour!

---

### Post by chipppy on 2008-12-12
This is a similar problem that I am having on my laptop.  It is an older ASUS unit with a 2700+ mobile CPU.
My problem is the computer is really slow.  I tried playing 'supertuxkart' and the frame rates as sloooooow eg 0.9fps
I am assuming that it is a reduced CPU issue

I noticed reading through the help for Gnome Power Management that there should be a button to change the speed of the CPU when it is on battery.

I checked my preference screen and that button was not available.  I read through the help again and it mentioned that the gconf policy keys may be disabled by the system admistrator and as such some options may be hidden.

I am a newbie to Linux and this whole command line bit.  I started the 'terminal' and had a go a gconfd-2 but nothing happen.  I logged in a root and tried again but still nothing.

I would like to get the CPU speed button onto Gnome Power Manager so that I can see what its setting are and see if this help me out but I dont have a clue how to do this.
You guys see to be knowledgable on in this area would you be able to step me through this process.  I thought as it seems to be in the same area as your problem if might help you spot something else to lead you down the path to fix your problems.

Cheers
chipppy

---

### Post by zika on 2008-12-12
I've tried ```
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
cpufreq-selector -c 2 -g performance
```on my Phenom X3 AMD and got 2100 instead of 1050MHz on all 3 cpu's when checked in ```
cat /proc/cpuinfo
``` Am I now overclocking the CPU or is it running now 'normal'?

I've put these commands in /etc/rc.local so that it becomes 'default' ... ;)

---

### Post by nick09 on 2008-12-12
Seems normal since you have two cores clocked at 3GHz when you add them up. Its just that the Ubuntu seems to be made so it does not use all of the processor to save power.

---

### Post by Sylchat on 2008-12-22
> **zika said:**
> Am I now overclocking the CPU or is it running now 'normal'?

If you bought a Phenom X3 AMD 2.1 GHz, then you're not overclocking it, but it's running at full speed (and there is no X3 1.5GHz anyway). Overclocking is when you're running the CPU at 'unofficial' frequences.
Scaling is good to save battery and have a lower CPU temp.

---

### Post by Sylchat on 2008-12-22
> **chipppy said:**
> This is a similar problem that I am having on my laptop.  It is an older ASUS unit with a 2700+ mobile CPU.
My problem is the computer is really slow.  I tried playing 'supertuxkart' and the frame rates as sloooooow eg 0.9fps
I am assuming that it is a reduced CPU issue

Hi Chippy,

If your computer is slow when running SuperTuxKart, the problem may be linked also to the graphic chip or the amount of RAM you have. In order to be sure, you need to analyse if everything is slow, or just 3D games, and if it happens on power and/or on battery.

And... don't be scared by the command line, it is your friend :)

First try to solve the main problem by any means you have. When you solved it, you can fix the button issue.

---

### Post by zika on 2008-12-22
> **Sylchat said:**
> If you bought a Phenom X3 AMD 2.1 GHz, then you're not overclocking it, but it's running at full speed (and there is no X3 1.5GHz anyway). Overclocking is when you're running the CPU at 'unofficial' frequences.
Scaling is good to save battery and have a lower CPU temp.

Yes, the speed was 1050 not 1500, my mistake (typo).

Since this is a desktop machine I wondered should it run at full speed (now I know that). Now I know more about scaling, at that time I was just surprised to see it running at half speed.

After learning more abut scaling methods I am more in doubt what choise is better: faster machine or cooler CPU. Since I do not play games probably I will stick to latter.

Thank You.

---

### Post by Sylchat on 2008-12-22
> **zika said:**
> 
After learning more abut scaling methods I am more in doubt what choise is better: faster machine or cooler CPU. Since I do not play games probably I will stick to latter.

Thank You.

Indeed, I use the CPU scaling too. I guess the cooler the components are, the longer they live.
With the CPU scaling applet, I saw that the frequence switch is made very fast.

---

### Post by zika on 2008-12-22
> **Sylchat said:**
> Indeed, I use the CPU scaling too. I guess the cooler the components are, the longer they live.
With the CPU scaling applet, I saw that the frequence switch is made very fast.

Yes, but the algorithms used for scaling nowadays are not too clever. If Your applications are not nice (with and without quotes, in general and in programmer's presumed way) then You will end up with a machine at half speed more time than You really want to. CPU applets are not good indicator. As long You can see the switch after Your action the algorithm is most probably bad.

One more thing, while keeping a CPU cooler it's keeping a fan more indecisive about the speed it should run. Since I'm a mathematician I will try to work, when I get some time, to see about optimality of these issues.

---

### Post by Donalb on 2008-12-22
Wow, thanks very much. I noticed this on a new 2.2gHz core duo, and didn't know what was going on. Thanks for your help....!

---

### Post by Donalb on 2008-12-22
Hey Chippy, Since your question wasn't answered;

Right-click on your Menubar. Select >Add to panel. Scroll down to >CPU Frequency Scaling Monitor. Select >Add.
 Now it should appear in your menubar. From this you can select your Preferred CPU speed and config.

I use Conky and hadn't used the Frequency Monitor.
I noticed on Conky that the freq was generally sitting at 800mhz only hitting 2.2ghz occasionally. I wasn't worried thinking it was a demand situation as this thread as indeed shown me!

Cheers

---

### Post by Doc Hoss on 2009-01-10
Well, after having posted this a good while back, and futzing around with god-knows-how-many things, it seems my processor and scaling are getting along nicely.  If I remember correctly, it was a combination of having the powernowd and other scaling tools set up correctly.  

Thanks for all the help and glad to see that this thread has helped others too!

Since my problem is solved, I'll mark the thread thus.

---

### Post by audebruin on 2010-10-16
After a 2 hour search on the internet i found out about this solution and it worked (thanks for the solution). I did a bios reset and memtest86 showed a cpu (AMD 3200+) speed of 1000MHz.

In Ubuntu I added CPU Frequency Scaling Monitor to the panel and it was set on 1GHz. I changed it to 2GHz and all was normal again.

---

### Post by zika on 2010-10-16
Substitute &#8222;ondemand&#8220; with &#8222;performance&#8220; in /etc/init.d/ondemand...

Boy, You rose his dead thread from deeply frozen...

---

