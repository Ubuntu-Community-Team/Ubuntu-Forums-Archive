---
title: "fan control without the pwmX file"
date: 2023-04-28
forum: Hardware
---

### Post by jkobori19 on 2023-04-28
Hi,

I recently bought an ASUS TUF F15 laptop,
but the CPU and GPU fans are extremely annoying:
suddenly spinning up then down (0 RPM -> 2700 RPM -> 0 RPM),
or just simply spinning up to 2700 RPM, then immediately falling back to 2200 RPM,
and finally stopping after a couple of seconds.
It drives me crazy, so I started to look for a solution.

I tried to use several fan controlling scripts
(fan2go, asus-fan-control, etc),
and went through numerous forums,
but I still have the following problem.

All of these scripts try to control the fans via editing
the /sys/class/hwmon/.../hwmonX/pwm1 (or generally pwmX) files
by setting the value in it,
which indirectly corresponds to a particular fan RPM.

However, my hwmonX directory does not contain any pwmX files,
instead, these ones are there:

[INDENT]pwmX_auto_pointY_pwm[/INDENT]

and

[INDENT]pwmX_auto_pointY_temp[/INDENT]

where X can be 1 (cpu) or 2 (gpu),
and Y runs from 1 to 8.
I guess that a particular *_temp
is the temperature at which the
fan starts to operate at the corresponding *_pwm value.
This way the OS have a fan curve,
which is actually the "name" of it: asus_custom_fan_curve

I found the commit in which this new feature was delivered into the asus-nb-wmi.c file: [https://patchwork.kernel.org/project...ke@ljones.dev/]("https://patchwork.kernel.org/project/platform-driver-x86/patch/20211002062157.33318-2-luke@ljones.dev/")

When enabling these custom curves via setting the pwmX_enable values to 1,
the spinning up and down of the fans are *much* smoother,
it hardly can be noticed. The problem is,
that since it is not entirely safe to use this method without knowing exactly how the fans
react to lower pwm values,
I want to gather all the necessary information before I start to use this stuff.
Since the pwmconfig uses the pwmX files for its tests,
I don't know at which pwm values do the fans start to spin/are still spinning.

However, the comment for the source code modification does not contain
some necessary information for me in order to make me able to write a script for fan controlling.
Thus, my question is that is there anybody here who has the same asus_custom_fan_curve available for them
and already used it/using it?

The information regarding this asus_custom_fan_curve I need are the following:

- which sensor is used to control the CPU fan? I guess it is the coretemp,
    and I observed that the BIOS (the default throttle thermal policy) is probably using that too
    
- what determines how fast a fan spins up?
- is there any option for hysteresis?

I mean I would like to create a script,
where all of these parameters can be fine tuned.
Another option would be to modify an already existing one
to make it able to handle the pwmX_auto_pointY_pwm/temp files instead of using the pwmX ones.

The output of the "fan2go detect" is

> coretemp-isa-0000
  Sensors  Index               Label                  Value
           1      Package id 0 (temp1_input)     45000
           2      Core 0           (temp2_input)     38000
           3      Core 4           (temp3_input)     41000
           4      Core 8           (temp4_input)     39000
           5      Core 12         (temp5_input)     41000
           6      Core 16         (temp6_input)     40000
           7      Core 20         (temp7_input)     39000
           8      Core 24         (temp8_input)     40000
           9      Core 25         (temp9_input)     40000
           10     Core 26        (temp10_input)   40000
           11     Core 27        (temp11_input)   39000
           12     Core 28        (temp12_input)   41000
           13     Core 29        (temp13_input)   41000
           14     Core 30        (temp14_input)   41000
           15     Core 31        (temp15_input)   41000

> iwlwifi_1-virtual-0
  Sensors  Index                   Label               Value
           1      hwmon7/temp1 (temp1_input)  N/A  

> asus-isa-0000
  Fans     Index  Channel  Label    RPM  PWM  Auto
           1      1     cpu_fan  0           N/A    true

> nvme-pci-0e100
  Sensors  Index  Label                         Value
           1      Composite (temp1_input)  37850
           2      Sensor 1 (temp2_input)     37850

> acpitz-acpi-0
  Sensors  Index                   Label                Value
           1      hwmon1/temp1 (temp1_input)   27800

Also, it seems that the temp sensor for the GPU is not detected.
I searched for kernel modules which can be used for probing the sensors on the motherboard/GPU,
but most of them is outdated, and only the already included ones are safe to use: asus_wmi and asus_nb_wmi
Of course, if I don't have the GPU sensor output,
I won't be able to control the GPU fan.

Some info about the OS: 5.19.0-41-generic #42~22.04.1-Ubuntu SMP  PREEMPT_DYNAMIC Tue Apr 18 17:40:00 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
The laptop is the TUF F15 FX507ZV4

Any help/tips/suggetions are appreciated!

 Józsi

---

### Post by Yellow Pasque on 2023-04-28
[https://gitlab.com/asus-linux/asusctl](https://gitlab.com/asus-linux/asusctl)

Let us know if you need help.

---

