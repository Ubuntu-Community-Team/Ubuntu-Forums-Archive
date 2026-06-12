---
title: "USB mouse spontaneous freeze"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by Abasher on 2005-04-19
Hi!

I have a problem with connecting a USB mouse to my laptop computer (don't know if it's a problem exclusive to laptops, therfore I posted it in the main HW forum). Pluging it in causes no problems, and it cooperates with my touchpad without problems.

However, after some random time (5min-1h usually) it freezes. The touchpad keeps working, and the lights on the mouse keep shining.

To get it working again I have to plug it out that back again.

Looking in /var/log/kern.log no errors are found, only entries aboud mouse disconnected (when I pull it out), then new mouse found.

It always seems that the HD works when the mouse freezes. Don't know if it happens because of the problem, or if it is the reason why it's happening.

This problem was in Warty too. Never found a way to fix it. Kinda had hoped that such a bug would be fixed in the new version, but seems like that is not the case.

I've never had these kinds of problems with any Other OS (except Warty). Not in WinXP, Fedora1,2&3 nor Debian "Testing".

The mouses I've tried are Logitech Wheelmouse Optical and Microsoft Intellimouse Explorer 1.0 Optical.

My computer is a Fujitsu-Siemens Lifebook C1020. The South bridge is a VIA VT8233, containing a UHCI USB 1.1 controller. The driver loaded for it is uhci_hcd.
My kernel version is: 2.6.10-5-686.

---

### Post by erkki70 on 2005-04-19
Hi,
Have you tried to reconfigure X?
 ```
sudo dpkg-reconfigure xserver-xorg
``` 
enter your password and for your mouse select /input/dev/mice
On my Fujitsu-Siemens E2010 this solved the prob for a logitech mouse. 
The touchpad is then on psaux and both are working fine.

Hope this helps and good luck. ;-)

Cheers,
Erkki

---

### Post by Dam on 2005-04-19
I have _exactly_ the same problem as you... 

and my computer is a Fujitsu-Siemens C1020 too! :-? 

I have been desperately looking for a solution for the last two months but I still didn't find the one!

---

### Post by heimo on 2005-04-19
Seems like laptop model specific problem:
[http://ubuntuforums.org/showthread.php?t=8001]("http://ubuntuforums.org/showthread.php?t=8001")
 
Found something on BIOS update release paper (S2 - suspend?) maybe related?
[http://download.fujitsu-siemens.com/WDB/download.asp?dir=Public\KE0030600&Attachment=SBM2002_039_GB.doc&Info=GenesisDoc]("http://download.fujitsu-siemens.com/WDB/download.asp?dir=Public\KE0030600&Attachment=SBM2002_039_GB.doc&Info=GenesisDoc")
 
I guess disabling power management is not an option...

---

### Post by Dam on 2005-04-19
I tried to reconfigure xorg as suggested by erkki70... but the problem remained!

Here are a few observations:

1) If I have two USB mouses plugged when the one I am using freezes, I only have to move the second one to make the first one work again.

2) The USB mouse works again when I reboot xorg (CTRL+ALT+BACKSPACE) or when I unplug it and plug it again.

---

### Post by erkki70 on 2005-04-19
Hi,
That's funny freeze behaviour...
Could you post your xorg.conf file as it might help to see if it requires extra settings or tweaking to make your mouse work?

Cheers,
Erkki

---

### Post by Dam on 2005-04-20
Ok, here is a part of my xorg.conf file.

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Do you need more?

Moreover, I tried the commands suggested by wimva in the other topic ([http://ubuntuforums.org/showthread.php?t=8001](http://ubuntuforums.org/showthread.php?t=8001)), and it worked fine.

I thank you all very much for your help!

---

### Post by Abasher on 2005-04-20
Great to see so many relpys in such short time! Thanks for your time, dudes.

Sorry to hear I'm not alone in my sufferings Dam  :wink: .

My xorg.conf has just the same InputDevice configuration parameters as yours.

If it is power management related, when does the computer enter S2 suspend? Is that just CPU throtteling?

If it a common thing to do for every ACPI-using OS, why does it only affect Ubuntu?

---

### Post by Abasher on 2005-04-29
I'm afraid I've been unable to resolve this issue.

I'm afraid it will force Ubuntu of my laptop  :sad:, and effectively out of my world. Really sad, since it's been a very positive experience otherwise.

With hopes for future releases!  :wink:

---

### Post by ZiZe on 2005-04-30
[QUOTE=heimo]Seems like laptop model specific problem:
[http://ubuntuforums.org/showthread.php?t=8001]("http://ubuntuforums.org/showthread.php?t=8001")
 
Found something on BIOS update release paper (S2 - suspend?) maybe related?
[http://download.fujitsu-siemens.com/WDB/download.asp?dir=Public\KE0030600&Attachment=SBM2002_039_GB.doc&Info=GenesisDoc]("http://download.fujitsu-siemens.com/WDB/download.asp?dir=Public\KE0030600&Attachment=SBM2002_039_GB.doc&Info=GenesisDoc")
 
I guess disabling power management is not an option...[/QUOTE]
 No, this is  not a laptop specific problem.
i have the same problem om a
p4 3ghz prescott
Asus P4P800-E Deluxe
2gb pc3200 ram
Microsoft Intelli Explorer 3.0
Logitech Itouch keyboard

And it is quite frustrating, i did not have this problem i warthy.
Some times the mouse can work fine a couple of days before it freezes, and sometimes it freezes every 15 minuttes,

---

### Post by heimo on 2005-04-30
[QUOTE=ZiZe]No, this is not a laptop specific problem.[/QUOTE] Ok. But on this thread two different people have C1020 and on another thread (linked on this thread) is third with same laptop model and same problem - and that looks like very unprobable coincidence. So there's probably some better explanation, some [ rule out ] chpset [ / rule out ] or USB device or ... I don't know. Hopefully people with this problem can find the cause. I only gave my observation.

Maybe it's related to ACPI. Anyone tried to disable ACPI?

---

### Post by Dam on 2005-05-02
Personnaly, I had this problem with Warthy too.

I have the same feelings as you Abasher  :-? 

Every two weeks I update my Ubuntu and hope the problem is solved until it freezes again  :neutral: 

I am not an expert and so I think I am not able to find the solution... but I will keep trying anyway  :)

---

### Post by Dam on 2005-05-02
[QUOTE=heimo]Maybe it's related to ACPI. Anyone tried to disable ACPI?[/QUOTE]
What is ACPI exactly? I read about it in many forums but I still don't know what are the pro's and the con's of disabling it.

---

### Post by heimo on 2005-05-02
ACPI is the modern version of APM. In other words, power management. Another technology which has caused headaches is APIC (programmable interrupts). If I had some mysterious hardware lockups, I'd try disabling these two and see if there was any effect. (You can disable these by disabling from BIOS settings and putting couple parameters to grub configuration file).
 
I can sense the frustration on this subject. It's very sad that these kind of problems occur. Also it's hard to track down the original reason why these hangups happen (because of the nature of the problem, random, unpredictable behaviour). We can't even know if these problems are directly related or two or three different problems causing similar symptoms.
 
Anything in logs? /var/log/messages? Any chance that it could be faulty BIOS? Bios upgrades available? (check changes before flashing).
 
:-(

---

### Post by ZiZe on 2005-05-02
[QUOTE=heimo] 
Anything in logs? /var/log/messages? 
 [/QUOTE]

yes, i have put in on my website since they are quite long
[www.zize.org/messages.log](www.zize.org/messages.log)
[www.zize.org/kern.log](www.zize.org/kern.log)

---

### Post by ZC3rr0r on 2005-05-02
Another victim of the weird mouse problem joins the thread. I got a Fujitsu-Siemens Lifebook C1300 (dunno exactly) and I have the exact same problems using my Logitech MX300. The weird thing however is that the same problems hit me under windows XP last night using a different computer (AMD64 thingie) and a differant mouse (Logitech MX510) Perhaps it's a logitech thing? Because my laptop is Via and my pc is Nforce, I rule the chipset out....

<edit> Coming to think about it, my pc does this with either mouse I attach, perhaps the USB controller is just dead...:S Nvm my previous ranting about the chipset rule-out, Could it be a chipset specific problem? I looked it up, and it looks like all the laptopsmentioned are using a VIA chipset.

<edit> And nvm the above edit as well,because someone has the sameproblem in an intel chipset too. Perhaps it's a problem with Logitech and Microsoft mouses?

---

### Post by Dam on 2005-05-04
[QUOTE=ZC3rr0r]the same problems hit me under windows XP last night using a different computer (AMD64 thingie) and a differant mouse (Logitech MX510)[/QUOTE]Personally, it never happened under Windows XP (I am using a Microsoft mouse).

[QUOTE=ZC3rr0r]Perhaps it's a problem with Logitech and Microsoft[/QUOTE]That could be. I am exclusively using Microsoft USB mouses (I tried three of them and they all had the same beahviour).
However, many people are using the same brands and don't have the same problem.



Furhermore, for those who might be interested, I had not the same problem under Mandrake 9.x and 10.0

---

### Post by heimo on 2005-05-04
[QUOTE=ZiZe]yes, i have put in on my website since they are quite long
[www.zize.org/messages.log]("http://www.zize.org/messages.log")
[www.zize.org/kern.log]("http://www.zize.org/kern.log")[/QUOTE]
 
This bug (which is closed...) sounds similar:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=287934]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=287934")
 
Are you using 2.6.10? (uname -r)
 
Can you try another kernel version, preferrably some older one, like 2.6.8 or 2.4 series?

---

### Post by tawk on 2005-05-09
Hello,
i basically have the same problem: My mouse stops working after some time (3-20 minutes)
But I have a totally different hardware, its an rather old (mobile amd 1600) laptop based on a Mitac 7321 with VIA KN 133 chipset. And my mouse is a logitech optical wheel mouse.

I had this problem already with Suse 9.1:
There I could resolve this problem by pulling out the battery of my laptop or by acpi=off. With the usb to ps2 converter, my mouse runs perfectly both in Ubuntu and Suse. In Ubuntu I don't want to disable acpi, because cpu frequency scaling does not work in consequence. 

@wimva: Your mentioned "temporarily" trick works.

This issue seemed very strange and unique to me, but as you have the same problems I'm still hoping for a solution...

---

### Post by heimo on 2005-05-10
I don't know if it's already mentioned, but one way to solve this may be to use "USB legacy" "USB PS/2 emulation" or similar setting in BIOS. However those laptop BIOSes I've seen are quite minimalistic and may lack this option.

---

### Post by Dam on 2005-05-10
> one way to solve this may be to use "USB legacy" "USB PS/2 emulation" or similar setting in BIOS. However those laptop BIOSes I've seen are quite minimalistic and may lack this option.I tried to find this option... or a similar one. But, as you said, the BIOS is very minimalistic and I could not find anything that could help me.

What I did instead was to change my "Internal ps/2 settings" from "Auto disable" to "Always enable"... but it freezed a few minutes ago!

Could it not be a GNOME related problem? This morning I tried a live version of Knoppix (KDE) and did not encounter the problem.

---

### Post by heimo on 2005-05-11
[QUOTE=Dam]
Could it not be a GNOME related problem? This morning I tried a live version of Knoppix (KDE) and did not encounter the problem.[/QUOTE]
 
I highly doubt this would (or even could) be desktop / window managers fault. It could be Xorg, but I suspect it goes even deeper to kernel level or BIOS / hardware. I'd try using older kernel for some time. Oh, and if you have used Knoppix for long enough time to make sure that this problem doesn't affect Knoppix, check which version of kernel you have there (uname -r).
 
This is very annoying problem. I almost wish I'd have this problem so I could diagnose / debug / hunt this problem and (hopefully) find out what's causing it.

---

### Post by Dam on 2005-05-16
> if you have used Knoppix for long enough time to make sure that this problem doesn't affect Knoppix, check which version of kernel you have there (uname -r)Under Knoppix, I was using kernel 2.6.11. However, I should spend more time under this distribution to be sure that it does not freeze... but it is a little bit boring with a Live CD! (if possible, I would like not to have to reinstall!)

> I'd try using older kernel for some time.I am not an expert in changing kernel but I will try this option as soon as I have understood how to do it!

> This is very annoying problem. I almost wish I'd have this problem so I could diagnose / debug / hunt this problem and (hopefully) find out what's causing it. If you want my laptop, you can have it!  :grin:   :grin:  Anyway, I really appreciate your help!


Today, I also tried the "noapic" and "noioapic" kernel options for the boot sequence... but it did not solve my problem  :-|

---

### Post by tawk on 2005-05-24
I did not really solve the problem now, but I could avoid the symptoms by setting  acpi=off in the grub boot command. As I have mentioned, this has already worked on my old SUSE installation.

But on Ubuntu it took me some time to get powernow working while acpi is disabled. In detail, I switched from ACPI to APM, as it was described somewhere else in this forum. Additionally, I had to put the module powernow-k7 for my mobile athlon XP in /etc/modules.
Not really hard to do, but for me as a linux beginner it was not that easy to find.

I'm now quite happy, because I can use my usb-mouse without ps/2 adapter and as there is no difference concerning the power-consumption.

Does acpi=off solve the mouse problems on your laptops, too? Someone else made this proposal on the page before...

Thank you for your help!

---

### Post by peluchio on 2005-05-30
[QUOTE=tawk]I did not really solve the problem now, but I could avoid the symptoms by setting  acpi=off in the grub boot command. As I have mentioned, this has already worked on my old SUSE installation.

But on Ubuntu it took me some time to get powernow working while acpi is disabled. In detail, I switched from ACPI to APM, as it was described somewhere else in this forum. Additionally, I had to put the module powernow-k7 for my mobile athlon XP in /etc/modules.
Not really hard to do, but for me as a linux beginner it was not that easy to find.

I'm now quite happy, because I can use my usb-mouse without ps/2 adapter and as there is no difference concerning the power-consumption.

Does acpi=off solve the mouse problems on your laptops, too? Someone else made this proposal on the page before...

Thank you for your help![/QUOTE]
 Greetings list! I also just installed ubuntu on my Lifebook C1020, with the same problem. Has anyone found any solution yet? I resorted for the time being, to invoking a shell script with the modprobe commands suggested on the previews posts.

Update: The problem does *seem* get solved with by appending acpi=off on the kernel entry in the /boot/grub/menu.lst file.

---

### Post by Dam on 2005-06-13
With *acpi=off* in the boot menu, it seems to work fine. I have not experienced any freeze since I chose this solution.

However, with kernel 2.6.10, my processor does not look very happy and can not stop asking for refreshments (i.e. my fan is working every other minute).

That is very boring...

So, I decided to install kernel 2.6.11.
The basic 'mouse freezing' problem still remains but, with acpi=off, I now have a very satisfying operating system without any strange behaviour (except for the sound that is very weak).

Today, I am certainly one of the happiest Ubuntu user...  :smile:

Thank you all for your help. I will keep trying finding a way to definitely solve the problem and of course I will let you know if I succeed!

Regardss from Belgium,

Damien

---

### Post by Dam on 2005-06-23
[QUOTE=tawk]on Ubuntu it took me some time to get powernow working while acpi is disabled. In detail, I switched from ACPI to APM, as it was described somewhere else in this forum.[/QUOTE]How did you manage to get it? I still could not find a solution. I always get the following message: > powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email] 
I have sysfs mounted in fstab and a 2.6 kernel. However, when I call cpufreq, I get that:> FATAL: Module cpufreq not found.
and "lsmod | grep cpu" gives me the following outcome:> 
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_userspace       4444  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0 
Sound and CPU scaling are my last problems (which I had not under older kernel).

Any insight?

Thank you!

---

### Post by Dam on 2005-07-01
This problem is weird!

I have collected a few insights since the last time...

1. (With acpi=on) When I unplug my battery and my network cable and that the module called "sony_acpi" is unloaded, all my problems are solved (sound ok, cpu scaling ok, and no mouse freezing). However, with either the battery or my network cable plugged in, my mouse starts freezing again...

2. When I set acpi=off in the boot menu, my problems are solved... but I do not have sound anymore as well as cpu scaling.

What about you?

---

