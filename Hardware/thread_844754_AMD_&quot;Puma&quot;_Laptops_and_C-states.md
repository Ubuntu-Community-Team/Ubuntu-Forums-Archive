---
title: "AMD &quot;Puma&quot; Laptops and C-states"
date: 2008-06-29
forum: Hardware
---

### Post by *Legion* on 2008-06-29
I just purchased a Toshiba U405D, which features the new AMD "Puma" hardware platform.

The CPU is a Turion X2 RM-70. According to AMD, one of the features of the Puma is that "[C-states are entirely and automatically controlled by the CPU]("http://www.behardware.com/news/9721/computex-amd-launches-the-puma.html"), without a single required action from the operating system".

Powertop doesn't see the C-states, so I have to wonder if they're working at all. Any ideas on finding this out?

---

### Post by Trebaruna on 2008-08-02
If you've found an answer by now, please post.

Meanwhile, I also got a laptop with this processor, and indeed, powertop doesn't see C-states, and the frequency scaling applet reports that scaling is unsupported. This occurs in x86 and x86-64 builds, both updated as of yesterday (31 July) with default repos and using the fglrx driver for the 780v/sb700 chipset.
Right now I'm using the bundled microsoft OS, and it does feel rather cooler than in Ubuntu; it is in fact barely warmer than ambient as opposed to the hot to the touch vent when using the latter.
Considering the hardware didn't technically exist when 8.04 released, I think it may simply be a matter of the kernel not knowing what to do with the processor.
For me, updating to intrepid alpha 3 resulted in a system that kept dropping me to the terminal. I'll try just plucking the alpha 3 CD from the site, but right now I do not have access to fast internet. Also, I'm on holiday.

---

### Post by Trebaruna on 2008-08-04
In case anyone might be interested:
The AMD Turion RM-70 (codename Griffin, part of the Puma platform) is supported in the current kernel, 2.6.26.1
Currently, I am on Ibex alpha 3 and haven't tried in 8.04 yet, but it will probably work.
Following the master kernel thread here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) one installs the latest kernel.
Ubuntu loads cpu modules according to /etc/init.d/loadcpufreq which currently will not load the proper module when it encounters a processor family higher than 15. Phenom is 16, Griffin is 17, AFAIK.
Find out your processor's family like so, you'll see one line per cpu/core:
```
cat /proc/cpuinfo | grep family
```Find the following section in the script...
```
AuthenticAMD*)
# Hurrah. This is nice and easy.
            case $CPU_FAMILY in
                5)
                    # K6
                    MODULE=powernow-k6
                    ;;
                6)
                    # K7
                    MODULE=powernow-k7
                    ;;
                15)
                    # K8
                    MODULE=powernow-k8
                    ;;
            esac
            ;;
```...and change "15)" to "15|16|17)". Do not boot the ubuntu kernels with this, they will not work. Only use your newly compiled vanilla kernel.

One can also manually load the module:
```
sudo modprobe powernow-k8
```Using this driver I'm seeing a significant reduction in heat from my machine.

---

### Post by thegnark on 2008-08-20
Do you see actual CPU scaling support? I compiled a new 2.6.26 kernel and saw an immediate improvement, even on bootup... but still after loading powernow-k8, the cpu frequency monitor applet only shows the max 2.4GHz speed

---

### Post by morbyte on 2008-08-26
> **Trebaruna said:**
> In case anyone might be interested:
The AMD Turion RM-70 (codename Griffin, part of the Puma platform) is supported in the current kernel, 2.6.26.1
Currently, I am on Ibex alpha 3 and haven't tried in 8.04 yet, but it will probably work.
Following the master kernel thread here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) one installs the latest kernel.
Ubuntu loads cpu modules according to /etc/init.d/loadcpufreq which currently will not load the proper module when it encounters a processor family higher than 15. Phenom is 16, Griffin is 17, AFAIK.
Find out your processor's family like so, you'll see one line per cpu/core:
```
cat /proc/cpuinfo | grep family
```Find the following section in the script...
```
AuthenticAMD*)
# Hurrah. This is nice and easy.
            case $CPU_FAMILY in
                5)
                    # K6
                    MODULE=powernow-k6
                    ;;
                6)
                    # K7
                    MODULE=powernow-k7
                    ;;
                15)
                    # K8
                    MODULE=powernow-k8
                    ;;
            esac
            ;;
```...and change "15)" to "15|16|17)". Do not boot the ubuntu kernels with this, they will not work. Only use your newly compiled vanilla kernel.

One can also manually load the module:
```
sudo modprobe powernow-k8
```Using this driver I'm seeing a significant reduction in heat from my machine.

[SIZE=1]for me, this works (family 17 - which is, in my case called a "turion mobile x2" or so) if i a) do not start the fglrx (ati) driver on startup or b) move the /etc/rc2.d/S20fglrx-driver to /etc/rc2.d/S29fglrx-driver so it loads later than normal... dunno why, but that makes the kernel oopses go away (yet to be proved, but looks promising)[/SIZE]

edit: it looks like i get powernow-k8 working if it is entered in /etc/modules, directly below "loop" i simply added the line "powernow-k8" and now it works flawlessly.

---

### Post by 92sho16 on 2008-10-16
I seem to be having trouble with this, when i gedit /etc/init.d/loadcpufreq the file is emtpy, running 8.10 with most current kernel 2.6.27-7. What can i do, im trying to improve my battery life on my tx2500 and the fan is constantly spinning i figured this is where i start?

---

