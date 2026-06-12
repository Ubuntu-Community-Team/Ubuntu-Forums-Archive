---
title: "QUIET!!-- please?!?"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by shorshe on 2005-03-24
Could you please point me to a tutorial on how to get a pentium-m to run in his most quiet state (lowest possible cpu feq)?

Thanks

---

### Post by alastair on 2005-03-24
No tutorial, but you could start by looking at the "powernowd" service (a cpufreq interface daemon) :

man powernowd

Also check the init script for it (/etc/init.d/powernowd).

---

### Post by rosslaird on 2005-03-24
[QUOTE=shorshe]Could you please point me to a tutorial on how to get a pentium-m to run in his most quiet state (lowest possible cpu feq)?

Thanks[/QUOTE]
 There are dozens of factors that influence quietness. Try looking at Mike Chin's site, silentpcreview.com, for more info.
I am running a custom designed system (put together by Mike Chin) that I cannot hear on the quietest day.

---

### Post by shorshe on 2005-03-25
ok i looked into powernowd... 
I did set it's parameters in /etc/default/powernowd to:
OPTIONS="-q -p 1500 -m 2 -l 50 -u 95"

but this didn't have any effect... 
(btw i have a Toshiba m30X wich ist perfeclty quiet under Windows)

I then learned that my kernel boots with acpi=off... i figure powernowd relies on acpi?

Unfortunateley I can't boot with acpi=on

---

### Post by songochain on 2005-03-25
[QUOTE=shorshe]Could you please point me to a tutorial on how to get a pentium-m to run in his most quiet state (lowest possible cpu feq)?

Thanks[/QUOTE]
 May be it works [http://www.ubuntuforums.org/showthread.php?t=14864&highlight=powernowd](http://www.ubuntuforums.org/showthread.php?t=14864&highlight=powernowd)

---

### Post by shorshe on 2005-03-26
i'm stuck:

/etc/init.d/powernowd restart says:

[...]
CPU frequency scaling not supported  :-? 

cat /proc/cpuinfo gives me that:

[FONT=Courier New]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.50GHz
stepping        : 6
cpu MHz         : 1499.178
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 2965.50[/FONT]

... help anyone?

----edit-------

ok i got one step further....

modprobe "p4-clockmod" enables the possibillity for powernowd to see and set the cpufrequency... now my cpu runs at 12% speed, But the fan isn't quiet at all (Which he is in Windows). 
I figure p4-clockmod is for pentium4 Processors... is there a similar thing for pentum-m processors?

-----edit2------------
The right module would be "speedstep-centrino".
But:
modprobe "speedstep-centrino"

says:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

 ](*,)

---

### Post by songochain on 2005-03-27
[QUOTE=shorshe]i'm stuck:

/etc/init.d/powernowd restart says:

[...]
CPU frequency scaling not supported  :-? 

cat /proc/cpuinfo gives me that:

[FONT=Courier New]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.50GHz
stepping        : 6
cpu MHz         : 1499.178
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 2965.50[/FONT]

... help anyone?

----edit-------

ok i got one step further....

modprobe "p4-clockmod" enables the possibillity for powernowd to see and set the cpufrequency... now my cpu runs at 12% speed, But the fan isn't quiet at all (Which he is in Windows). 
I figure p4-clockmod is for pentium4 Processors... is there a similar thing for pentum-m processors?

-----edit2------------
The right module would be "speedstep-centrino".
But:
modprobe "speedstep-centrino"

says:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

 ](*,)[/QUOTE]
Have u a compiled kernel or image kernel??

---

### Post by nightmaresc on 2005-03-29
I like cpufreqd better than powernowd myself.  I like controlling the range of throttling.  I think it's available in the univserse.

They do the same type of thing I believe.  Correct me if I'm wrong someone.

Edit:  Also, I have been unable to get my laptop to be fairly quiet using either program.  It doesn't run all the time, but it runs far more often than it does in Windows.

---

### Post by shorshe on 2005-03-31
[QUOTE=songochain]Have u a compiled kernel or image kernel??[/QUOTE]

I use the precompiled kernel (i686) from ubuntu.

Do you think a kernel compiled by myself would be better?

---

### Post by shorshe on 2005-04-03
... i managed to start speedstep-lib... but powernowd still can't throttle the cpu... i'm pretty helpless here.

---

### Post by Darrena on 2005-04-03
This thread might help:
[http://ubuntuforums.org/showthread.php?t=20832&highlight=powernowd](http://ubuntuforums.org/showthread.php?t=20832&highlight=powernowd)

Another item to look at is that cpufreq-detect.sh may not be able to identify your chip.

I *THINK* that it identifies it by the "model name" string in which case your model name doesn't match something in your /var/share/powernowd/cpufreq-detect.sh

My cpufreq-detect.sh has this line which should match your CPU and works on mine (A Pentium M 1.8 ):

	### Intel Pentium 4 / Centrino diveratives
	# jdub wants speedstep_lib.o  (?)
	Intel\(R\)\ Pentium\(R\)\ M\ processor*)

What does your cpufreq-detect.sh look like?

---

### Post by songochain on 2005-04-03
[QUOTE=shorshe]I use the precompiled kernel (i686) from ubuntu.

Do you think a kernel compiled by myself would be better?[/QUOTE]
I dont think. It's rare because a kernel-image has all necessary modules to run ok. U would compile a kernel

---

### Post by shorshe on 2005-04-03
my cpufreq-detect.sh looks like this:
```
#! /bin/sh
# Paul Sladen 2004-09-23

# Revision 0.0.9 2004-12-16  don't show module extensions
# Revision 0.0.8 2004-12-14  extra string CPU id strings
# Revision 0.0.7 2004-12-01  string comparision with '==' is a bashism
# Revision 0.0.6 2004-12-01  PIII Coppermine test, bug #4262

# Class    Family Model Stepping  Mhz  Mhz String
# PIII          6     8        6  850      "Pentium III (Coppermine)"                         # Jean Privat
# PIII          6    11        1 1131 ---- "Intel(R) Pentium(R) III CPU             1133MHz"  # pandora
# PIII-M        6    11        1 1131| 731 "Intel(R) Pentium(R) III Mobile CPU      1133MHz"  # emeritus
# PIII-M        6    11        1  995   ?? "Intel(R) Pentium(R) III Mobile CPU      1000MHz"  # Pascal Hakim
# PIV          15     2        4 1616   ?? "Intel(R) Pentium(R) 4 CPU 1.60GHz"                # dasboot
# PIV-M        15     2        4            Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz          # Bug 1444
# PIV Xeon     15     2        4 2188   ?? "Intel(R) XEON(TM) CPU 2.20GHz"                    # Googled
# P4-M         15     2        7 2188-1196 "Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz"     # Dafydd
# Athlon        6     4        4  750  --- "AMD Athlon(tm) processor"                         # yukidoko (Mako)
# Athlon64     15     4       10 3400?  ?? "AMD Athlon 64 Processor 3400+"                    # iDunno
# Sempron      15     8        2 1600  800 "Mobile AMD Sempron(tm) Processor 2800+"           # Matthew Trent (Ubuntu #1444)

# Code below contains cases for wildcarded matches of:
#
#    Intel(R) Pentium(R) III Mobile CPU
#    Mobile Intel(R) Pentium(R) III CPU - M
#    Pentium III (Coppermine)
#    Intel(R) Pentium(R) M processor
#    Mobile Intel(R) Pentium(R) 4 - M CPU
#    Mobile Intel(R) Celeron(R) CPU
#    mobile AMD Athlon(tm) XP
#    Mobile AMD Athlon(tm) XP
#    AMD Athlon 64 Processor
#    AMD Athlon(tm) 64 Processor

# No .o/.ko module extensions, for feeding the output to 'modprobe' or '/etc/modules'
EXT=''

#are we on a laptop?
LAPTOP=0
if /usr/sbin/laptop-detect; then LAPTOP=1; fi
CPUINFO=/proc/cpuinfo
IOPORTS=/proc/ioports

if [ ! -f $CPUINFO ] ; then
    echo $CPUINFO not detected... >2
    exit 1
fi

MODEL_NAME=`grep '^model name' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`
CPU=`grep -E '^cpud[^:]+:' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`
VENDOR_ID=`grep -E '^vendor_id[^:]+:' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`

MODULE=none
OPTIONS=''

# Too modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
if [ -f $IOPORTS ] && grep -q 'Intel ICH' $IOPORTS ; then
  PIII_MODULE=speedstep-ich$EXT
else
  PIII_MODULE=speedstep-smi$EXT
fi

# Noodles: acpi
# Intel(R) Pentium(R) III Mobile CPU

#CyrixInstead
#GenuineIntel
#CentaurHauls
#AuthenticAMD

case "$VENDOR_ID" in
    GenuineIntel*)
    # x86 machines seem to be happy with /proc/cpuinfo 'model name:'
    case "$MODEL_NAME" in
	### Intel Pentium III diveratives
	# Need to speedstep-ich.o on ICH-2/ICH-3 machines (check if on 440-somethingX southbridge) -mjg59
	# Load speedstep-smi otherwise
	# If coppermine, need to pass "coppermine=1" to the module on load (or something?!) -- FIXME this appears not to be correct:
        #   speedstep_smi: Unknown parameter `coppermine'
	# Rumour has it that there are sub-600Mhz PIII Mobiles's (*without* Speedstep)
	# ...and there's also Deschutes(?) PII's that have speedstep
	Intel\(R\)\ Pentium\(R\)\ III\ Mobile\ CPU*)
	    MODULE=$PIII_MODULE ;;

	# JD: says this works with   cpufreq_userspace
	Mobile\ Intel\(R\)\ Pentium\(R\)\ III\ CPU\ -\ M*)
	    MODULE=$PIII_MODULE ;;

	# https://bugzilla.ubuntu.com/show_bug.cgi?id=4262
	# UNCONFIRMED
	Pentium\ III\ \(Coppermine\)*)
	    MODULE=$PIII_MODULE 
	    ;;

	### Intel Pentium 4 / Centrino diveratives
	# jdub wants speedstep_lib.o  (?)
	Intel\(R\)\ Pentium\(R\)\ M\ processor*)
	    MODULE=speedstep-centrino$EXT ;;

	# Unconfirmed except for the cpuid string; from Kirsch on #ubuntu
	Mobile\ Intel\(R\)\ Pentium\(R\)\ 4\ -\ M\ CPU*)
	    MODULE=speedstep-centrino$EXT ;;

        Intel\(R\)\ Pentium\(R\)\ 4\ Mobile\ CPU*)
	    MODULE=speedstep-centrino$EXT ;;

	### Mobile Intel(R) Celeron(R) CPU 2.00GHz
	# According to: http://www.bay-wolf.com/speedstep.htm#10
	#
	# Q: Does the mobile Intel Celeron processor have the Intel SpeedStep
	# technology feature?
	#
	# A: No, mobile Intel Celeron processors do not have the Intel
	# SpeedStep technology feature. Intel SpeedStep technology is a
	# feature found on all mobile Intel Pentium 4 processors - M and
	# Pentium III processors - M at 600 MHz and above.
	Mobile\ Intel\(R\)\ Celeron\(R\)\ CPU*)
	    MODULE=none ;;

        Intel\(R\)\ Pentium\(R\)\ 4\ CPU*)
            if [ $LAPTOP -eq 1 ]; then
                MODULE=p4-clockmod$EXT
            fi
            ;;

        Intel\(R\)\ Pentium\(R\)\ 4\ Mobile\ Family\ CPU*)
                MODULE=$PIII_MODULE ;;
        esac;;
    AuthenticAMD*)
    case "$MODEL_NAME" in
	### AMD K7 diveratives
	[mM]obile\ AMD\ Athlon\(tm\)\ XP*)
	    MODULE=powernow-k7$EXT ;;
	[mM]obile\ AMD\ Duron\(tm\)*)
	    MODULE=powernow-k7$EXT ;;

	### AMD K8 diveratives
	AMD\ Athlon\ 64\ Processor*)
	    # -iDunno @ #debian-uk
	    MODULE=powernow-k8$EXT ;;
	AMD\ Athlon\(tm\)\ 64\ Processor*)
	    MODULE=powernow-k8$EXT ;;
        [Mm]obile\ AMD\ Sempron\(tm\)\ Processor*)
	    MODULE=powernow-k8$EXT ;;
        [Mm]obile\ AMD\ Sempron\ Processor*)
	    MODULE=powernow-k8$EXT ;;
        [Mm]obile\ AMD\ Athlon\(tm\)\ 64\ Processor*)
	    MODULE=powernow-k8$EXT ;;
        [Mm]obile\ AMD\ Athlon\ 64\ Processor*)
	    MODULE=powernow-k8$EXT ;;
    esac;;
esac

# I think PowerPC's use  /proc/cpuinfo 'cpu:' and just have a number
# NEED TO CHECK
case $CPU_NAME in
    FIXME)
	MODULE=FIXME ;;
esac

if [ "$MODULE" = "none" ] ; then
    echo This processor \"$MODEL_NAME\" is known _not_ to support power-saving. >&2
elif [ "$MODULE" = "FIXME" ]; then
    echo No known cpufreq module for \"$MODEL_NAME\". Please add/report. >&2
    exit 1
elif [ -n "$MODULE" ] ; then
    echo $MODULE $OPTIONS
    exit 0
else
    echo No known cpufreq module for \"$MODEL_NAME\". Please add/report. >&2
    exit 1
fi

exit
``` 

Bute even if the correct module isn't loaded on startup powernowd should be able to set the processor speed if I load the correct module manually and restart powernowd, right?

I started speedstep-lib:
```

modprobe "speedstep-lib"
```
which seems to work (no error messages), but still powernowd says:
```

root@toshi:/usr/share/powernowd # sudo invoke-rc.d powernowd restart:

 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...
 * CPU frequency scaling not supported                                 [ ok ]
```

the only situation in which powernowd supports frequency scaling is when I load "p4-clockmod"...  only in this case the cpu-frequency-indicator in my panel shows a numer at all BUT although it says my CPU runs at 187MHz  :shock:, the fan is loud as ever.

---

### Post by moley on 2005-04-04
I absolutely sympathise, as I have had lots of problems getting my mobile AMD laptop fan to keep quiet.  

At the moment Hoary scales the CPU back to two thirds by default, which is enough to shut the fan off.

One thing which helped me was to get the latest BIOS installed, from the laptop manufacturer Taiwan website.

I thought powernowd and cpufreqd were 2 separate things.  powernowd was mainly for AMD CPUs.

---

### Post by shorshe on 2005-04-10
[QUOTE=moley]I absolutely sympathise, as I have had lots of problems getting my mobile AMD laptop fan to keep quiet.  

At the moment Hoary scales the CPU back to two thirds by default, which is enough to shut the fan off.

One thing which helped me was to get the latest BIOS installed, from the laptop manufacturer Taiwan website.

I thought powernowd and cpufreqd were 2 separate things.  powernowd was mainly for AMD CPUs.[/QUOTE]
 no, you can use powernowd for intel and amd cpus. It talks do many throttling daemons.

... any new suggetstions anyone?

---

### Post by joffen on 2005-04-30
[QUOTE=shorshe]no, you can use powernowd for intel and amd cpus. It talks do many throttling daemons.

... any new suggetstions anyone?[/QUOTE]
Nope, sorry. But I have the same problem. The noise is really annoying!

I have an Intel Celeron M processor, and which reports the following:
```
[johannes@schnappi ~]$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no
[johannes@schnappi ~]$ cat /proc/acpi/processor/CPU0/throttling
<not supported>

```
It seems throttling is impossible here (throttling control: no), but I don't know whether this is because of the processor or just the configuration of Linux. Anyone?


Also, when I run powernowd, I get:
```

ncpus is not a multiple of threads_per_core!

```
Which I really don't understand. (even google hasn't heard of that particular line!)

---

### Post by zgoda on 2005-09-02
[QUOTE=joffen]It seems throttling is impossible here (throttling control: no), but I don't know whether this is because of the processor or just the configuration of Linux. Anyone?[/QUOTE]

AFAIK, Celeron-M cupports frequency scaling downto ~10% of maximum nominal frequency. I got into the same problem with CM360J on my HP nx6110, and I didn't found any resolution. The CPU fan keeps running all the time.

---

### Post by luopio on 2005-09-30
How I got freq-scaling working on a **Mobile Celeron**:
[LIST=1]
[*]sudo modprobe p4-clockmod (also add it to /etc/modules)
[*]install cpufreqd. Powernowd didn't work
[*]configure cpufreqd by editing the file /etc/cpufreq.conf (very straight forward syntax)
[*]start cpufreqd ( /etc/init.d/cpufreqd start )
[/LIST]

Using 5.10 preview release with kernel 2.6.12-9

---

### Post by mjg59 on 2005-10-04
[QUOTE=zgoda]AFAIK, Celeron-M cupports frequency scaling downto ~10% of maximum nominal frequency. I got into the same problem with CM360J on my HP nx6110, and I didn't found any resolution. The CPU fan keeps running all the time.[/QUOTE]

Celerons don't support frequency scaling. It's the main thing that distinguishes them from full Pentium-Ms.

---

### Post by luopio on 2005-10-04
[QUOTE=mjg59]Celerons don't support frequency scaling. It's the main thing that distinguishes them from full Pentium-Ms.[/QUOTE]

Celerons don't, but celeron-Ms do. See my post earlier. It works. I've proven it :cool: . But celeron-ms don't support speedstep and AFAIK with the p4-clockmod you don't get **voltage**-scaling support (don't know if it is even possible at all with celeron-ms)

---

### Post by linuxfanatic1024 on 2006-01-13
[quote=shorshe]ok i looked into powernowd... 
I did set it's parameters in /etc/default/powernowd to:
OPTIONS="-q -p 1500 -m 2 -l 50 -u 95"

but this didn't have any effect... 
(btw i have a Toshiba m30X wich ist perfeclty quiet under Windows)

I then learned that my kernel boots with acpi=off... i figure powernowd relies on acpi?

Unfortunateley I can't boot with acpi=on[/quote]

Have you tried a BIOS update? My Toshiba laptop got a lot quieter (and a lot cooler) once I upgraded the BIOS. You need a blank CD and a CD burner for this. (you don't need Windows to do it)

---

