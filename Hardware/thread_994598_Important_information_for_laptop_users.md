---
title: "Important information for laptop users"
date: 2008-11-26
forum: Hardware
---

### Post by ispyamoose on 2008-11-26
Hello,

If you have a laptop, I would highly suggest reading this:

I began using Ubuntu a lot just about two weeks ago. After installing, I noticed that my laptop hard drive was making a strange noise at least a few times per minute. As it turns out, that "noise" is the same as a load cycle. When I used Windows as my primary operating system, I don't recall ever hearing the noise.

So here's the problem: Hard drives are rated for a certain number of load cycles before they are considered "dead". Most hard drives are rated for 600,000 +/- load cycles before they die, but I'm sure there are many that have exceeded that number and lived. Since I was hearing that "noise" quite a few times per minute, I was getting concerned.

After doing some research, I found that laptop mode is disabled by default, which is understandable. I don't know if Ubuntu is primary for desktops or not, but that "laptop mode" setting is critical. Aggressive power settings, either by Ubuntu or through the system BIOS, can cause a massive influx of load cycles.

So here in the forums there is a fix for the load cycles, otherwise known as "the ugly fix". Well, that "fix" doesn't really work too well in my opinion. It has you creating some file, then saving it to three different places. The fix has no guarantee of fixing anything, really.

I would say, after all the internet research I've done, that 15 cycles or less per hour is probably normal.


[COLOR="Red"]All I did to stop the constant load cycles was enable laptop mode, which can be done like this:[/COLOR]

1. Open Terminal

2. Type in: sudo smartctl -a /dev/sda | grep 193
*Underneath Load_Cycle_Count is the total number of load cycles the hard drive has done. If you are getting an excessive number of cycles per hour, then continue reading.*

3. Type in: sudo gedit /etc/default/acpi-support

4. Scroll down and find: ENABLE_LAPTOP_MODE= (true=on, false=off)

5. Set ENABLE_LAPTOP_MODE=TRUE to enable laptop mode (if applicable), and save the document

6. Reboot

Note: If enabling laptop mode did not decrease the number of load cycles you have per hour to a minimal amount, then you might want to look for other solutions. You can easily revert back by following the instructions again and setting the value to FALSE. Before I enabled laptop mode, I had one hour where I had OVER 100 load cycles (bad).

[COLOR="Red"]You can also use the code:[/COLOR] 

sudo smartctl -a /dev/sda | more

That code will tell you everything about your hard drive. Scroll down to find "SMART Attributes", and underneath that will be values for Load_Cycle_Count. The closer your "WORST" value is to "THRESH", the more likely it is that your hard drive will fail soon. You can also check back with that page periodically to see how the load cycle counts are affecting the "WORST" value. 


[COLOR="Red"]UPDATE:[/COLOR] Now with laptop mode enabled, I had 6 cycles over a period of two hours.

[COLOR="Red"]ADDED INFORMATION:[/COLOR]

Originally Posted by tommcd

I would like to add that you can check if laptop mode is enabled by running in terminal:
Code:

cat /proc/sys/vm/laptop_mode

If it returns 0, laptop mode is not enabled. A result of 2 = enabled.

---

### Post by binbash on 2008-11-26
There was a big sticky about this issue in this section.But someone removed it i guess.

---

### Post by ispyamoose on 2008-11-26
> **binbash said:**
> There was a big sticky about this issue in this section.But someone removed it i guess.

I wonder why? It's a really big issue..

---

### Post by tommcd on 2008-11-27
> **ispyamoose said:**
> I wonder why? It's a really big issue..

Yes it is. Thanks for posting it.

Also, see this from the Ubuntu wiki:
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

One question, what did you install to get the  **smartctl** command? I don't seem to have that on my laptop (running Intrepid). I do have laptop-mode-tools installed.

---

### Post by Sorivenul on 2008-11-27
> **tommcd said:**
> 
One question, what did you install to get the  **smartctl** command? I don't seem to have that on my laptop (running Intrepid). I do have laptop-mode-tools installed.
I believe it is in the "smartmontools" package.

---

### Post by ispyamoose on 2008-11-27
> **Sorivenul said:**
> I believe it is in the "smartmontools" package.

That is correct.

---

### Post by tommcd on 2008-11-27
> **Sorivenul said:**
> I believe it is in the "smartmontools" package.

Yup, that was it. Thanks.

I would like to add that you can check if laptop mode is enabled by running in terminal:
```
tom@ubuntu:~$ cat /proc/sys/vm/laptop_mode 
2
tom@ubuntu:~$ 

```
If ti returns 0, laptop mode is not enabled. A result of 2 = enabled.

Regarding smartmon tools, does anyone know what load cycle count is considered excessive? Here is mine (with laptop mode enabled):
```

tom@ubuntu:~$ sudo smartctl -a /dev/sda | grep 193
193 Load_Cycle_Count        0x0012   078   078   000    Old_age   Always       -       225637
tom@ubuntu:~$ 

```

---

### Post by ispyamoose on 2008-11-27
> **tommcd said:**
> Yup, that was it. Thanks.

I would like to add that you can check if laptop mode is enabled by running in terminal:
```
tom@ubuntu:~$ cat /proc/sys/vm/laptop_mode 
2
tom@ubuntu:~$ 

```
If ti returns 0, laptop mode is not enabled. A result of 2 = enabled.

Regarding smartmon tools, does anyone know what load cycle count is considered excessive? Here is mine (with laptop mode enabled):
```

tom@ubuntu:~$ sudo smartctl -a /dev/sda | grep 193
193 Load_Cycle_Count        0x0012   078   078   000    Old_age   Always       -       225637
tom@ubuntu:~$ 

```

I would say, after all the internet research I've done, that 15 cycles or less per hour is probably normal. Your cycle count is pretty high. How long have you had your laptop? 

You can also use the code: sudo smartctl -a /dev/sda | more
That code will tell you everything about your hard drive. Scroll down to find "SMART Attributes", and underneath that will be values for Load_Cycle_Count. The closer your "WORST" value is to "THRESH", the more likely it is that your hard drive will fail soon. You can also check back with that page periodically to see how the load cycle counts are affecting the "WORST" value.

PS: I added info to the original post giving credit. Thanks for the code.

---

### Post by ispyamoose on 2008-11-27
Bump.

---

### Post by tommcd on 2008-11-27
> **ispyamoose said:**
> I would say, after all the internet research I've done, that 15 cycles or less per hour is probably normal. Your cycle count is pretty high. How long have you had your laptop? 
I was afraid of that. I've had the laptop for about 1.5 years. I don't know why the load cycle count is so high.

> **ispyamoose said:**
> 
You can also use the code: sudo smartctl -a /dev/sda | more
That code will tell you everything about your hard drive. Scroll down to find "SMART Attributes", and underneath that will be values for Load_Cycle_Count. The closer your "WORST" value is to "THRESH", the more likely it is that your hard drive will fail soon. You can also check back with that page periodically to see how the load cycle counts are affecting the "WORST" value.

When I run: "smartctl -a /dev/sda | more" here is what I get:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
.........
193 Load_Cycle_Count        0x0012   078   078   000    Old_age   Always       -       225762

```
As you can see, my THRESH value is 000. Any idea what that means? Also, under TYPE, what do all those "Pre-fail" and "Old_age" values mean?

One more thing,
In addition to editing /etc/default/acpi-support as you described, I also had to edit /etc/laptop-mode/laptop-mode.conf
and change: 
ENABLE_LAPTOP_MODE_ON_AC=0 
to:
 ENABLE_LAPTOP_MODE_ON_AC=1
in order to enable laptop mode while on AC power. This is how I enabled laptop mode in Debian also, since Debian does not seem to have /etc/default/acpi-support.
Does laptop mode work on AC power for you without editing /etc/laptop-mode/laptop-mode.conf?

---

### Post by sdennie on 2008-11-27
> **tommcd said:**
> 
I would like to add that you can check if laptop mode is enabled by running in terminal:
```
tom@ubuntu:~$ cat /proc/sys/vm/laptop_mode 
2
tom@ubuntu:~$ 

```
If ti returns 0, laptop mode is not enabled. A result of 2 = enabled.


This only indirectly checks to see if laptop-mode is enabled.  What you are looking at is a kernel tunable that tells the kernel that it should try to schedule I/O in a way that is conducive to reducing disk activity.  The laptop mode daemon sets this tunable by default but, in order to definitively know whether the laptop mode deamon is running try:

```

sudo laptop_mode

```

> **tommcd said:**
> I was afraid of that. I've had the laptop for about 1.5 years. I don't know why the load cycle count is so high.

When I run: "smartctl -a /dev/sda | more" here is what I get:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
.........
193 Load_Cycle_Count        0x0012   078   078   000    Old_age   Always       -       225762

```
As you can see, my THRESH value is 000. Any idea what that means? Also, under TYPE, what do all those "Pre-fail" and "Old_age" values mean?


THRESH is when the disk passes into TYPE.  So, at THRESH, the disk is getting old.  Your disk seems to be able to support about 1 million Load_Cycle_Count.  A VALUE of 78 means you've gone through 22% of the Load_Cycle_Counts needed to get to pass into Old_Age.  If you've had the disk for 1.5 years, that gives you like 4.5 more years of disk usage before Load_Cycle_Count could become and issue.

---

### Post by Stephen_at on 2008-11-27
I've just found this thread and turned on the laptop modes for both battery and ac so sudo laptop_mode reports:
Laptop mode enabled, active

my check on the smartctl returns:

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       13256
```

Which I think means the disk is good (well it better be, its a new laptop!)

---

### Post by tommcd on 2008-11-28
> **vor said:**
> 
THRESH is when the disk passes into TYPE.  So, at THRESH, the disk is getting old.  Your disk seems to be able to support about 1 million Load_Cycle_Count.  A VALUE of 78 means you've gone through 22% of the Load_Cycle_Counts needed to get to pass into Old_Age.  If you've had the disk for 1.5 years, that gives you like 4.5 more years of disk usage before Load_Cycle_Count could become and issue.
Interesting. How did you determine that my disk can support 1 million Load_Cycle_Count, and that I've used 22% of that, from the smartctl data that I posted?

---

### Post by sdennie on 2008-11-28
> **tommcd said:**
> Interesting. How did you determine that my disk can support 1 million Load_Cycle_Count, and that I've used 22% of that, from the smartctl data that I posted?

On all the disks I've seen, Load_Cycle_Count starts at 100 and counts down.  So, based on the 078 number reported for VALUE, I just inferred all the other numbers.

---

### Post by Lavahead on 2008-11-29
I have followed the "official" procedure in the Ubuntu Wiki link (See Post #4 Tommcd). So far, while idling the computer the Load Cycle count averages about 1.3 per minute as opposed to about 10 or more per minute before I applied the fix. I only use the computer in AC mode, so the Load Cycle was dsconcerting.

The Wiki instructions are somewhat cryptic in certain points. For one thing, you must delete/comment-out the _entire_ For-Done HDPARM blocks in the script. There are four such blocks.

Second, the "bogus" /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools is created by copying the file in /usr/lib/pm-utils/power.d/ to /etc/pm/power.d/ first. Then, insert the following code at Line 26 (in the new file):

```
if [ -f "/etc/default/acpi-support" ] ; then
 . /etc/default/acpi-support
 if [ x$ENABLE_LAPTOP_MODE = xtrue ] ; then
  echo "Laptop mode enabled, laptop-tools has nothing to do"
  exit 0
 fi
fi
```

The other modifications appear to be straight forward.

I switched to Ubuntu on my Toshiba P105-S6147 when the Windows Vista SP-1 upgrade turned my computer into a doorstop. Fortunately, I had just received the Hardy Heron CD a few days prior. It installed fine. I threw out the Windows restore CD, so I have no choice but to make Ubuntu work for me.

---

### Post by Stephen_at on 2008-11-30
There is something odd going on. I've made all the changes in the laptop_mode.conf file and the disks don't do their thing any more. As long as I stay on AC. The minute I drop onto battery the count starts rising quickly again.

---

### Post by namdung on 2008-12-24
> **vor said:**
> On all the disks I've seen, Load_Cycle_Count starts at 100 and counts down.  So, based on the 078 number reported for VALUE, I just inferred all the other numbers.

My DELL Vostro 1500 Laptop is about 8 Months old and I use it for about 10 hrs daily. The Laptop mode wasn't enabled so far. How do the following read?

Load_Cycle_Count        0x0032   008   008   000    Old_age   Always       -       185194

---

### Post by knuckx on 2008-12-24
How is the following:

193 Load_Cycle_Count        0x0032   080   080   000    Old_age   Always       -       40249
Dell Vostro 1000 Laptop ~1 year old. Laptop mode has just been enabled.

> **Stephen_at said:**
> There is something odd going on. I've made all the changes in the laptop_mode.conf file and the disks don't do their thing any more. As long as I stay on AC. The minute I drop onto battery the count starts rising quickly again.
Yep - mine do that too; It's not that bad, I mostly use the laptop on AC anyway.

Should I add this to my /etc/default/acpi-support to fix the clicking on battery power?
```

# Enable laptop mode when on battery power.
ENABLE_LAPTOP_MODE_ON_BATTERY=1

# Enable laptop mode when on AC power.
ENABLE_LAPTOP_MODE_ON_AC=1

```

Thanks.

---

### Post by elliottj85 on 2008-12-24
sudo: smartctl: command not found
 what now?

---

### Post by tommcd on 2008-12-24
> **elliottj85 said:**
> sudo: smartctl: command not found
 what now?

Install the package **smartmontools** and you will be able to use **smartctl**.

---

### Post by archyslave on 2009-01-12
this fixed my (new) laptop, the frequent clicking is gone! thanks a bunch!

---

### Post by jojo21 on 2009-01-12
I never heard a clicking problem, but I was disconcerted to find that my laptop mode was off. Thanks.

---

