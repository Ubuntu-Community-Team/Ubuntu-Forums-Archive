---
title: "Sandy Bridge Overclocking and Ubuntu"
date: 2011-01-22
forum: Hardware
---

### Post by zzjing on 2011-01-22
I overclocked my i5-2500K to 4.3GHz with turbo disabled in the BIOS.  The overclock was tested stable in Windows and CPU-Z shows the correct speed.  But when I boot into Ubuntu, /proc/cpuinfo only reports the default speed of 3.3GHz.  CPU Frequency Monitor shows the same 3.3GHz and informs me that CPU Frequency Scaling is unsupported.  It looks like Ubuntu is ignoring the overclock.  How did this happen and how can I fix it?  Thanks in advance.

---

### Post by technicalsquash on 2011-01-30
I just put together a 2600k (3400mhz) system with the intel p8p67 pro. In the bios I adjusted my max turbo speed to something north of 4400mhz, however it appears that any speed above the 3400mhz is simply displayed as 3401. I can't find a reliable tool to measure actual frequency.

lscpu while running  'stress -c 10':
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                8
Thread(s) per core:    2
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Stepping:              7
CPU MHz:               3401.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K

---

### Post by technicalsquash on 2011-01-30
After re-reading your post, one thing stuck out. Overclocking of thses through the bios is done by adjusting the maximum Turbo multiplier. If you disable Turbo mode, something else (a windows OC utility, for example) will have to turn it back on in order for you to go beyond the stock multiplier. These seems to be no negative to the Turbo method beyond not being able to just force that maximum speed.

---

### Post by Tamale on 2011-02-01
I have the same problem.. also a p8p67 deluxe motherboard, also trying to run overclocked.

the problem for me is that i don't even see how you can overclock the i7 2600k without using turbo.. the multiplier tops out at 34.. only the turbo multipliers go all the way up, and in ubuntu, they don't seem to be 'respected', regardless of whether i'm using the 'os' setting in bios or the 'bios' setting.

it all works fine in windows, however.. extremely frustrating and confusing!

---

### Post by technicalsquash on 2011-02-01
This was pointed out to me in another thread:
[http://ubuntuforums.org/showpost.php?p=10414999&postcount=26](http://ubuntuforums.org/showpost.php?p=10414999&postcount=26)

you need this additional tool to accurately measure speed in Turbo mode. install the 'stress' package and run `stress -c [number of cores]` and you should see your overclocked speed. Mine looks like this:
core CPU   %c0   GHz  TSC   %c1    %c3    %c6    %c7   %pc2   %pc3   %pc6   %pc7                                                                                                                                                             
         100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   0   0 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   0   4 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   1   1 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   1   5 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   2   2 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   2   6 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   3   3 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00                                                                                                                                                            
   3   7 100.00 4.64 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00

---

### Post by Tamale on 2011-02-04
Ok, finally figured out how to get that compiled and ran.. and it worked!

after loading the msr kernel module and running the turbostat program, I see the actual frequencies properly.

now, how do you get the frequency scaling applet to respect these 'actual' values?  is there some larger issue at play here for getting this stuff supported 'out of the box' ?  it seems a little ridiculous to have to do all this just to know how fast my computer is running!

is there ANYTHING like the windows utility cpu-z for ubuntu?

please help!

---

### Post by guadafan on 2011-09-11
Yes, CPU-Z running under wine.

---

