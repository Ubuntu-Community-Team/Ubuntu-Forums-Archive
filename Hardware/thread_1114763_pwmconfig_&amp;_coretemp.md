---
title: "pwmconfig &amp; coretemp"
date: 2009-04-03
forum: Hardware
---

### Post by gabrielalcivar on 2009-04-03
Ok, I have been looking online for a solution for 2 days now. If there's a post that is related to my issue, it did not solve my problem.

I have a HP dv6875 with Ubuntu 8.10 installed (fully updated). I turn it on and the fans go full speed and they never slow down. I have to work in quiet environments and this issue is making me resort to using VISTA :-&

I have followed many tutorials to set up pwmconfig with no success. I've installed lm-sensors and that part went with no problems, then when I run "sudo pwmconfig" I get the following output:
**/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed**

My "sensors" output is the following:
[B]coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +85.0°C, crit = +85.0°C) 
[/B]
My computer IS capable of controlling the fans in VISTA, therefore I presume it is an issue in Ubuntu.

Please help me fixing this problem, it is driving me insane.

Thank you in advance

---

### Post by gabrielalcivar on 2009-04-05
Anyone!? I've been spending countless hours online, but no success yes. Tried nvclock...and apparently my video card doesn't support fan control. (I read somewhere that it might be that)

Please if you guys know a solution, i need you help!

---

### Post by bednar007 on 2009-12-19
I have the same problem with desktop machine (Asus P5K Premium, with P35 and ICH9 bridges and Core 2 Duo).

I used OpenSuse 11.0 and 11.1 on this machine and pwmconfig worked perfectly. After installing Kubuntu 9.10 the problem started.

---

### Post by zzhao on 2010-05-27
Same problem here. pwmconfig returned only "no pwm-capable sensor modules installed". Also searched on the internet and found 'pm-powersafe' and 'upower' to try.  No meaningful responses.

I am using ASUS P7P55D mainboard. Under Windows ASUS has a build in program called EPU Engine to control the CPU fan speed and SmartDoctor for the GPU fan (ASUS EAHD5670). I guess there should be a way in Ubuntu as well. However, searching on the internet only returned stories of people who succeeded using pwmconfig and fancontrol. It would be nice if someone has an idea on what options are there if pwmconfig doesn't work.

---

### Post by AcidMoon on 2010-05-27
I found some info on lm-sensors here [http://ubuntuforums.org/archive/index.php/t-607614.html](http://ubuntuforums.org/archive/index.php/t-607614.html) Check out the post by Temüjin.
Old info I know but it might help!

---

