---
title: "Conky"
date: 2023-02-11
forum: Hardware
---

### Post by klapvogn on 2023-02-11
Hi,

I have installed ```
sudo apt install conky-all
```

And im trying to setup it up with my AMD GPU with cpu and core temps but so fare I have failed :-(

sensors info:
```

sensors
corsaircpro-hid-3-6
Adapter: HID adapter
in0:          12.10 V  
in1:           4.98 V  
in2:           3.41 V  
fan1 4pin:   1511 RPM
fan2 4pin:   1509 RPM
temp1:        +34.2°C  
temp2:        +49.6°C  
temp3:        +29.3°C  
temp4:        +30.0°C  

k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +37.8°C  
Tccd1:        +39.5°C  

nvme-pci-0100
Adapter: PCI adapter
Composite:    +37.9°C  (low  =  -0.1°C, high = +74.8°C)
                       (crit = +79.8°C)

amdgpu-pci-0900
Adapter: PCI adapter
vddgfx:      712.00 mV 
fan1:           0 RPM  (min =    0 RPM, max = 3300 RPM)
edge:         +51.0°C  (crit = +110.0°C, hyst = -273.1°C)
                       (emerg = +115.0°C)
junction:     +51.0°C  (crit = +105.0°C, hyst = -273.1°C)
                       (emerg = +110.0°C)
mem:           +0.0°C  (crit = +105.0°C, hyst = -273.1°C)
                       (emerg = +110.0°C)
slowPPT:      19.00 W  (cap = 125.00 W)

```

And would like it to match 
```
#--------------------+
# TEMPS AND FAN SPEED
#--------------------+
${voffset 2}${color1}${font :size=8:bold}TEMPS AND FAN SPEED ${hr 1}${font}
#CPU
${color1}CPU: ${color3}${execi 2 sensors | grep "Package id 0" | awk '{print "            " $4,$5$6$7$8$9$10}'}
${color3}${execi 2 sensors | grep "Core" | awk '{print $1,$2"        "$3,$4$5$6$7$8$9}'}
#GPU
${color1}GPU: ${color3}${goto 70}${nvidia temp}°C (threshold=${nvidia threshold}°C,ambient=°C)
#CPU fan Speed
${color1}CPU fan speed:${color3}${execi 2 sensors | grep "fan" | awk '{$1=""; print $0}'}
```

I have notived this:
```
${color1}GPU: ${color3}${goto 70}${nvidia temp}°C (threshold=${nvidia threshold}°C,ambient=°C)
```
which is for nvidia

Can someone help me figure this out?

---

### Post by mIk3_08 on 2023-02-12
nvidia wont work on AMD GPU hardware. AMD GPU depend on radeontop. You  should have to install radeontop first before you apply the following  codes below for your AMD GPU.
In my desktop this command below will show the GPU % usage.
```
${offset 1}${color slate grey}GPU: ${color }${execi 5 radeontop -d- -l1 | grep -o 'gpu [0-9]\{1,3\}' | cut -c 5-7 }%
```

This is the graph of my CPU in General
```
${offset 1}${color slate grey}CPU GRAPH:
${offset 1}${color }${cpugraph 20, 198 000000 ffffff}
```

4 cores of my CPU. Regards and cheers
```
${offset 1}${color }Core-1: (${cpu cpu0}%)
${offset 1}${color }${cpubar cpu0 3}
${offset 1}${color }Core-2: (${cpu cpu1}%)
${offset 1}${color }${cpubar cpu1 3}
${offset 1}${color }Core-3: (${cpu cpu2}%)
${offset 1}${color }${cpubar cpu2 3}
${offset 1}${color }Core-4: (${cpu cpu3}%)
${offset 1}${color }${cpubar cpu3 3}
```

---

### Post by klapvogn on 2023-02-12
> **mIk3_08 said:**
> nvidia wont work on AMD GPU hardware. AMD GPU depend on radeontop. You  should have to install radeontop first before you apply the following  codes below for your AMD GPU.
In my desktop this command below will show the GPU % usage.
```
${offset 1}${color slate grey}GPU: ${color }${execi 5 radeontop -d- -l1 | grep -o 'gpu [0-9]\{1,3\}' | cut -c 5-7 }%
```

This is the graph of my CPU in General
```
${offset 1}${color slate grey}CPU GRAPH:
${offset 1}${color }${cpugraph 20, 198 000000 ffffff}
```

4 cores of my CPU. Regards and cheers
```
${offset 1}${color }Core-1: (${cpu cpu0}%)
${offset 1}${color }${cpubar cpu0 3}
${offset 1}${color }Core-2: (${cpu cpu1}%)
${offset 1}${color }${cpubar cpu1 3}
${offset 1}${color }Core-3: (${cpu cpu2}%)
${offset 1}${color }${cpubar cpu2 3}
${offset 1}${color }Core-4: (${cpu cpu3}%)
${offset 1}${color }${cpubar cpu3 3}
```

Thanks a million :)
Is it possible to get the ?```
°C
```

---

### Post by mIk3_08 on 2023-02-12
> **klapvogn said:**
> Thanks a million :)
Is it possible to get the ?```
°C
```
Here is the conky code for the temperature of your CPU in Celsius.
```
${offset 1}${color slate grey}CPU TEMP:${color } ${acpitemp}C
```
Here is the conky code for the frequency of your CPU. Regards and cheers
```
${offset 1}${color slate grey}CPU FREQ:${color } ${freq_g}GHz
```

---

### Post by klapvogn on 2023-02-12
Thank, im not getting any temps from
```
${offset 1}${color slate grey}CPU TEMP:${color } ${acpitemp}C
```

---

### Post by klapvogn on 2023-02-12
And hopefully you can answer this to : 

```
sudo apt-get install inxi
```
is a fine tool also, so I would use that to. when I do this in Terminal:
```
inxi -G | grep 'OpenGL: renderer:' | cut -c 20-41
```
I get: ```
AMD Radeon RX 5500 XT
```

but the output in conky is blank?

---

### Post by mIk3_08 on 2023-02-12
Can you please run the command below and post the results here in thread wrap with code. Regards and cheers.
```
hostnamectl
```

---

### Post by deadflowr on 2023-02-12
This is supposedly your cpu temps

```
k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +37.8°C  
Tccd1:        +39.5°C  
```
with tccd1 as the actual cpu real temp and tctl as the fan controlling temp, or something. (I don't know, that's just what I got from a very cursory look up, could be completely wrong)

Most of your sensors output are weird and foreign to me so you'll probably have to wait on someone who also has ( I'm guessing ) a ryzen system.

Perhaps you could run the Ubuntu forums script which would provide information about the system, in general.
See: [https://ubuntuforums.org/showthread.php?t=2475931]("https://ubuntuforums.org/showthread.php?t=2475931")

I mean, we know very little about the system at hand like which kernel is being used, or what version of Ubuntu is installed.
Running the script will help everyone get a fuller picture of what is what.

---

### Post by mIk3_08 on 2023-02-12
> **klapvogn said:**
> Thank, im not getting any temps from
```
${offset 1}${color slate grey}CPU TEMP:${color } ${acpitemp}C
```
You can also try this one. Maybe it will help you. [Click here]("https://askubuntu.com/questions/235713/how-to-detect-processor-correct-temperature-in-conky") Regards and cheers

---

### Post by klapvogn on 2023-02-13
```

 Static hostname: klapvogn-Computer
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: d0ee8e6f943e458582ae6285a86e6e75
         Boot ID: 50a82e2216694952af36c25b732a2784
Operating System: Ubuntu 22.04.1 LTS              
          Kernel: Linux 5.15.0-60-generic
    Architecture: x86-64
 Hardware Vendor: MM-Vision
  Hardware Model: Computer

```

---

### Post by mIk3_08 on 2023-02-14
> **klapvogn said:**
> ```

 Static hostname: klapvogn-Computer
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: d0ee8e6f943e458582ae6285a86e6e75
         Boot ID: 50a82e2216694952af36c25b732a2784
Operating System: Ubuntu 22.04.1 LTS              
          Kernel: Linux 5.15.0-60-generic
    Architecture: x86-64
 Hardware Vendor: MM-Vision
  Hardware Model: Computer

```
Just follow what deadflowr says. so that we can check your hardware. This might be at your hardware specification. Regards and cheers.
> **deadflowr said:**
> 
Perhaps you could run the Ubuntu forums script which would provide information about the system, in general.
See: [https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

I mean, we know very little about the system at hand like which kernel is being used, or what version of Ubuntu is installed.
Running the script will help everyone get a fuller picture of what is what.

---

