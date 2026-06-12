---
title: "HDD Overheating on 10.04"
date: 2010-10-31
forum: Hardware
---

### Post by daredevil_g on 2010-10-31
Hi everyone, i'm having a little problem whit Ubuntu 10.04, which is installed on a HDD in a external USB case (140 GB). My laptops is a HP Pavilion dv7-4069wm (RAM 4 GB DDR3, HDD (2) 320 GB, 2.1GHz VISION Technology from AMD - Ultimate with AMD Phenom II Triple-Core Mobile Processor N830,  ATI Mobility Radeon HD 5470s itchtable graphics).
When i work in Ubuntu, from my external HDD my laptop gets too hot, when i swich to win 7 the HDD Life Pro pop up an emergency label, the internal HDD is 55 °C, i have read the specifications of my internal HDD (WD3200BEKT) and it can handle until 60 °C. But, why is getting so hot when i'm using Ubuntu on a external disk ???? Is that normal ? Thanks for your help.

---

### Post by P4man on 2010-10-31
Windows or ubuntu will change nothing here I think. Its just if the drive is powered, and your laptop seems to have really poor thermals, well, its going to get hot. I fear there is very little you can do; you could try not mounting the internal drive in ubuntu and/or enable the drive to spin down in power management settings. But thats a bit of a crutch because it will get just as hot again if you run windows from the internal drive.

Either hope the drive will take it, or consider a laptop cooler.

---

### Post by Jimtheplanner on 2010-10-31
Hi Folks,

Hi Folks,

Have a look at [http://ubuntuforums.org/showthread.php?t=1600307](http://ubuntuforums.org/showthread.php?t=1600307)

I did a back to back clean install between 10.10 and Mandriva 2010.1 just to prove my hardware. I found that Mandriva was a cool 40 deg C where 10.10 was cooking my hardware at good 10+ Degs C higher.

I would love to here of any other distro comparison.But with 10.10 I need asbestos gloves. 

Jim

---

### Post by daredevil_g on 2010-10-31
I miss the little detail that, in win 7 the temperature goes normal after a while. I have no problemo whit the temperature in win 7, only when i'm done working whit ubuntu and switch to 7, win 7 starts whit 53 - 55 °C and later it normalizes to 35 - 45 °C. And yes i have a cooler. :)

---

### Post by P4man on 2010-10-31
Does CPU scaling work? Right click the panel, add to panel, cpu frequency scaling applet. If that gives no error, make sure its set to ondemand.

Also, if you have an ATI videocard, the default drivers dont provide powermanagement and that causes the GPU to run hot. In a cramped space like a laptop that will inevitably heat up other components.

---

### Post by gordintoronto on 2010-10-31
You might find that 10.10 solves this problem. Try running it from a USB stick to see how the temperature goes. 10.04 can't read the CPU temperature on your CPU (or any other AMD "10h" processor), but the later kernel in 10.10 reads it just fine.

---

### Post by efflandt on 2010-10-31
I doubt if the internal hard drive "is" the problem, it is likely an "effect" of the actual problem (cpu or gpu not throttling back, fans not speeding up).  Unless it is a green hard drive, its speed does not change.

However, you can spin the internal drive down when not being used.  When booted from USB go to System > Preferences > Power Management, and check the box to "Spin down hard drives when possible".  It will not spin down immediately, but should after a period of not accessing that drive.  That will not necessarily resolve whatever heating or cooling issue, but may help.  Your USB drive that you are running from will likely remain running due to logging.  If you access your internal drive it will spin up again until it is idle for awhile.

---

### Post by daredevil_g on 2010-11-01
Wow, thanks a lot to all of you. A lot of possible problem solvers jejejeje, i'll try one by one and i'll let you know how is it going. :):)

---

### Post by daredevil_g on 2010-11-01
I added to the panel the CPU Frequency and Temperature Monitor, the CPU Frequency it's about 800 MHz at the moment i'm writing this and the temperatures are WD3200BEKT /dev/sg0 = 50 °C* (after 10 min working in ubuntu) || WD3200BEKT /dev/sg2 = 45 °C || WD3200BEKT /dev/sda0 = 50 °C || WD3200BEKT /dev/sdb = 46 °C.
I have CPU 0 - Ondemand, and the spin drive down when possible On.
I guess the only possible option will work is upgrading to 10.10.
I'll do it and tell how is it working

==============================================================================================================================================================================================
Edito:
I just finished installing Ubuntu 10.10 and nothing changes, the themperature just keep rising and rising. Any other idea ????

---

### Post by tadaskr on 2010-11-02
is your laptop fan running? maybe it could be cooling problems. now my HDD is 47C when fan running normaly I mean when need go faster when need go slower

---

### Post by daredevil_g on 2010-11-02
Mmmmm yes it works, but not go fast when this thing is heating up. In win works fine, the fan speed up when i use software like dvd shrink or flash cs4. Why in ubuntu isn't working in that way ? Why is working that HDD when i'm not using it ? Thanks for your answers.

---

### Post by Schuby007 on 2010-11-20
Is there any way to check if the "Spin down hard disks whenever possible" function in gnome-power-manager is actually working? I'm using Ubuntu 10.10.

Thanks

---

