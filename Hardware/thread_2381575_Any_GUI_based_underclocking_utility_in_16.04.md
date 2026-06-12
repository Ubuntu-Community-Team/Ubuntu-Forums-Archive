---
title: "Any GUI based underclocking utility in 16.04"
date: 2018-01-02
forum: Hardware
---

### Post by garvind25 on 2018-01-02
Hi,

  I wanted to underclock my Ubuntu 16.04 desktop to reduce fan noise and processor heating. Is anyone aware of any GUI based underclocking utility to do so. It will be useful for me to change the processor clocking again and again as per my requirement.

Thanks and Regards,
Arvind Gupta.

---

### Post by Frogs Hair on 2018-01-02
You may want to run the following command to help identify the cause and post the results here. 
```
top
```

---

### Post by garvind25 on 2018-01-02
Thanks for your response. Here's the screenshot pls.

[ATTACH=CONFIG]278003[/ATTACH]

Regards,
Arvind Gupta

---

### Post by Frogs Hair on 2018-01-02
I don't see any processes using a high % of cpu . Does this computer use a graphics card with a fan ?

---

### Post by Yellow Pasque on 2018-01-02
I'm not aware of a GUI to do this. I know of tpc as a CLI utility for some AMD CPU's: [https://github.com/turionpowercontrol/tpc](https://github.com/turionpowercontrol/tpc)

---

### Post by garvind25 on 2018-01-03
Yes... I dont use the PC for any heavy work. Still the CPU temperature shoots upto 80-90 degree celcius. It has onborad graphics with heat sink only (no add on graphics card).

Arvind Gupta

---

### Post by vasa1 on 2018-01-03
Install *inxi* and post the output of *inxi -Fxz*. That may help people understand your system.

Have you cleaned your machine lately? No clogged vents?

What program are you running when the temperature is high?

---

### Post by garvind25 on 2018-01-03
OK... here is the output of inxi -Fzx. Presently I can see the temp  increases when I use mozilla firefox. BTW I was trying to install  cpufreq yesterday. Is the icon next to 'psensors' that of 'cpufreq' utility  pls? I chose the option powersave. Now it seems that the temp is between  50-60 degree celcius (on choosing performance icon from in cpufreq, the  cpu temp rose to 90 degree celcius -- the outside temp. is about 10 degree celcius). And yes, I cleaned my CPU cabinet on this Sunday itself :D

[ATTACH=CONFIG]278028[/ATTACH]

---

### Post by Yellow Pasque on 2018-01-03
The CPU should never get up to 80 - 90C, even at full clocks under load. You are crippling the CPU performance with 'Powersave' option and ignoring the main cause of the problem, so it's not a good workaround. Something is wrong with the cooling hardware, so that's where you should be looking (unless you disabled the BIOS fan control).

> I cleaned my CPU cabinet on this Sunday itself

Is that when the problem started? If so, maybe you knocked the heatsink loose.

---

### Post by garvind25 on 2018-01-03
No... the problem existed before that ... anyways I justed opened the cabinet and checked the heat sink and fan -- they are intact. My sytem is a dual boot machine; in windows I keep max. processor state in system power options to about 70% to avoid the problem. One more thing... I got my m/b repaired twice for the same problem within a span of 3 months -- the 12v onboard supply IC was getting shorted.The problem existed well before that as well. I use Ubuntu sapringly. Hence I did not previously try to adjust the CPU clock speed (does selecting 'Powersave' option reduce the clock speed or reduce the voltage supply to the cores?)

Thanks and Regards,
Arvind Gupta

---

### Post by Yellow Pasque on 2018-01-03
> does selecting 'Powersave' option reduce the clock speed or reduce the voltage supply to the cores?

Yes, both. That's why you're seeing lower temps.

> anyways I just opened the cabinet and checked the heat sink and fan -- they are intact.

It is possible to bump the heatsink and compromise the bond between the heatsink and the CPU. You cannot discern this just by looking at it. It's also possible the heatsink was never applied correctly in the first place. Did you build this system? Is it the stock heatsink that came with the CPU?

If it was me, I would reapply the heatsink (using new thermal compound, of course).

---

### Post by garvind25 on 2018-01-04
Well&#8230; the repair engg. installed the fan with thermal grease. He replaced the original heatsink + fan as the fan was rotating slowly. He used i3 processor family heatsink + fan as a replacement. I could see that the new heatsink had the same diameter of contact  and same overall diameter but was half the height of the original heatsink. The problem of processor heating existed while I was using the original heat sink also. I had only used a brush to clean the internals and was very gentle in doing so. So I suppose I would not have rocked the heatsink assembly.  Do you suppose the problem is related to software / OS? I have presently Win 7 + Ubuntu 16.04 (both 64 bit). Previously, I was using WinXP SP3 &#8211; 32 bit. While using WinXP, there was no heating problem. Also, one more temporary change made is my system is that it is running on 2GB RAM. Previously my system had 2 X 2GB RAM. On sunday, one of the RAM went bad and had to remove the DIMM from the m/b. 

Thanks and Regards,
Arvind Gupta

---

### Post by Yellow Pasque on 2018-01-04
> Do you suppose the problem is related to software?

No, I don't, especially if you have to limit the speed in Windows too. The BIOS controls the fan, unless you disable that option in the BIOS settings. In that case, the fan runs at full speed unless you use a program to slow it down.
Another way to test if the problem is software related is to monitor the temperatures in the BIOS

I am sorry if this sounds simple, but you did verify the fan is running, correct? The output from inxi reports fan speed as 0 RPM. Can you copy/paste the output of:
```
sensors
```

---

### Post by garvind25 on 2018-01-04
Sure... here is the output of sensors command. I also checked the heating of BIOS physically. It is indeed getting very warm! 

[ATTACH=CONFIG]278043[/ATTACH]

I have run into another problem. It seems I have forgotten my BIOS password! Is there any way to disable the BIOS password through Ubuntu? I tried by shorting the terminals of the CMOS battery holder while the system was switched off. It didnt help. Only the BIOS time & date got reset (I can enter BIOS settings by simply pressing enter when the BIOS password option comes up but almost all options are greyed out -- ie uneditable!)

Thanks and Regards,
Arvind Gupta

---

### Post by vasa1 on 2018-01-04
Please copy/paste output from the terminal here between code tags rather than post images. Doing so allows others to quote part of the terminal output.

---

### Post by QIII on 2018-01-04
Your problem is hardware related.  Trying to slow your fans using software fan control is never a good idea.  The fans run as fast as they need to to cool your machine.  Slowing them is likely to cause serious damage.

If I were to guess, I'd bet a week's pay that:

1.  Your fan is loud and "running fast" because it is actually failing and running slower than it should.

2.  The heat sink is clogged

Or

3.  You need to refresh the thermal compound between the base of your heat sink and the CPU.

---

### Post by Yellow Pasque on 2018-01-04
EDIT: Sorry, double post.

---

### Post by Yellow Pasque on 2018-01-04
To clear password, you need to boot with jumper on pins 2 and 3:
[https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/desktop-boards/G41/DG41TY/DG41TY_ProductGuide01.pdf#%5B%7B%22num%22%3A765%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C72%2C707%2Cnull%5D](https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/desktop-boards/G41/DG41TY/DG41TY_ProductGuide01.pdf#%5B%7B%22num%22%3A765%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C72%2C707%2Cnull%5D)

Please confirm that you see/hear the fan running while the system is powered on. sensors reports fan(s) as 0 RPM, but it's not always reliable.

---

### Post by garvind25 on 2018-01-04
Yes... I just opened the side panel of the cabinet and checked the CPU fan. It is running (and thanks... I was able to reset my BIOS password :)).

Regards,
Arvind Gupta

---

### Post by garvind25 on 2018-01-04
> **QIII said:**
> Your problem is hardware related.  Trying to slow your fans using software fan control is never a good idea.  The fans run as fast as they need to to cool your machine.  Slowing them is likely to cause serious damage.

If I were to guess, I'd bet a week's pay that:

1.  Your fan is loud and "running fast" because it is actually failing and running slower than it should.

2.  The heat sink is clogged

Or

3.  You need to refresh the thermal compound between the base of your heat sink and the CPU.

Thanks for your response. It is a new fan installed by the repair engineer 10-15 days back using thermal paste. So all these options are ruled out. And I had cleaned the cabinet this saturday itself using a brush.

Regards,
Arvind Gupta

---

### Post by QIII on 2018-01-04
How well is the case ventilated?

Your CPU is simply overheating.

---

### Post by garvind25 on 2018-01-04
> **vasa1 said:**
> Please copy/paste output from the terminal here between code tags rather than post images. Doing so allows others to quote part of the terminal output.

Thanks for your response. I dont know how to dump output of a command in a text file. So I paste images.

Regards,
Arvind Gupta

---

### Post by garvind25 on 2018-01-04
It is an ATX cabinet (the m/b most probably has uATX form factor -- Intel DG41TY). Has two 80 mm cabinet fans -- one on side and one on back run directly by SMPS output. 

Is there a way to test if the CPU is healthy?

Regards,

Arvind Gupta

---

### Post by QIII on 2018-01-04
Does the CPU run cooler with the side panel removed?

(Don't run it too long that way.  There are mobo components that depend on case airflow.)

Is the CPU fan making all the racket, or is it the anemic 80mm case fans?

---

### Post by Yellow Pasque on 2018-01-04
> **QIII said:**
> Does the CPU run cooler with the side panel removed? Is the CPU fan making all the racket, or is it the anemic 80mm case fans?

80mm fans aren't necessarily anemic. They can move air like 120mm fans. They just make a racket when doing it. (Have you ever dealt with 1U servers and 40mm fans?)

The non-CPU temps look okay to me. The idle Voltage (1.14V) seems okay. I still suspect the CPU cooler. I find it odd that your tech used an i3 heatsink, as there were no i3's for Socket T/775. Googling around, I see mixed reports about whether Socket 775 and 115x heatsinks are interchangeable. 
Also, the Q6600 came with a beefier stock heatsink than other Socket 775 CPU's with lower TDP.  Using a different Intel heatsink seems like a downgrade.  
[https://www.anandtech.com/show/10500/stock-cooler-roundup-intel-amd-vs-evo-212/3](https://www.anandtech.com/show/10500/stock-cooler-roundup-intel-amd-vs-evo-212/3)

---

### Post by garvind25 on 2018-01-06
The CPU runs with the side panel closed. The noise is sometimes coming  from processor fan (when the processor is on performance mode -- using CPU freq utility)

Regards,
Arvind Gupta

---

