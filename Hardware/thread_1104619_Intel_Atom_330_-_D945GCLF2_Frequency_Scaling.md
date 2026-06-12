---
title: "Intel Atom 330 - D945GCLF2 Frequency Scaling"
date: 2009-03-23
forum: Hardware
---

### Post by shasi on 2009-03-23
Hello everyone,

I've installed Ubuntu on a newly assembled desktop with Intel Atom 330 processor. I was trying to scale the CPU frequency as it was consuming a lot of power. I've tried all the methods used to scale Atom 270 and they are not working.

Does anyone know if we can scale Atom 330 processor? If yes, help required!

Thank you,
Shasi

---

### Post by cariboo on 2009-03-23
What kind of power supply have you got connected to that motherboard? I have an Atom 230, and the 90 watt power supply that came with the case is designed for the atom 330, so it is a bit of over kill for the 230.

Jim

---

### Post by executor on 2009-03-25
it don`t support Intel SpeedStep, 

look her [http://ark.intel.com/cpu.aspx?groupId=35641](http://ark.intel.com/cpu.aspx?groupId=35641)

---

### Post by vishnumrao on 2009-08-22
> **executor said:**
> it don`t support Intel SpeedStep, 

look her [http://ark.intel.com/cpu.aspx?groupId=35641](http://ark.intel.com/cpu.aspx?groupId=35641)

Does that mean, the frequency can't be scaled at all and the processor will always run at 1.6 GHz?  

I just built a system with an atom dual core 330. The plan was to use this machine as a media server. If the freq is stuck at 1.6 Ghz, its going to be consuming more power (atleast more than it would if the frequency were scaled down!)

Here is the item:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)

I check the cpu frequency on the "CPU Frequency Monitor" applet on the panel. I see the frequency is always 1.6 GHz, though there are many options for lower frequencies. I am able to change the frequency to powersave mode or only performance. The "ondemand", "conservative" options don't work! I haven't tried changing the ferequencies to other frequencies manually.

---

### Post by vishnumrao on 2009-08-27
Frequency scaling is available on the dual core atom 330 (and the single core 230 as well, i think).

I booted up the live cd (or rather usb) installer of jolicloud ( which is ubunutu + some extras) on my MSI nettop and tried playing around with the frequency settings. It is possible to scale the frequency. In fact there are multiple frequency scaling factors. The frequencies are 399 MHz (25%), 599 MHz (37%), 799 MHz (50%), 999 MHz (62%), 1200 MHz (75%), 399 MHz (87%), 1.6 GHz (100%). 

I also checked cpuinfo. Please see output below.

However the dynamic frequency scaling does not work. I tried to set scaling to "Ondemand" or "Conservative", it does not work. But I am able to set it scaling to "Performance" which sets the processor to 1.6 GHz or "powersave" which set it to 399 MHz (the applet reports it as 300 MHz, but /proc/cpuinfo reports 399 MHz).


Can someone shed some light on the frequency scaling on Atom processors? 

```
jolicloud@jolicloud:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 399.999
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3191.85
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 399.999
cache size	: 512 KB
physical id	: 2
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4468.74
clflush size	: 64
power management:

jolicloud@jolicloud:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 599.998
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3191.85
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 599.998
cache size	: 512 KB
physical id	: 2
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4468.74
clflush size	: 64
power management:

jolicloud@jolicloud:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.996
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3191.85
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.996
cache size	: 512 KB
physical id	: 2
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4468.74
clflush size	: 64
power management:

jolicloud@jolicloud:~$
```

---

### Post by pablolie on 2009-11-03
I am curious about the exact same topic. I also have a 330. It is not a *huge* deal since the CPU only consumes 8W, and most of the power goes to the 945 chipset, but nevertheless it would be good to know.

I installed Vista on the same hardware for a friend, and there it seemed to scale up and down (although I have to admit I did not have the time to check in depth).

---

### Post by katakaio on 2009-12-14
I'm also curious about this. I assumed that Ubuntu's CPU scaling tools (like powernowd *et al*) utilized Intel's SpeedStep technology and AMD's Cool'n'Quiet technology. executor correctly stated that the Atom 330 does **not** support SpeedStep, so that explains why Ubuntu can't dynamically adjust the frequency.

However, vishnumrao observed that the frequency can be set manually, so if you really want to underclock the Atom, you could. However, you could only increase the frequency manually, which would be a pain. The Atom's power usage is impossibly tiny, so I would personally save yourself the trouble and let it run at 1.60 GHz. I find that it's just enough power to run a web server and transfer files via SFTP.

But, if there was a way to dynamically adjust the frequency . . . ?

---

### Post by darkforcesjedi on 2010-01-03
I came across this thread trying to find a solution to the same problem. I don't know how to change between the Performance or Powersave profiles, but I did find I could set the scaling factor directly by running this as root:

```
echo X > /proc/acpi/processor/CPU0/throttling
```

So I went ahead and wrote a script ("savepower") that periodically checks the CPU load and increases or decreases the throttling based on usage.

I use vmstat to get CPU idle %. For some reason it always returns 86% the first time, so I run "vmstat 1 2" to run it twice 1 second apart and grab the second result.

The way I have it set up, it increases throttling by 1 level (1/8 of rated clocks) each second that CPU usage is less tan 5%. It decreases throttling similarly when usage is over 15%. This works well for my file server. Samba transfers start out a little slow, but increase to the full gigabit speed in about 10 seconds. If you actually use it interactively, I would change max_throttle to 6 (corresponds to 400MHz) and change the line "((curstate--))" to "curstate=0" to disable throttling as soon as it detects usage.

To run the script at boot, create a new script ("start_savepower") with the line "/bin/bash /path_to_the_script/savepower &" (inputting the appropriate path the the script -- don't forget the & at the end) and use the "update-rc.d" command to add start_savepower to the startup scripts.

If you run it from the console it'll tell you what it's doing. According to my UPS, it uses approximately 8 Watts less when in T7 (12.5% clock rate), but I have my 330 overclocked to 2 GHz. If you are running at the rated 1.6GHz, then you might save 4-6 Watts. In the ends it probably wasn't worth it. 8-[

```
# !/bin/bash

if [[ `whoami` != root ]]; then

  echo "Must be root!"
  exit 1

fi

min_load=5
max_load=15
max_throttle=7
min_throttle=0

thr="/proc/acpi/processor/CPU0/throttling"

while [ 1 ]
do
  # parse CPU idle time from vmstat
  t=`vmstat 1 2 | sed 's/\W\W*/|/g'|tail -n 1|cut -d \| -f 16`

  ((load=100-$t))

  load_formatted="00$load"
  load_formatted=${load_formatted:(-3)}

  if [[ $load -lt $min_load ]]; then
    # cpu is idle, increase power saving

    # get current throttle state
    curstate=`cat $thr | grep "*"`
    curstate=${curstate:5:1}

    msg="$load_formatted% CPU -- full power saving"

    #get next throttle state
    ((curstate++))
    if [[ $curstate -le $max_throttle ]]; then
      echo $curstate > $thr
      msg="$load_formatted% CPU -- power saving set to $curstate"
    fi

  elif [[ $load -gt $max_load ]]; then
    # cpu is loaded, decrease power saving

    # get current throttle state
    curstate=`cat $thr | grep "*"`
    curstate=${curstate:5:1}

    msg="$load_formatted% CPU -- min power saving"

    #get next throttle state
    ((curstate--))
    if [[ $curstate -ge $min_throttle ]]; then
      echo $curstate > $thr
      msg="$load_formatted% CPU -- power saving set to $curstate"
    fi
  else
    msg="$load_formatted% CPU -- throttle not changed"
  fi

  echo $msg
done
```

---

### Post by Jose Catre-Vandis on 2010-01-17
Can anyone explain why htop reports 4 cpus on my Asus EB1012. This has the same Atom 330?

Also perversely for this thread, how to get the best performance out of the processor - am running 32 bit Xubuntu?

---

### Post by Groodles on 2010-01-21
> **Jose Catre-Vandis said:**
> Can anyone explain why htop reports 4 cpus on my Asus EB1012. This has the same Atom 330?


There's probably a setting in your bios about reporting CPU cores to the OS.  With Hyper-threading enabled, the BIOS will report the 4 Threads as individual cores.

---

### Post by snowpine on 2010-01-21
> **Jose Catre-Vandis said:**
> Can anyone explain why htop reports 4 cpus on my Asus EB1012. This has the same Atom 330?

Also perversely for this thread, how to get the best performance out of the processor - am running 32 bit Xubuntu?

Groodles is correct... hyperthreading makes single core atoms look like double cores, and double cores look like quad cores.

32 bit Xubuntu is probably a good choice (haven't personally tried it on my Atom 330). I am running 64-bit Fedora 12 on mine, not the fastest thing in the world but fine for my needs. You also could use lpia (low power intel architecture) Ubuntu if you wanted, I suppose. I haven't seen any benchmarks comparing these 3 architectures on the Atom 330.

ps Frequency scaling works out-of-the-box in fedora.

---

### Post by Jose Catre-Vandis on 2010-01-22
Thanks for the replies. In understand now about atoms :)

What I meant in terms of performance was in terms of tweaking the dual cores to work at their best. Is this done by default or is there more I could do to get the cbest out of them. Xubuntu is simply my distro of choice but it works well enough :)

---

### Post by userid on 2010-01-27
Thanks darkforcesjedi, just the ticket!

> ps Frequency scaling works out-of-the-box in fedora.

Really? Is that a similar software side hack as above?

---

### Post by ojobson on 2010-03-14
I have the atom 330 Little Falls 2 board from intel - I wouldn't worry about CPU scalling as the northbridge consumes nearly 3 times more power than the CPU..

[http://ark.intel.com/Product.aspx?id=35641&processor=330&spec-codes=SLG9Y]("http://ark.intel.com/Product.aspx?id=35641&processor=330&spec-codes=SLG9Y")

[http://ark.intel.com/chipset.aspx?familyID=28994]("http://ark.intel.com/chipset.aspx?familyID=28994")

---

### Post by Brian88 on 2010-12-06
Sorry for ressurecting an old thread, but I had two Intel D945GCLF (Atom 230) and Ubuntu Lucid (10.04) automatically configures the CPU Frequency Scaling on one of the machines. 

This machine serves as my main desktop doubling as a web, mail and FTP server, so I usually just need half of the processor speed most of the time. Turning the processor speed from 1.60Ghz to 800Mhz reduces +- 2W. 

As with the others say, most of the power are consumed by the 945 VGA chipset.

The processor itself (in the case of 230) consumes 4W. So, at most you only could save 4W - if you set it to 133Mhz which is really slow even for GNOME. You would better disable Compiz (if you're running a server or a media center), because you won't need cube effects while watching a movie :D

PS. The strange thing is that on the second D945GCLF I had to *sudo modprobe p4_clockmod* to get CPU scaling. It looks like that I had entered those commands on the first D945GCLF long time ago, as the harddrive installed in this computer is an old HDD from a 2001 Pentium 4 system.

---

