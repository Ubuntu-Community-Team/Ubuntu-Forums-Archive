---
title: "Ubuntu freezes when started w/o AC cable"
date: 2017-05-04
forum: Hardware
---

### Post by theraf90 on 2017-05-04
Hi there everyone,
I've installed ubuntu gnome on my MSI GS40 laptop and it works great when on AC power.
Unfortunately whenever (statistically 5 out of 6 times) I _start my laptop with the cable unplugged_ it just freezes after about 50 seconds...
Incredibly enough, whenever I start it with the AC and unplug the AC (after about a minute) my laptop works amazingly well for hours (up to ~5)!!!
Furthermore I cannot put my laptop in suspension mode, because it won't start after it...
How can I fix this issue?

What I've tried:

Boot flags
```
intel_idle.max_cstate=5
```
```
intel_idle.max_cstate=7
```
```
acpi_osi=Linux
```
```
acpi_osi=Linux acpi_osi='!Windows 2012'
```

Using nvidia drivers:
all up to 385, but unfortunately when I type in ```
sudo prime_select intel
``` and log out/in I'm stuck in a loop until I run in TTY mode ```
sudo prime_select nvidia
```.

So now I get about ~8W consumption with nouveau drivers **only** if I unplug AC AFTER my laptop's fully operational.

Thank you for reading my cry for help!
Aaron

My [ATTACH]274951[/ATTACH] using ```
hwinfo --short
```


EDIT:
I've tried using
```
intel_idle.max_cstate=1
```
but it makes my battery last about an hour and a half compared to ~6-7 hrs when unplugged after boot.

---

### Post by DuckHook on 2017-05-04
Welcome to the forums, theraf90.

[LIST=1]
[*]What version of Ubuntu are you running?
[*]Have you tried another version in a LiveUSB?
[*]Have you tried another flavour in a LiveUSB?
[/LIST]
A total shot-in-the-dark, but perhaps you can try the following: [https://askubuntu.com/questions/292696/ubuntu-crashes-when-on-battery-power](https://askubuntu.com/questions/292696/ubuntu-crashes-when-on-battery-power)

---

### Post by theraf90 on 2017-05-04
Hi DuckHook,
thank you for your reply!

So let's get to it:

[LIST=1]
[*]Gnome Ubuntu 16.04.2 LTS with 4.8.0-51-generic kernel;
[*]I haven't tried other distros using LiveUSBs on battery;
[*]I have tried normal Ubuntu 16.04.2 installed before GNOME, but only on AC so I don't really know if the issue was present.
[/LIST]
[INDENT]
[/INDENT]
**Wireless**
Didn't actually think about wifi adapter (bluetooth doesn't work on my kernel, but that, I thought, would be a secondary problem to solve later). Now that I'm thinking about it when I added intel_idle.max_cstate=1 it did make my laptop work without hangs (I'll update OP)... That would exclude the wifi adapter from the problem list right?

The big problem with intel_idle.max_cstate=1 is that it makes my battery last 1/5th of the time it would work for after detaching it once it's fully booted.

**NewBug?** One more bug I've found out about today that might help is that, whenever on battery I send a HW scan with a command like **hwinfo **or **lshw,** the computer hangs.

Let me know in light of this new info what you might think!
Aaron


> **DuckHook said:**
> Welcome to the forums, theraf90.

[LIST=1]
[*]What version of Ubuntu are you running?
[*]Have you tried another version in a LiveUSB?
[*]Have you tried another flavour in a LiveUSB?
[/LIST]
A total shot-in-the-dark, but perhaps you can try the following: [https://askubuntu.com/questions/292696/ubuntu-crashes-when-on-battery-power](https://askubuntu.com/questions/292696/ubuntu-crashes-when-on-battery-power)

---

### Post by DuckHook on 2017-05-04
[LIST=1]
[*]Do you still have a 4.4. kernel? If so, try that.
[*]So you layered Gnome over an Ubuntu install? If so, log in to the original Ubuntu DE and see if that makes a difference.
[*]If that doesn't work, try the wireless fix linked to in my first post. If it doesn't work, it can always be reversed. That link alludes to a setting/bug where the wireless script calls on the system to suspend after a certain inactive time on the wireless NIC. Your intel_idle.max_cstate kernel setting also prevents the CPU from ever going into idle, so they may be related.
[*]The lshw scan problem may be useful: instead of:```
sudo lshw
```&#8230;please refine your scans with the -c switch to narrow down the exact subsystem causing the hang. i.e.```
sudo lshw -c network
sudo lshw -c bus
```&#8230;etc. For a complete list of the subsystems (and their names) that you can use, do:```
lshw -short
```
[/LIST]

---

### Post by theraf90 on 2017-05-05
[LIST=1]
[*]I don't have 4.4 anymore, but I remeber it had bluetooth working, it seemed to me when I was using it that it didn't have any issues though, do you recommend a downgrade?
[*]No, I tried most distros to find an X environment that suited my desing OCD and gnome was the best fit, the only one I used for more than 10 minutes was Ubuntu, then I decided to stick with Gnome;
[*]Got it. I don't have pm-utils installed, but tlp and powertop. My next step with tlp would have been to downclock my cpu min and max values, but at this point it's more important to have it to work properly :D Should I uninstall tlp in favour of pm-utils and apply the patch? Is there something particular I could tweak in tlp to help me?
[*]So using [ATTACH]274960[/ATTACH] I haven't been able to hang my laptop, at the moment I've been using it for about one hour straight without booting it plugged in (strange) the only thing that happened was a gnome restart about 50 seconds in where I was thrown back to my login page...
[/LIST]


I've tried a ```
lshw -enable pci
```

and got: [ATTACH]274961[/ATTACH]

---

### Post by theraf90 on 2017-05-06
Hey @DuckHook I've noticed that sometimes I get this error message:

```
[COLOR=#6A6A6A][FONT=arial]**plymouthd crashed with SIGSEGV**[/FONT][/COLOR][COLOR=#545454][FONT=arial] in script_obj_deref_direct()[/FONT][/COLOR]
```

So, scrolling down the suggested fix was to upgrade the package:
```
passwd
```
after doing that I upgraded:
```
login
```
Now after rebooting plugged in I didn't get that error, so when I get back later (I'm going to see [this]("http://www.elvisilmusical.it/en/")) I'll check without AC.

Do you think this error could be related to my problem?

Thank you again,
Aaron

NEXT DAY UPDATE:
Unfortunately the plymouthd fix didn't help... :(

---

### Post by theraf90 on 2017-05-11
So...
I've done some digging and I came up with this pdf ([ATTACH]275047[/ATTACH]) from a Dell technician that explains how to change c-states dynamically! So my idea was to find a way to start the laptop with the content of /dev/cpu_dma_latency set to the minimum value and then change it after 2-3 minutes in automatic with a deferred start program that sets the cstates to their proper value again...
We would have 2 possible outcomes:


[LIST=1]
[*]the laptop runs error free for hours;
[*]the laptop freezes as soon as i leave it alone for 5 minutes.
[/LIST]

The next problem to solve would be to fix the suspend issue that's been haunting me. Every time I try to suspend the laptop (closing the lid or power button) it would just loop on a black screen and not go into suspend mode... Ideas?

---

