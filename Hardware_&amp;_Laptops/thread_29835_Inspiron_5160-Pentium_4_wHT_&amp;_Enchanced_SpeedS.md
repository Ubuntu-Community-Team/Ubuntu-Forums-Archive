---
title: "Inspiron 5160-Pentium 4 w/HT &amp; Enchanced SpeedStep Technology"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by hacktix on 2005-04-26
As I have googled the hell out of this, i still can't figure out my problem.
As the subject says I have a p4 on my laptop. Now I remember on Suse I was able to get the cpu to downclock and save battery. 1:30 of battery time is bull, when in winxp i can get 3:30. Now I've heard alot about applications and scripts, and I'll go down the list of ideas that i tried and why they didn't work. 

cpufreq/cpufreqd - didn't work because I can't find a required library for the file to run. And yes I googled this, and might have found an RPM to fix it, but I think its the same rpm i tried a week ago. 
the library error:
> cpufreq-info
cpufreq-info: error while loading shared libraries: libcpufreq.so.0: cannot open shared object file: No such file or directory


echo'ing to proc/../../cpu0/throttling t7 and all that. yeah I got the cpu to operate at the lowest frequency of 233 mhz, but for some reason all it did was that, slow down the cpu, but the battery still drained fast, while my terminal was slow. 

Powernowd - Well when I run it

> powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]


Thats what I get in the terminal, and when i tried to restart the service or daemon, it said my cpu didn't support frequency scaling. If my CPU doesn't support it why does SpeedSwitchXP in WinXP let me downlock the cpu to 233mhz, kill the fans, and power, so that I can get my battery?

the little gnome applet won't even tell me my cpu speed. I did get teh battery aplet working by editting grub bootloader to force acpi on, but turn it off on the pci, so that i don't lose my ethernet like on my desktop....maybe i'll try letting acpi onthe pci too. 

I've been looking at posts here ont he forum, and theres some trick to manually change a setting in the /sys/ directory, but the setting under CPU0 in sys isn' tthere. cpu0 is empty. But in proc i was able to echo "7" > throttling to get the cpu to T7, which i think is 233 mhz, all I know is it really slowed teh computer, but didn't actually give me back any battery as far as I know. Is there anyway i can get my battery to last as long as in winxp pro?

Example of readout in the sys:
> circusb0y@circus2go:/sys/devices/system/cpu/cpu0$ pwd
/sys/devices/system/cpu/cpu0
circusb0y@circus2go:/sys/devices/system/cpu/cpu0$ ls
circusb0y@circus2go:/sys/devices/system/cpu/cpu0$


CPU Info:
> circusb0y@circus2go:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3190.307
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6324.22



I'm really loving ubuntu, Wifi works right away with my netgear, Cedega is running STEAM, aside from the need to get Divx and Mp3's to work right in totem, Ubuntu is hands down the easiest distro to work with, but its not a glorified windows replacement, you do need to learn something in order to operate it. 

I just want to say thank you very much for your time and attention, especially this being my first post, but i hope to hang around and push ubuntu as far as it will go.

---

### Post by alastair on 2005-04-26
Not sure.

Are there any relevant CPU/ACPI logs in the syslog i.e. /var/log/syslog?

Might be worth a look.

Also, see what modules are loaded : lsmod

---

