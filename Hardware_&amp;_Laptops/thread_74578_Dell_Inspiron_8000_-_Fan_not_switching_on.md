---
title: "Dell Inspiron 8000 - Fan not switching on"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by gstamp on 2005-10-12
I've installed breezy on a Dell Inspiron 8000 laptop and the fan doesn't come on at all.  As a result the laptop is getting very hot.  Anyone got any tips for diagnosing the problem?

---

### Post by gstamp on 2005-10-12
Sorry... I take that back.  The fan is turning on but it doesn't stay on very long.  Can the fan settings be adjusted?

---

### Post by chanders on 2005-10-13
You need to install 'i8kutils' with synaptic.

By loading the i8k module when the system boots, you can tell the temperature of the CPU and also the fan speed. Place 'i8k' (without the quotes) on the last line of your /etc/modules file. 

When you reboot you would be able to see the fan info from the terminal by typing

```
$ i8kctl
1.0 A17 B5W123K 52 2 1 8040 6420 1 2

```
The output is in the format  **version**, **bios**,** id**, **temp**, **fan**, **speed**, **ac** and **fn**

The fan command can accept two optional parameters, one for each fan. For example,

```
[ $ i8kctl fan 2 2
```
sets the fan speed to high on each fan.

0  turn the fan off
1  set low speed
2  set high speed
-  don’t change the state of this fan

Optionally you can use the i8k Dell sidecandy in gDEsklets that shows the info graphically and you can just change them by clicking (Recommended!)

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=263](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=263)

---

### Post by PopeOptimusPrime on 2005-10-27
Hi, I have an Inspiron 1200 with the same problem.  However, apt-getting i8kutils works just fine, and I have added it to my /etc/modules, and on reboot I try to run i8kctl and am told, "can't open /proc/i8k: No such file or directory"

Any ideas?

---

### Post by normf on 2005-10-27
Hi,

I have a Inspiron 8500 with a BT Voyager 1020 PCMCIA Wireless card (which worked 'straight out of the box with Ubuntu - very impressive. Not many Distros support my card right out of the box!)

Anyway! I digress!

This is what you need to do to get your fans working. Install the i8k packages as mentioned in other posts. Also install gkRellm and the i8k plugin for gkRellm. You can use the i8kutils for the same job if you don't want install it.

For some Dell Inspirons (above 8000, I think?), you have to force the kernel to accept the module. To do this you need to do this from a shell.

[INDENT][FONT="Courier New"]$ sudo modprobe i8k force=1[/FONT][/INDENT]

If you now start gkrellm or use i8kfan, you should see the fans are working.

If this works, the next step is to make it startup evertime you boot up. Add a line with just 'i8k' on it into /etc/modules. Next you need to instruct the kernel that there is the option 'force=1' that also needs to be invoked. You do that by changing directory to /etc/modprobe.d/ Once there, create a new file in the /etc/modprobe.d directory called 18k. Add one line to the file.

[INDENT][FONT="Courier New"]options i8k force=1[/FONT][/INDENT]

Save the file. Reboot the machine and log in. Start gkrellm again and check if the fans are working.

Next thing you need to do is get i8k to work without running gkrellm each time you boot up. Just in case you forget. i8kmon can be run as a daemon so just add a script into into the right rc?.d directory to run it as a daemon.  The syntax being 

[INDENT][FONT="Courier New"]i8kmon --daemon[/FONT][/INDENT]

I haven't done this last step yet as I only just got my fans working last night. I only installed Ubuntu at the weekend and am still playing with it. Will get around to doing this step tonight. 

Also check out the page in the Official Wiki about Dell Laptops.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28i8k%29]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28i8k%29")

Happy tweaking! ;) 

Norm

---

### Post by n3rdism on 2006-11-05
Hello,
I'm currently running ubuntu 6.06 on my Inspiron 4100 and I managed to get everythign working except the fans are still giving me an issue.
I tried the gkrellm and i8k things,but still the bottom case fan isn't turning on.

It's strange because after the initial instlal the fan worked for one time and that is it.

Any ideas?

---

### Post by esaym on 2006-11-05
as far as I know all these laptops have the fans controlled by the bios.  Linux should not mess with the function at all.  Perhaps this is a ubuntu thing because I have never heard of this issue on any inspiron 8000,8100,8200.  Right now I am using an inspiron 4100 with kubuntu 6.06 with no problems.:-k :-k

---

### Post by n3rdism on 2006-11-06
well this is just weird.
however, i think i have a lead..

when i try to run the i8kmon or i8kctl i get /proc/i8k not found. and then some errors when i try to run something from i8kmon.

> can't open /proc/i8k: No such file or directory
can't open /proc/i8k: No such file or directory
    while executing
"exec /usr/bin/i8kfan 1 {}"
    ("eval" body line 1)
    invoked from within
"eval $cmd"
    (procedure "i8kfan" line 12)
    invoked from within
"i8kfan $status($fan) {}"
    (procedure "toggle_fan" line 15)
    invoked from within
"toggle_fan left"
    invoked from within
".i8kmon.lfan invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .i8kmon.lfan"
    (command bound to event)


---

### Post by David Corrales on 2006-11-06
Besides adding i8k, I installed gkrellm (with a transparent theme of course, that default robocop one sucks) and it's dell plugin. I get a visual status of my temp and fan speeds :) Plus, I can configure the temperature ranges for auto speed up and also, manually control them.

---

### Post by n3rdism on 2006-11-07
Does anyone know why i might be getting those errors?

---

### Post by n3rdism on 2006-11-23
I am running ubuntu edgy on my inspiron 4100, when i install i8kutils all goes fine.

except when i try to run i8kctl or i8kmon, i get
"can't oopen /proc/i8k: No such file or directory"

Any ideas?????????????

---

### Post by tvst on 2006-12-03
did you try running "sudo modprobe i8k force=1" as per  normf's reply? his post is quite detailed. you should look there.

---

### Post by keirnna on 2007-08-22
> **n3rdism said:**
> I am running ubuntu edgy on my inspiron 4100, when i install i8kutils all goes fine.

except when i try to run i8kctl or i8kmon, i get
"can't oopen /proc/i8k: No such file or directory"

Any ideas?????????????

When I run ```
sudo modprobe ik8
``` the computer instantly freezes input. The screen and power buttons still behave correctly, but my trackpad and keyboard are non-responsive. ctrl + alt + backspace does nothing as well as trying to switch runtime environments. When I add i8k to my /etc/modules the computer boots normally, but doesn't permit any input. Suggestions please!

---

### Post by keirnna on 2007-08-22
> **keirnna said:**
> When I run ```
sudo modprobe ik8
``` the computer instantly freezes input. The screen and power buttons still behave correctly, but my trackpad and keyboard are non-responsive. ctrl + alt + backspace does nothing as well as trying to switch runtime environments. When I add i8k to my /etc/modules the computer boots normally, but doesn't permit any input. Suggestions please!

Seems this is a known problem:
> After a default install the computer freezes anytime a power management function kicks in, including pull the power plug. After play with ACPI and APM on the 2.6.8.1 kernel I went back to 2.6.7 with APM & now everything works as expected.

I still would like to know what to do as I have 2.6.20-16.

---

### Post by shadowfx78 on 2007-08-28
> **chanders said:**
> 
```
$ i8kctl
1.0 A17 B5W123K 52 2 1 8040 6420 1 2

```
The output is in the format  **version**, **bios**,** id**, **temp**, **fan**, **speed**, **ac** and **fn**

when i do this command i get 
1.0 (null) 29XP151 -1 -1 -1 -1 -1 -1 -1

what is up with the -1's? 

Btw i have a dell inspiron 1000

---

### Post by Noccy on 2007-08-30
I have another interesting problem with i8kutils:

```
$ i8kctl
1.0 (null) 39JCF31 52 -1 0 -1 176400 -1 -1
$ cat /proc/i8k
1.0 A08 39JCF31 53 -22 0 -22 176400 -1 -22
$ i8kfan
-1 0
$ i8kfan 2 2
-1 0
```

Fans refuse to be controlled, and furthermore, every time i query the i8k status (either with i8kctl or with cat /proc/i8k) the system goes unresponsive for about a second. 

The system is a Dell Inspiron 300m, and everything else works brilliant (except for the SD/MMC card slot)

---

### Post by Noccy on 2007-12-07
Bump

Comp just went down due to overheating, and I'm afraid that it might not last long if I can't get the fan running.

I know for a fact that i8kFanGui (windows program) works and allows me to control the fans on this exact laptop, it's weird that i8kutils doesn't. :/

---

