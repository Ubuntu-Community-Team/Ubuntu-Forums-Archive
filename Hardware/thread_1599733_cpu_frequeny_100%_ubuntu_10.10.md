---
title: "cpu frequeny 100% ubuntu 10.10"
date: 2010-10-18
forum: Hardware
---

### Post by @mir on 2010-10-18
Hi

i have hp dv6000 laptop. i upgraded to 10.10 because my fan was always running. so i stated to search in to it. after some search i added a "cpu frequency scaling moniter" to my panel.

first i was showing only 55% then after some time it showd 100%, then change it to powersaver but still it changed back to performance

then checked system moniter and my both cpu are not more than 40%.

then i checked my tempreture 

```

amir@amir-HP-Pavilion-dv6700-Notebook-PC:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +65.0°C 

```and it gave me this

now i am confused that why is my system moniter showing 40% cpu usage history, my temperature 65C and still the cpu frequency 100%.

can some one help me with this, i am really stuck
or someone tell my how to reduce the cpu frequency 

thankx
@mir

---

### Post by richf on 2010-10-19
Similar problem here. Right after booting, one cpu is at 100% in system monitor. No applications running except Ubuntu system. Sometimes reboot fixes, sometimes not. 

Using HP Dv6000 laptop w/ 10.10.

Thanks in advance.

Update: I added CPU Frequency Scaling Monitor for each processor to the top panel. I set both CPUs to Ondemand.
Seems to have stopped the 100% usage. i'll see how this works, then update.

2nd Update: Spoke too soon.... CPU at 100% again....reboot, seems ok again.... maybe back to Win7?

---

### Post by dabl on 2010-10-19
In the terminal, you might be able to see your supported "policies" with this:

```
solid-powermanagement query cpufreq
```

You might see a list like this:

```
ondemand
powersave
performance
conservative
```

If so, then you can set your desired policy with this:

```
solid-powermanagement set cpufreq <policy>
```

(replace "<policy>" with the actual policy that you want)

Then you can put that command in the "Execute this command" box in your powermanager profile utility.

---

### Post by TBABill on 2010-10-19
If cpufreq is installed you can also:
```
sudo cpufreq-set --governor ondemand
```
or use another setting in place of ondemand, such as performance or powersave.
 
To see what configuration you are in at any time via terminal just type:
```
cpufreq-info
```

---

### Post by @mir on 2010-10-21
> **dabl said:**
> In the terminal, you might be able to see your supported "policies" with this:

```
solid-powermanagement query cpufreq
```

You might see a list like this:

```
ondemand
powersave
performance
conservative
```

If so, then you can set your desired policy with this:

```
solid-powermanagement set cpufreq <policy>
```

(replace "<policy>" with the actual policy that you want)

Then you can put that command in the "Execute this command" box in your powermanager profile utility.
Hi

thanks for the reply, i have tried ur option i think i worked, the the odd thing is when i have only one application open like watching a movie my cup frequency 100%,
but yesterday when i had chrome, firefox,, geany editer, firezilla, and movie player open my cpu frequency was  52% 

:D, now again it is confusing, 

why is when there is more than one app open it is at 52% and when one app is open it is at 100%,

have any idea

thankx
@mir

---

### Post by UbuNoob001 on 2010-10-21
> **@mir said:**
> Hi

thanks for the reply, i have tried ur option i think i worked, the the odd thing is when i have only one application open like watching a movie my cup frequency 100%,
but yesterday when i had chrome, firefox,, geany editer, firezilla, and movie player open my cpu frequency was  52% 

:D, now again it is confusing, 

why is when there is more than one app open it is at 52% and when one app is open it is at 100%,

have any idea

thankx
@mir

@mir, similar issue here. Open System Monitor, view CPU graph, then open Applications>Ubuntu Software Center. Do you notice anything? I get CPUs trading off 100/25 then 25/100, stops after about 15 seconds. Do you notice same thing?

---

### Post by dabl on 2010-10-21
Frequency scaling is one thing, and consumption of CPU cycles is another, so you really need to look at both.

You can use top or htop to see the use of CPU cycles by processes, in descending order of usage.  And you can use your system monitor or something like conky or gkrellm to see the frequency.

Some things, like running a VM, or even a browser, are considerably more intensive than other things, like using a text editor or terminal.  Just running the X server makes quite a difference.  You'll have to experiment with your own system and learn how different processes affect the use and frequency of the CPU.

---

### Post by odzk on 2010-10-31
I have the same problem, it was constantly running 100%. I got mine fixed though, it was sipw -d keeps on running on background eating all my resources.

I have it disabled by:

sudo gedit /etc/default/sipwitch

then change the START=1 to START=0

works fine now.

---

