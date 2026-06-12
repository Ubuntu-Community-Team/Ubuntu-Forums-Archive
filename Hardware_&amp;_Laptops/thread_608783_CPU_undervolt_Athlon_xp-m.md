---
title: "CPU undervolt Athlon xp-m"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by naja on 2007-11-10
Hallo
I am using Ubuntu gusty on HP Pavilion ze4400 with Athlon XP-M 2400+ und i can undervolt it to 0.925V at ca. 800MHZ and than fan stops running.under Ubuntu i can select the Clock -Cpufreqlet-.but my question ist.is it possible to undervolt Athlon XP-M?
I know this site but its for K8:
[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/)
the other tool called linux PHC but its only for  Pentium M and up.
I am thanksfull for every help

---

### Post by naja on 2007-11-24
Hi All
I did do some research and i ve done it !!!!!!!! Thanks to the Author! my Laptop now is silienced!!!!!!!
i found i small program called K7mctrl, with it you can control VID and FID but first be sure that powernowd or governor disabled or set at userspace.
First,download K7mctr:
[http://www.gem.mydns.jp/dti/k7mctrl/k7mctrl-0.4a.tar.gz](http://www.gem.mydns.jp/dti/k7mctrl/k7mctrl-0.4a.tar.gz)
Second:you will need some Compiling stuff-not very much though-.be sure to install g++,c++ ,Tk and tcl -i did that with dev packages too and the Kernelmodule msr to be loaded.
then just run make in the extracted folder:
make
after compiling is done-which doesnt take much time-,you will find 2 executable files, the first one is in cmd folder and its called k7mctrl,the second on is tkK7mauto in the tk folder and it is the GUI-Yeppi!-.you can put those in /usr/bin/  or link them to be able to excute them globaly-is this the write word?-
this is how to use :
sudo k7mctrl -fid x.x    where x.x is the wanted multiplier e.g. 4.0
sudo k7mctrl -vid x.xxx where x.xxx is the wanted Voltage e.g. 0.925
to check your setting just run the k7mctrl command.
I have 2 VID reading now -dont know why,i dont have SMP,but I am going to look after that too.
now my Problem is that I cant run the GUI tkK7mauto, it look for configured sensors - i2c thingy -,the problem is,that sensors-detect doesnt find any usefull sensors and doesnt write any sensorconfigs!!!,though i can read my cputemp using computertemperaturemonitor (ACPI),
Is there anyway to make dummy sensors configs,so i can atleast run tkK7mauto?
tkK7mauto gives me the following error:
light@light-laptop:~$ sudo tkK7mauto
/sys/devices/platform/i2c-9191/9191-0290/in0_input: No such file or directory
Any solution for that? 
any help will be appreciated

---

### Post by naja on 2007-11-24
Hi 
There is a chance to ignore sensors or something like that by editing the senosor.c and sensor.h but i really didnt understand the gtranslated japanes website:
[http://www.gem.mydns.jp/dti/k7mctrl/](http://www.gem.mydns.jp/dti/k7mctrl/)
thanks

---

### Post by daitei on 2007-11-26
Thanks for your question. 
 
Please define NO_SENSOR like below in tk/sensors.h to ignore sensors. 
 
#define NO_SENSOR 
 
And, compile again. 
 
(REMARK) 
Now,tkK7mauto is not detect FSB automatically. 
There is ,script ,"init.d/chkfsb.sh". 
This script detects FSB and writes into /usr/local/var/cpustate/state like below. 
 
CLOCK  800.148 
MULTIPLER 6.0 
FSB 133.358 
 
If /usr/local/var/cpustate/state is there, tkK7mauto reads FSB from it. 
 
yours sincerely.

---

### Post by naja on 2007-11-26
Hallo
thank you very much!
hmmm with NO_SENSOR it shows me only 1 slider for MHZ and a systemmonitor with auto/manual button.its not very usefull this way because the system hangs when moving the slider.k7mctrl works just fine,but i would like to have a tool,that makes it possible to select profiles (Powersave,Performance,Ondemand,Lowpower etc.).I think a small scriptfile would be enough for Powersave and Performance but how to make a script that allows Ondemand(on the fly FID and VID at different cpuloads)? or make governor use k7mctrl,could it be possible?
I think it should be a daemon or something like that.unfortunatlly i dont have any programing skills.
another question,from where does k7mctrl read FID and VID? cant tkK7mauto  just do the same thing?
k7mctrl ROCKS !!!
thank you alot

---

### Post by daitei on 2007-11-27
Hallo 
 
Please limit max-clock using command-option like below(example limited 
 1.6GHz), if your system hangs. 
 
$ tkK7mauto -max 1600 
 
k7mctrl and tkK7mauto reads FID and VID from MSR device. 
Please refer to lib/devmsr.c and lib/devmsr.h. 
 
tkK7mauto can change FID by auto(ondemand) or manual. 
Please refer to [http://fab51.com/cpu/tips/linux_k7-mcf.html](http://fab51.com/cpu/tips/linux_k7-mcf.html) 
(fab51.com's english document). 
 
-- my way of using tkK7mauto (with X-Window): 
1) Install tkK7mauto with suid(chmod 4755) for normal users use. 
2) Execute tkK7mauto from X Display Manager(wdm,gdm or etc.). 
 
-- smarter method: 
I think it is smarter method to use "powernow k7 module" with 
"Manual-Frequency-Table-patch" (but, I have not used it yet). 
Please refer to the following sites. 
 [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html) 
 [http://www.yggdrasl.demon.co.uk/code/](http://www.yggdrasl.demon.co.uk/code/) 
 [http://linux.mini13i.gotdns.org/kernel%2Fdesktop%A4%C7powernow-k7.html](http://linux.mini13i.gotdns.org/kernel%2Fdesktop%A4%C7powernow-k7.html) 
 
have a fun.

---

### Post by naja on 2007-11-27
Hallo 
thanks alot for the infos, ill try to patch powernow k7 later,which is the last solution  i wanted to try.so i can choose custom Voltage WHILE autoscaling.the frequencyscale is good,but with undervolting its alot better.
i thank you again

---

### Post by naja on 2007-11-27
Hallo
hmmm tkK7mauto hangs system when the speeds goes down,i think there is something wrong about downsclaing.i took a look at lib/devmsr but i really didnt understand much:confused:,sorry
here is a screenshot from tkkK7mauto.
as you can see, there is no Vcore.is there a way to just ignore the sensors and only have Vid control?shouldnt it get vid from MSR only?
I really know that I am annoying sometimes
Thank your for your patience

---

### Post by daitei on 2007-11-28
Hallo 
 
> tkK7mauto hangs system when the speeds goes down. 
hmmm... :confused:
It might be a cause by low Vcore possibly.  
Please try a higher Vcore(example:default Vcore). 
 
Sorry, tkK7mauto only reads the VID,and does not control VID, 
because I cannot confirm an actual result on my system. 
My system is "Athlon XP-M 2500+" on M/B for Desktop. 
This M/B is not supported VID change. 
 
best regards

---

### Post by naja on 2007-12-12
Hi
I ve found this page : 
[http://www.vdr-portal.de/board/thread.php?threadid=47006&sid=46b1e8a2a81f557a5fbcd9b4e5ab7805](http://www.vdr-portal.de/board/thread.php?threadid=47006&sid=46b1e8a2a81f557a5fbcd9b4e5ab7805)
it is german but its really easy to follow and the patches there are newer.
I did patched the kernel  with Manual-Frequency-Table-patch and i am now using governor with custom voltage table,i have only 1 problem, i cant change voltages on the fly,but i am running at the lowest voltage available.
I have now in /etc/modules
powernow_k7 overwrite_table=1 multiplier=40,50,60,70,80  voltage=925,925,925,925,925
thats good enough for now,because i can change to the highest speed with k7ctrl after selecting userspace mode in governor.i may investigate it later,but for now i had enough compiling ;)
I thanks you alot for everthing

---

