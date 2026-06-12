---
title: "Fan not working on ASUS laptop"
date: 2017-09-14
forum: Hardware
---

### Post by alvib on 2017-09-14
Hello,
I have an ASUS X540SAA laptop with an Intel N3060 (Celeron family) CPU. I am running Kubuntu 17.04.
Since the laptop is suspiciously silent and tends to overheat, I installed the lm-sensors and pwmconfig packages to check the state of the fan.
sensors gave me this output:
```

asus-isa-0000
Adapter: ISA adapter
cpu_fan:     -1 RPM
temp1:       +6280.0°C  

```

and on running pwmconfig:
```

   Found the following devices:
   hwmon0 is acpitz
   hwmon1 is coretemp
   hwmon2 is soc_dts0
   hwmon3 is soc_dts1
   hwmon4 is asus

Found the following PWM controls:
   hwmon4/pwm1           current value: -1
hwmon4/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) 
There are no usable PWM outputs.

```

So i tried the manual setup, and got this:
```

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon4/fan1_input     current speed: 0 ... skipping!

There are no working fan sensors, all readings are 0.
Make sure you have a 3-wire fan connected.
You may also need to increase the fan divisors.
See doc/fan-divisors for more information.

```

I couldn't directly check whether I simply had a faulty fan, since this laptop came with no Windows copy pre-installed and Kubuntu is the only OS that has been running on it.
I decided to look for solutions on the internet and found that many ASUS users had the same problems, and one possible solution was to update the BIOS.
So I found a newer version of the BIOS on the ASUS website, and I installed it. As soon as the laptop rebooted after the installation, the fan clearly started whirring and I could feel air blowing from the laptop.
I thought I had solved the problem, so I ran sensors to check whether everything was alright with the new BIOS.
The output was:
```

asus-isa-0000
Adapter: ISA adapter
cpu_fan:     3400 RPM
temp1:       +6280.0°C  

```

Thus, the fan was actually working properly. The problem is that after I ran sensors it stopped immediately, and running pwmconfig gave me the same output as earlier.
On rebooting the PC, the fan kept on staying still.
I decided to stop worrying about the issue (it only bothers me when I'm playing HD videos or playing games, as the CPU limits the clock due to high temperature, otherwise the PC runs fine).
Today I turned on the laptop, and the fan started spinning again, but again it stopped as soon as I ran a fan-related program.
Even if I could go on using my PC like this, it really bothers knowing that the fan probably works fine but Kubuntu just can't deal with it properly, so I'm asking for help.
Is there any possible solution to this? Assuming my fan works properly (which I do, since I'd prefer not to replace it), is it possible that this is a bug, and would it be of any help reporting it?
I already tried uninstalling, reinstalling and reactivating the proprietary intel-microcode driver package.

Any help would be greatly appreciated.

---

### Post by DAB4970 on 2017-09-15
Just my thoughts:
Is the laptop new or used?  How old is it?  So it's the CPU fan, and you say it seems to run fine until you ran the fan-related program.  There could be a glitch in the programming of that application.  or Is the BIOS updated?

---

