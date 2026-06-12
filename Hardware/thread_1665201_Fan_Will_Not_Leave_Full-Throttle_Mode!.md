---
title: "Fan Will Not Leave Full-Throttle Mode!"
date: 2011-01-12
forum: Hardware
---

### Post by Pard68 on 2011-01-12
I'm running Ubuntu 11.04 on a Toshiba Satellite L505. 

On start-up my fan runs perfectly fine. It will increase in speed and then idle back, but after a little while the fan goes into full-throttle and it will not stop unless I do a restart. 

I am not sure if it was having this problem with my LiveCD 10.04 I use and I know it doesn't do this on Windows 7. 

I tried the "pwmconfig" option, but I do not have the controls for that. I looked around and it seems a fix has been discovered by editing your GRUB start-up file, but of course I am using GRUB 2, so the whole thing is different. I went and looked in my "/ect/Defualt/grub" file, but there is no where to place add the "acpi-osi=Linux" on this new GRUB 2 deal. 

Is there a new work around for the constant fan? I wouldn't even care that much, except I do not want to be replacing my fan every year!

---

### Post by Fafler on 2011-01-12
Try out fnfxd and fancontrol.

Also make sure the vents arent clogged up with dust and stuff.

---

### Post by Pard68 on 2011-01-12
Having a problem getting fnfxd to work. I appears my kernel(s) (2.6.35 and also 2.6.32) are missing some required stuff. Namely my kernel doesn't have the Toshiba option enabled in my ACPI. When I go to /proc/acpi/ I find that there is no Toshiba file (as all the tutorials I am finding say that there is). Found one that will help me compile a new kernel, butmy concern is that the last Toshiba ACPI thing they have is for 2.6.29 and I am not sure if that will be OK, I imagine it will be, but I'd hate to find out that it doesn't work. 

Anyone know a work around? I've been using 2.6.35 and I read somewhere that 2.6.32 is a bit more stable for Toshiba. When I got onto Windows 7 I am going to flash the BIOs with the latest update and maybe that will help, some people said it helped them out. 

I think I have a workaround for the time being, found a program, I think it's Toshset (but I cannot recall), and it allows me to control my fan, but only on/off.

---

### Post by Fafler on 2011-01-12
modprobe toshiba_acpi ?

---

### Post by Pard68 on 2011-01-12
Ya, tried modprobe before (and again for old time's sake) and I get a "modprobe: command not found". I have to go compile a new kernel, I think I will do a quick back-up and downgrade to Lucid (I don't want to compile a new kernel with .35, to unstable for my taste). Then I can make a new kernel real quick with Toshiba_ACPI enabled.

---

### Post by Pard68 on 2011-01-12
Just an update, I reinstalled Unbuntu 10.04 and installed it over everything else (just running Ubuntu 10.04 right now). I added "noapci" to the grub loader (didn't do that before). Everything seems to be working alright now. I've been building and compiling a kernel for the last few hours and the fan has not gone into full-throttle as of yet (which I think is a record length of time!). I'll keep the kernel around, but maybe I will not even need to use it.

---

### Post by Pard68 on 2011-01-13
OK, fan is back to full-throttle. Not sure if this is because of a fan issue or a CPU issue, however. The air coming out is pretty hot. Wondering if that is because the kernel runs on performance for the CPU by default. Is there a way to switch the CPU to OnDemand without compiling a new kernel.

---

### Post by 3602 on 2011-01-13
Supposedly CPU Scaling Monitor can change that.

---

