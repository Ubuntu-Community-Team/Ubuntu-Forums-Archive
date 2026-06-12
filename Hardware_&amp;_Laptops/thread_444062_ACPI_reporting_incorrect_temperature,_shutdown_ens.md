---
title: "ACPI reporting incorrect temperature, shutdown ensues"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by jamieplucinski on 2007-05-15
This is a new bug (on my system) since I dabbled with the latest Ubuntu and Ubuntu Studio releases. Whenever I try and do anything remotely GPU intensive the system shuts down, and the following is written in the /var/log/syslog file:
> May 15 00:23:45 maplesyrup kernel: [ 3391.624000] ACPI: Critical trip point
May 15 00:23:45 maplesyrup kernel: [ 3391.624000] Critical temperature reached (71 C), shutting down.

So it's obvious that the CPU is overheating, or is it? The logs point to that, but the GPU is only performing about 10% of the things I used to do in Windows Vista with no problems with CPU temperature. I used to run WoW (World of Warcraft), Dreamweaver, WinAmp, Firefox, Thunderbird, Navicat, Live Messenger, and random other things with no problems. So this has lead me to believe that somewhere, Ubuntu is being fed bad data.

Doing 
> cat /proc/acpi/thermal_zone/THRM/temperature
Displays 59 C most of the time,  and that's only from running Ubuntu in a Gnome running, terminal open state. Somewhere something is incredibly wrong, since the same tests on Windows show the CPU at ~45C and even when running games I never come close to 60 degrees. I've had to force Ubuntu to run up to 71C to be able to watch videos online in Firefox.

So does anyone have any ideas on what I can do to get Ubuntu working properly? I **do not **want to go back to Windows.

System is a Compaq R4225CA with a 200m chipset, and an AMD Athlon 3500+ processor. I am using Ubuntu Studio 7.04 (uname -a outputs: Linux maplesyrup 2.6.20-15-lowlatency #2 SMP PREEMPT Sun Apr 15 07:39:03 UTC 2007 i686 GNU/Linux)

---

### Post by whitetrash on 2007-05-16
I'm having the exact same problem. 100% the same - and my hardware is pretty much identical.

I have a Comapq Presario R4000, AMD 3500+, 1 GB RAM, ATi 200M.

I set my screen saver to the Plasma one and a few minutes after it comes on Ubuntu shuts down. During the shutdown it tells me that I'm running at 71C as well.

It's kinda weird that we're both shutting down during the same type of use, with the same temp. being reported.

I'm guessing it must be a bug (something is 'causing the hardware to run way too hot).

I have Windows XP on the same machine (J'm dual booting) and I've never had a heat issue in Windows with this computer.

Does anyone have any suggestions?

I haven't updated or changed the default 200M driver installed by default and I multi task like crazy (surfing while listening to music, sometimes playing a video with no sound, remote desktop running at the same time) so the CPU is pretty taxed and I don't shutdown, a little while after the graphics card starts getting used bam, the PC is shutting down.

I'm leaning towards graphics but I'm just learning Linux so I have no clue how to do anything about this.

Any help would be much appreciated. :confused:

---

### Post by robin.w on 2007-05-19
Hi guys,

not alone!!! When I started to boot my Linux this morning (distro Kubuntu 7.04 Feisty Fawn) I've got exactly the same issue. And yesterday everything was ok. I didn't upgrade, so I was pretty surprised when I saw that my CPU reached critical temperature.
My laptop configuration: HP Compaq Presario M2000, CPU AMD Turion64, RAM 1GB, ATI 200M.

---

### Post by jamieplucinski on 2007-05-20
I'm 100% positive that the problem lies with ACPI, I installed a Gnome Applet that monitors the temperature of the system, and the first (CPU) sensor was bugged, but the second was accurate, around 41 degrees, which is exactly the temperature I was getting when I checked in Windows. Yes software isn't always right, but with a margin for error of over 30 degrees... ;)

I'll re-install Ubuntu Studio soon, I need to get some code churned out and can't do it for more than 5 mins on Ubuntu :(

BTW I did try disabling ACPI in the grub loader options, and that completely disables my wireless card, so yeah, burn in Ubuntu, or stay cool in Hell (Windows), something got messed up somewhere.

---

### Post by jamieplucinski on 2007-05-24
More information:
I am using Computer Temperature Monitor 0.9.6.1 from [http://computertemp.berlios.de/](http://computertemp.berlios.de/) right clicking the applet when it's on my gnome panel and choosing properties gives me the following under "Select Sensor to monitor":
[LIST]
[*]ACPI
[*]Kernel i2c sensors (hwmon)
[/LIST]

Thermal zones are:
[LIST]
[*]THRM (for ACPI)
[*]hwmon0 (1) (for Kernel i2c sensors (hwmon))
[/LIST]

ACPI is reporting temperatures of anywhere between 11 and 33 degrees higher than the hwmon0 temperature (which is the same temperature under Windows)

Anyone have any ideas?

---

### Post by foresth on 2007-06-15
Hi,
the same problem here :(. Any news?

---

### Post by Big Dan on 2007-07-28
I'm having the same issue here, Compaq Persario M2000.. Laptop starts, gnome loads and I get the "shutting down fatal temperature error" 41 F.. It only seems to happen when I'm on battery power.. When plugged in, I can run it for hours without an issue. 

Normally, I'm attached to my desk anyhow so it doesn't bother me.. This time the computer was off all day, at room temperature and Ubuntu threw a fit about a "fatal temperature". I booted into Windows and all is fine. 

BTW I'm running Feisty. 

Has there been any resolution to this? Can I turn off the sensor somehow?

---

### Post by CutterXYZ on 2007-07-29
Maybe the system interprets teperatures in Fahrenheit as Celsius, then a temperature of 95°F (35°C) can seem critical if interpreted as °C.

---

### Post by henriquemaia on 2007-07-30
I'm installing Feisty on a friend's laptop and I'm having the same issue here. The laptop shutsdown with temperature critical message but I'm sure the temperature readings are wrong, since I'm running the laptop over to iced coolers and when shutting down the laptop base is totally cool. The problem seems to be closely related to the graphic card, because when I run the laptop in graphical mode, the shutdown occurs 1 or 2 minutes after it starts. I'm running it for an hour now in text mode (posting this in Links2) and the laptop is running fine and silently.

Any ideas how to solve this?

Edit: after another shutdown after using graphical mode, I insisted in rebooting this time only using text mode. The computer shutdown when installing packages, so I assume my above reasoning is not valid anymore.

---

### Post by henriquemaia on 2007-08-02
> **henriquemaia said:**
> I'm installing Feisty on a friend's laptop and I'm having the same issue here. The laptop shutsdown with temperature critical message but I'm sure the temperature readings are wrong, since I'm running the laptop over to iced coolers and when shutting down the laptop base is totally cool. The problem seems to be closely related to the graphic card, because when I run the laptop in graphical mode, the shutdown occurs 1 or 2 minutes after it starts. I'm running it for an hour now in text mode (posting this in Links2) and the laptop is running fine and silently.

Any ideas how to solve this?

Edit: after another shutdown after using graphical mode, I insisted in rebooting this time only using text mode. The computer shutdown when installing packages, so I assume my above reasoning is not valid anymore.

Solved it by installing another distro on the laptop. This is a very annoying bug on Ubuntu.

---

### Post by rebegin on 2007-08-02
i've had problems with acpi in feisty also but everything is solved now by upgrading the kernel to gutsy's one. it's easy to do:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
give it a try.

---

### Post by skompier on 2007-09-30
I had the same problem of Feisty saying that the CPU overtemp had been reached and shutting down my system. I did the kernel update as described above and here [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) and all is well. I was easy to do and I've seen no issues.

---

### Post by shadarack on 2007-10-07
I'm having a similar problem with a system of mine, but instead of reporting a temperature that's too high, it's reporting it too low.

The following command is run:

cat /proc/acpi/thermal_zone/THRM/temperature

I get -230 reported.

Periodically, and for no reason that I can see, the system simply shuts itself down. The monitor goes black, the monitor signal light darkens as if the computer were shut down. Case fans continue to function and CD rom still has the power to eject. When I opened up the system, I noticed that when it shuts down like this, the CPU fan stops spinning, although all other systems apparently continue to function.

I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

to upgrade kernel to Gutsy, and it appeared to work...for a short time.

jamieplucinski mentioned disabling ACPI in GRUB - how can one do that, and what would be the disadvantages of doing so?

---

### Post by Thasaidon on 2007-10-07
I had Feisty (Dualboot with WindowsXP) running on my HP Pavilion ZE5400 just fine for a while, but from one day to the next, I was getting the same errors with my CPU beeing too hot and the system shutting down.
I didn't find a solution then, other than that it is supposed to be a bug in Ubuntu, and installed another distro.

However, I would like to give Ubuntu another try, but I'm not going to install Feisty knowing it has this anoying bug. Some people say updating to Gutsy's kernel solves the problem, so I guess I'd better wait for Gutsy to be released? Or does anyone have a solution yet?

---

### Post by Felipe_U on 2007-10-21
Im having the same issues on a desktop with gusty installed :( it says it reached 98 degrees and it shutsdown.....anyway to turn Ubuntu temp readings or at least ignore them?

Regards,
Felipe

---

### Post by Thasaidon on 2007-10-21
This may be a solution...

I'm running a dualboot with windowsXP and am using Grub as the boot loader
I added "acpi=off" to the kernel line in Grub, and sofar things seem to run ok (for now).

as stated somewhere in this forum...
"To turn ACPI off edit the /boot/grub/grub.conf file and add "acpi=off'' at the end of the kernel line that corresponds to kernel 2.x.xx-xx and reboot the machine."

---

### Post by Maconvert on 2008-04-11
That's pretty pathetic on Ubuntu's part.
They still haven't fixed this.
What distro did you switch to anyway?

Regards.

---

### Post by Maconvert on 2008-04-12
Hi,

I've installed LM-Sensors on my Ubuntu Gutsy machine and, with three movies playing I can't get the CPU temperature above 35 degrees Celsius.

So, as I see it, there are two different things that could be happening: (1) Ubuntu is reading the value differently from LM-Sensors and shutting down when it shouldn't (i.e. software bug) - OR - (2) there is something wrong with the actual sensors and the processor is actually much hotter and the CPU is using it's built in fail-safe to shut everything down to save itself (i.e. Ubuntu is not the culprit).

In regards to cause #1, I wonder if there could be something to this notion that Ubuntu is reading a Fahrenheit value and interpreting it as a Celsius value. 35'C is about 95'F and a previous poster said that his PC shuts down at 98'C. 

Anyway, I think the next thing that I'm going to do is swap out the drive and install Windows and see if the problem still continues. If it does, then this is a hardware problem. If it stops, then I'm going to need to get a different Linux distro, which would suck because I really like the Ubuntu GUI.

Cheers.

P.S.
If this turns out to be an Ubuntu problem then they owe be $61 for the new power supply I bought.

---

### Post by Thasaidon on 2008-04-14
> Anyway, I think the next thing that I'm going to do is swap out the drive and install Windows and see if the problem still continues. If it does, then this is a hardware problem. If it stops, then I'm going to need to get a different Linux distro, which would suck because I really like the Ubuntu GUI.
I can tell you beforehand that nothing will show in Windows.
I was running a dual-boot with Windows XP and Ubuntu 7.4 (later 7.10)
and in windows everything ran just fine, but as soon as I booted Ubuntu, I got the temp warning and the system just shut down.
When I then restart the system and boot in XP, there is nothing wrong what so ever.
Even when the system was "cold" and I booted into Ubuntu first, I even got the message while Ubuntu was still starting up sometimes.

So either Ubuntu is reading the temps wrong, or they mistaken Fahrenheit for Celcius or whatever.
Either way, it's an Ubuntu problem, because other distro's (Like Suse of Slackware) do not have this weird behavior on the same system.

SuSE 9.2 seems to work best on the system (considering wireless and all), but since that's an old distro, I'm still looking at some newer versions of various distro's.
Maybe I'll put BackTrack 3 on it when that is released, BackTrack 2 ran like a peach.

---

