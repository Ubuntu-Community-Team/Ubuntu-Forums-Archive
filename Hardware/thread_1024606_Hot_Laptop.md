---
title: "Hot Laptop"
date: 2008-12-29
forum: Hardware
---

### Post by danlembek on 2008-12-29
I've got a behemoth laptop, an HP zd7200 model with a widescreen. I've had it for about 4.5 years. It seems as though it is generating more heat than it used to. The fans seem to be working alright, but is it possible that they need to be replaced regularly? Is there any software or hardware to test whether or not the temperature may be affecting performance?

---

### Post by davec64 on 2008-12-29
Hi,

If the laptop is 4.5 years old, there's a fair chance that there's a large build up of dust inside covering the components and fans.
If you're feeling brave I would remove covers and give it a good clean out with an air can.

As far as benchmarking, have a search in Synaptic and see what it comes up with.

All the best:)

---

### Post by linux_tech on 2008-12-29
Cleaning the dust out is a good idea, on laptops, just lift off the keyboard and then with a can of air, spray the dust out away from it.  You should be able to see the air vents on the back of the case, w/ some copper cooling fins.  The dust usually gets stuck in the cooling fins.

To monitor temp, here is a temp sensor pkg you can install-
[http://www.gnomefiles.org/app.php?soft_id=1065](http://www.gnomefiles.org/app.php?soft_id=1065)

To cool the laptop, there are two common ways- regulate the fan speed and/or change the cpu frequency scaling, both methods often work.

To regulate the fan speed you want to install i8kutils/gkrellm 
[http://packages.debian.org/etch/i8kutils](http://packages.debian.org/etch/i8kutils)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_for_Dell_Laptops_and_install_Gkrellm_plugin_.28i8kutils.2C_gkrellm-i8k.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_for_Dell_Laptops_and_install_Gkrellm_plugin_.28i8kutils.2C_gkrellm-i8k.29)

Enabling CPU Frequency Scaling
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

Using cooling mats also help keep the laptop cooler-
[http://www.targus.com/us/accessories_cooling.asp](http://www.targus.com/us/accessories_cooling.asp)

---

### Post by joshh88 on 2008-12-29
A quick tip to help keep it clean is to use a small attachment on a vaccuum at one end of the laptop and then use the compressed air and blow toward it. It helps keep the dust managed and out of the air. Aswell as ensuring it doesn't resettle on any components or your furniture.

---

