---
title: "CPU 1 Overloaded/Overheating?"
date: 2016-11-17
forum: Hardware
---

### Post by Disposition96 on 2016-11-17
I thought it was windows but linux seems to be doing the same thing, my first core (1) in this case is consistently at 80% + when my laptop is doing absolutely nothing, I believe this is why my laptop CPU is sitting at 80-90C consistently.  What would cause this?  Just a chip malfunction at this point?  The laptop is 5 years old, I assumed it was windows causing me this issue but I've now come to feel like it's not, the other cores are literally between 2 & 15%

When I use htop it says I'm using 15% total cpu with firefox but core 1 is at 80+%

 PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 6640              root      20   0       0      0      0 S  75.7  0.0   8:22.20 kworker/0:0 
 2817   rory      31  11 2205968 949260 136840 S  20.9 12.1  20:15.07 firefox     
 1048     root      20   0  271696 108056  53396 S   5.0  1.4   3:46.94 Xorg

[ATTACH=CONFIG]272192[/ATTACH]

---

### Post by kpatz on 2016-11-17
What's pid 6601 in your screenshot?  It's what's pegging that one core.  You can use the arrow keys to scroll htop left and right to show more of the command line.

---

### Post by Disposition96 on 2016-11-18
[ATTACH=CONFIG]272202[/ATTACH]

Here's a larger picture of just everything, that one is no longer that, I am scrolled all the way to the top... Just doesn't make sense.

[ATTACH=CONFIG]272218[/ATTACH]

Like this is nuts.. What's causing this?

---

### Post by kpatz on 2016-11-18
Those shots don't show whatever's hogging the cpu... make sure you're scrolled to the top of the list so the process with the highest CPU% shows up at the top.  The "home" key will take you there.

---

### Post by Disposition96 on 2016-11-18
> **kpatz said:**
> Those shots don't show whatever's hogging the cpu... make sure you're scrolled to the top of the list so the process with the highest CPU% shows up at the top.  The "home" key will take you there.

I'm telling you right now, that is the top of the list. 

[ATTACH=CONFIG]272222[/ATTACH]

---

### Post by kpatz on 2016-11-21
Try hitting Shift+K while in htop to show kernel threads.

---

### Post by Disposition96 on 2016-11-21
I have done this, now maybe someone can help me get to the "root" of the problem.  LOL


[ATTACH=CONFIG]272289[/ATTACH]


I found this but don't want to go ahead and do it as I Don't know what any of the commands mean.

**[http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)**

---

### Post by Disposition96 on 2016-11-23
Bump. Sorry if it's not allowed, just trying to get this bad issue resolved.

---

### Post by QIII on 2016-11-23
Hello!

It is perfectly OK to bump if you have not gotten a response for 12 hours.

Cheers!

---

### Post by kpatz on 2016-11-23
Although your htop shows kworker using 0% CPU, it's at the top of the list so it's probably using a lot and htop isn't reporting it accurately.

There may be some suggestions here: [http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)
Also here: [http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu](http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu)

My suggestion would be to try stopping/disabling anything you can, one at a time, to see if the problem is tied to a particular device or service.  Unplug any USB devices, turn off wireless, unmount filesystems, unload modules with modprobe -r, etc.

---

### Post by Disposition96 on 2016-11-23
Sorry, I don't understand why but it uploaded the wrong file... Definitely not the one that I Wanted to show you! 

[ATTACH=CONFIG]272354[/ATTACH]

---

### Post by Disposition96 on 2016-11-24
Bump

---

### Post by kpatz on 2016-11-25
Did you try my suggestions in my previous post?  Since it's a kernel thread doing it, it could be a device driver causing it.

---

### Post by Disposition96 on 2016-11-25
> **kpatz said:**
> Did you try my suggestions in my previous post?  Since it's a kernel thread doing it, it could be a device driver causing it.

I did try unplugging usbs ect, I had found the first thread you gave me before but I don't actually know what all of the commands do/mean and I Would really hate to mess things up. :D  (Wrong system for that, I know)

When I do the first thing on the first thread to find out the "gpe" I get this :

```
/sys/firmware/acpi/interrupts/ff_gbl_lock:       0   enabled
/sys/firmware/acpi/interrupts/gpe15:       0   invalid
/sys/firmware/acpi/interrupts/gpe05:       0   invalid
/sys/firmware/acpi/interrupts/gpe3F:       0   invalid
/sys/firmware/acpi/interrupts/gpe33:       0   invalid
/sys/firmware/acpi/interrupts/gpe2F:       0   invalid
/sys/firmware/acpi/interrupts/gpe23:       0   invalid
/sys/firmware/acpi/interrupts/gpe1F:       0   invalid
/sys/firmware/acpi/interrupts/gpe13: 2313770   enabled
/sys/firmware/acpi/interrupts/gpe0F:       0   invalid
/sys/firmware/acpi/interrupts/gpe03:       0   invalid
/sys/firmware/acpi/interrupts/gpe3D:       0   invalid
/sys/firmware/acpi/interrupts/gpe31:       0   invalid
/sys/firmware/acpi/interrupts/gpe2D:       0   invalid
/sys/firmware/acpi/interrupts/gpe21:       0   invalid
/sys/firmware/acpi/interrupts/gpe1D:       0   invalid
/sys/firmware/acpi/interrupts/gpe11:       0   invalid
/sys/firmware/acpi/interrupts/ff_pwr_btn:       0   enabled
/sys/firmware/acpi/interrupts/ff_slp_btn:       0   invalid
/sys/firmware/acpi/interrupts/gpe0D:       0   disabled
/sys/firmware/acpi/interrupts/gpe01:       0   enabled
/sys/firmware/acpi/interrupts/ff_pmtimer:       0   invalid
/sys/firmware/acpi/interrupts/gpe3B:       0   invalid
/sys/firmware/acpi/interrupts/gpe2B:       0   invalid
/sys/firmware/acpi/interrupts/gpe1B:       0   invalid
/sys/firmware/acpi/interrupts/gpe38:       0   invalid
/sys/firmware/acpi/interrupts/gpe0B:       0   disabled
/sys/firmware/acpi/interrupts/gpe28:       0   invalid
/sys/firmware/acpi/interrupts/gpe18:       0   invalid
/sys/firmware/acpi/interrupts/gpe08:       0   invalid
/sys/firmware/acpi/interrupts/sci: 2314027
/sys/firmware/acpi/interrupts/gpe36:       0   invalid
/sys/firmware/acpi/interrupts/gpe26:       0   invalid
/sys/firmware/acpi/interrupts/error:       0
/sys/firmware/acpi/interrupts/gpe16:       0   invalid
/sys/firmware/acpi/interrupts/gpe06:       4   enabled
/sys/firmware/acpi/interrupts/ff_rt_clk:       0   disabled
/sys/firmware/acpi/interrupts/gpe34:       0   invalid
/sys/firmware/acpi/interrupts/gpe24:       0   invalid
/sys/firmware/acpi/interrupts/gpe14:       0   invalid
/sys/firmware/acpi/interrupts/gpe04:       0   invalid
/sys/firmware/acpi/interrupts/gpe3E:       0   invalid
/sys/firmware/acpi/interrupts/gpe32:       0   invalid
/sys/firmware/acpi/interrupts/gpe2E:       0   invalid
/sys/firmware/acpi/interrupts/gpe22:       0   invalid
/sys/firmware/acpi/interrupts/gpe1E:       0   enabled
/sys/firmware/acpi/interrupts/gpe12:       0   invalid
/sys/firmware/acpi/interrupts/gpe0E:       0   invalid
/sys/firmware/acpi/interrupts/gpe02:       0   enabled
/sys/firmware/acpi/interrupts/gpe3C:       0   invalid
/sys/firmware/acpi/interrupts/gpe30:       0   invalid
/sys/firmware/acpi/interrupts/gpe2C:       0   invalid
/sys/firmware/acpi/interrupts/gpe20:       0   invalid
/sys/firmware/acpi/interrupts/gpe1C:       0   invalid
/sys/firmware/acpi/interrupts/gpe10:       0   invalid
/sys/firmware/acpi/interrupts/gpe39:       0   invalid
/sys/firmware/acpi/interrupts/gpe0C:       0   invalid
/sys/firmware/acpi/interrupts/gpe00:       0   invalid
/sys/firmware/acpi/interrupts/gpe3A:       0   invalid
/sys/firmware/acpi/interrupts/gpe29:       0   invalid
/sys/firmware/acpi/interrupts/gpe2A:       0   invalid
/sys/firmware/acpi/interrupts/gpe19:       0   invalid
/sys/firmware/acpi/interrupts/gpe1A:       0   invalid
/sys/firmware/acpi/interrupts/gpe09:       0   disabled
/sys/firmware/acpi/interrupts/gpe37:       0   invalid
/sys/firmware/acpi/interrupts/gpe0A:       0   invalid
/sys/firmware/acpi/interrupts/gpe27:       0   invalid
/sys/firmware/acpi/interrupts/gpe17:     249   enabled
/sys/firmware/acpi/interrupts/sci_not:       0
/sys/firmware/acpi/interrupts/gpe07:       0   enabled
/sys/firmware/acpi/interrupts/gpe35:       0   invalid
/sys/firmware/acpi/interrupts/gpe25:       0   invalid
/sys/firmware/acpi/interrupts/gpe_all: 2314059


```

Oddly enough, I get the same one doing tons of interupts he does, I assume it is because it's a similar laptop.  So should I just continue to do what he does and hope for the best?

When I do the other one to see what's being used on CPU-0

```
[  226.291868]  [<ffffffffad9059e6>] tick_nohz_restart+0x66/0x70
[  226.291869]  [<ffffffffad905f83>] tick_nohz_idle_exit+0x93/0x120
[  226.291869]  [<ffffffffad8c7beb>] cpu_startup_entry+0x18b/0x350
[  226.291870]  [<ffffffffae0919e7>] rest_init+0x77/0x80
[  226.291870]  [<ffffffffae781fd3>] start_kernel+0x448/0x469
[  226.291871]  [<ffffffffae781120>] ? early_idt_handler_array+0x120/0x120
[  226.291871]  [<ffffffffae7812ca>] x86_64_start_reservations+0x24/0x26
[  226.291871]  [<ffffffffae781419>] x86_64_start_kernel+0x14d/0x170



&&

[  228.159116]  [<ffffffffadcf06bc>] acpi_ps_parse_loop+0x52d/0x5a3
[  228.159117]  [<ffffffffadcf9107>] ? acpi_ut_create_generic_state+0x39/0x44
[  228.159118]  [<ffffffffadcf11fa>] acpi_ps_parse_aml+0x98/0x26f
[  228.159118]  [<ffffffffadcf1a59>] acpi_ps_execute_method+0x14d/0x184
[  228.159119]  [<ffffffffadcebe2a>] acpi_ns_evaluate+0x1c6/0x252
[  228.159119]  [<ffffffffadcdf078>] acpi_ev_asynch_execute_gpe_method+0xa0/0x105
[  228.159120]  [<ffffffffadcc7fc6>] acpi_os_execute_deferred+0x14/0x20
[  228.159120]  [<ffffffffad89d61c>] process_one_work+0x1fc/0x4b0
[  228.159121]  [<ffffffffad89d91b>] worker_thread+0x4b/0x500
[  228.159121]  [<ffffffffad89d8d0>] ? process_one_work+0x4b0/0x4b0
[  228.159122]  [<ffffffffad89d8d0>] ? process_one_work+0x4b0/0x4b0
[  228.159122]  [<ffffffffad8a3c18>] kthread+0xd8/0xf0
[  228.159123]  [<ffffffffae09f29f>] ret_from_fork+0x1f/0x40
[  228.159124]  [<ffffffffad8a3b40>] ? kthread_create_on_node+0x1e0/0x1e0


&&&


[  228.610701]  [<ffffffffadf1d272>] cpuidle_enter_state+0xf2/0x2c0
[  228.610702]  [<ffffffffadf1d477>] cpuidle_enter+0x17/0x20
[  228.610702]  [<ffffffffad8c791a>] call_cpuidle+0x2a/0x50
[  228.610702]  [<ffffffffad8c7d00>] cpu_startup_entry+0x2a0/0x350
[  228.610703]  [<ffffffffae0919e7>] rest_init+0x77/0x80
[  228.610703]  [<ffffffffae781fd3>] start_kernel+0x448/0x469
[  228.610704]  [<ffffffffae781120>] ? early_idt_handler_array+0x120/0x120
[  228.610704]  [<ffffffffae7812ca>] x86_64_start_reservations+0x24/0x26
[  228.610705]  [<ffffffffae781419>] x86_64_start_kernel+0x14d/0x170






```

---

### Post by Disposition96 on 2016-11-26
Bump

---

### Post by Disposition96 on 2016-11-27
Bump

---

### Post by Disposition96 on 2016-11-30
Bump

---

### Post by Disposition96 on 2016-12-07
Bump

I've tried disabling the usb charging, double checked to make sure all the fans are operating properly, I did the scans a few replies before.

I don't know how to disable things individually like the ethernet port and the wifi, the dedicated video card to try an isolate the issue any further however.

---

### Post by Disposition96 on 2016-12-09
Bump

---

### Post by l3v2 on 2016-12-11
hi, just stumbled over your thread here. could you provide more info on the laptop? does ist have an old bios or already uefi enabled? what windows version are you using on it, besides ubuntu?  and which ubuntu version did you try? did you install ubuntu or was it a live distro on a usb stick / dvd.  I'm not entirely sure the problems on both operating systems are linked. could you maybe show us a screenshot from windows with the taskmanager open and all processes from all users shown, sorted by cpu load? just for comparison. i've had several cases where the bloody .net framework under windows got stuck during its "optimization" stage or, this year, when win7 got the major update in july and something went wrong. it tried to install some tiny part of it over and over, causing 50% cpu load for nothing...  also, if your laptop (it is a laptop, right?) is overheating, just as a sloppy workaround, try another power setting. in windows its in the control panel somewhere. in ubuntu with unity, theres a similar option. as i'm on xubuntu, i have to set the cpu governor manually. this will slow down your machine, but it won't overheat or do an emergency shutdown.  as far as i understand it from your logs - and i'm a newbie - it's an acpi thing. i would try the bios and check what settings can be configured in regards to acpi and standby

---

### Post by Disposition96 on 2016-12-12
It is an older bios, very very limited things you can change.
I completely removed windows as an operating system.
I am running Ubuntu 16.10, direct install from DvD.
I will check to see if ACPI can be modified.

Edit:  Nothing in the bios on ACPI, I tried disabling hyper threading to see if that was the issue, no change.

---

### Post by l3v2 on 2016-12-13
what manufacturer / model is it? which bios version is running on it? htop showed 6 or 8 cores...? fully fledged i7?

just for kicks, what happens if you kill this ominous k-worker process? does it reappear immediately?
btw, i was asking about the laptop model, just to check if there was a bios update available. sometimes this might help, if you know what you're doing that is.

to make sure, that this is not an issue which is limited to ubuntu 16.10, you would need to test several live distros from usb. personally, i would try debian 8, an older ubuntu, maybe ubuntu 15.04 (also a different flavor) or something, and fedora 22 onwards, as this one is quite different from debian / ubuntu.
also, for your version of ubuntu, what happens if you temporarily disable ACPI in Grub (parameter for grub: acpi=off)? if it's really acpi, this should lower the cpu usage to about 1% total, but it would also prevent your cpu from lowering it's clocks, i.e. consuming more juice.



what this guy does in the already mentioned guide ([http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)) is aparently disapling this specific acpi interrupt 13 (again, i'm a noob :D)

further down in this thread someone posted, that he resolved this issue by installing a kernel module called "**phc-intel**". since you told me that your laptop is about 5 years old, this would roughly fit the description of the PHC package i've found for Arch Linux (found here: [https://wiki.archlinux.org/index.php/PHC](https://wiki.archlinux.org/index.php/PHC)). it's aparently specifically for the first and second intel i-generation (or older core 2 cpus). on newer cpus this does not work anymore 

as far as i understand it, the pch-intel module is a replacement for the  acpi-cpufreq module, which in turn is responsible for the cpu clocks.  did you by any chance find any performance hickups / slowdowns or simply  unusual cpu clock settings? it may well be, that your system is not  properly able to scale the cpu frequency under ubuntu 16.10 (from  minimum to normal and up to boost frequency). additionally that package  also allows you to undervolt your cpu in case you should need it. but  it's a bit tricky. i found this guide (german) for debian ([https://debianforum.de/forum/viewtopic.php?f=33&t=154693](https://debianforum.de/forum/viewtopic.php?f=33&t=154693))

in the second post ([http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu](http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu)) a guy tried the backtrace thing. your log seems to point into the acpi direction as far as i can tell, but your log does not show any other specific component, compared to this guys post.
also, further down in this thread, someone says, it could also be that one of his partitions was simply full. freeing some space helped him (aparently on XFS). Another one had the issue with an nfs share. can you make sure, none of these cases apply to you?



other than that, i'm at a loss :(

---

### Post by Disposition96 on 2016-12-13
Model : Samsung NP700Z5C ; I have never updated the bios.

Yes, when I kill the k-worker it immediately comes back.

I know it's not just Ubuntu, I had the same core operating at 100% on windows.  I changed to Ubuntu as I thought maybe it was windows and I got fed up as I couldn't figure it out... Which leads me to believe it's some type of hardware failure.


If I load up the computer, hit esc and change my boot parameters and add acpi=off I can't even get to the login screen, it pops up bbswitch: No discrete VGA device found.

I'm not going to do anything until I get responses on what I Should do from this stuff, the PHC, I could try but I do have a ton of space on my SSD still, I also had this issue on my other OS prior to deleting it so I feel there's a different underlying problem.

---

### Post by l3v2 on 2016-12-14
ok, i've dug some more using your input. (still, which sub-model is it? NP700Z5C is just the laptop "family".) 

let's take it from the top. i guess the problem was not present when you first got the laptop.  since you said, you're using a ssd, i have to assume that you installed it by yourself and reinstalled windows on it and some time around that the problem started. is that correct?

intel rapid storage driver; aparently across different hardware setups. [http://superuser.com/questions/851726/why-is-the-cpu-frequency-always-very-high-on-my-system](http://superuser.com/questions/851726/why-is-the-cpu-frequency-always-very-high-on-my-system)
this one has similar issues (intel rapid storage driver issue) [http://forum.notebookreview.com/threads/samsung-series-7-chronos-one-core-is-stuck-at-100-np700z5c-s02ub.718554/](http://forum.notebookreview.com/threads/samsung-series-7-chronos-one-core-is-stuck-at-100-np700z5c-s02ub.718554/)
same poster, other hint (take out ssd, boot from live distro) [http://superuser.com/questions/594473/one-cpu-core-stuck-at-100-doing-kernel-stuff](http://superuser.com/questions/594473/one-cpu-core-stuck-at-100-doing-kernel-stuff)

did you try this alredy? don't know if this applies to linux as well, but worth a try (bluetooth driver issue, windows fastboot)? [http://www.tomshardware.co.uk/answers/id-2284730/system-interrupts-taking-idle-cpu-processing-power.html](http://www.tomshardware.co.uk/answers/id-2284730/system-interrupts-taking-idle-cpu-processing-power.html)

so from what i've read, it really is possible to have this kind of problem across different OSs. so, aparently you're right. it somehow boils down to driver issues related to acpi / intel rapid storage and MAYBE an old bios version. this is a weird issue i've never encoutered before.

---

### Post by Disposition96 on 2016-12-14
NP700Z5C-S04CA is the entire model number, I do apologize for that.
 
 
 The problem most definitely did not start when I got the laptop, I swapped out the SSD the day I got it, everything was perfectly fine up until when I posted, I noticed the laptop was getting absolutely crazy hot.
 
 
 One thing I did do was I left my power adapter behind so I had to go buy a cheap one from Best Buy to use for about two weeks, everything was fine then aswell but when I recieved my power bar a few days after that I noticed that it was stuttering and that&#8217;s when I started to do my analasys of everything, I couldn&#8217;t fix it in windows even on a fresh install so I decided to try and use linux and still didn&#8217;t work lol!
 
 
 ```
intel rapid storage driver; aparently across different hardware setups. [http://superuser.com/questions/85172...h-on-my-system]("http://superuser.com/questions/85172...h-on-my-system%5B/code") 
```
 
 
 This one that you sent me is about the video card not the storage driver haha.  it links to a intel driver problem.  The motherboard/cpu does have an integrated HD4200, I don&#8217;t see that anywhere listed on my Ubuntu information, could that be the culprit?
 
 
 ```
this one has similar issues (intel rapid storage driver issue) [http://forum.notebookreview.com/thre...-s02ub.718554/]("http://forum.notebookreview.com/thre...-s02ub.718554/%5B/code") 
```
 
 
How do you install this on ubuntu?
 
 
 ```
ame poster, other hint (take out ssd, boot from live distro) [http://superuser.com/questions/59447...g-kernel-stuff]("http://superuser.com/questions/59447...g-kernel-stuff%5B/code") 

```
I suppose removing the SSD will really show if that&#8217;s the issue or not...

---

### Post by l3v2 on 2016-12-15
ok, so the NP700Z5C-S04 (CA or otherwise) has a intel 3xxx cpu, so PHC is out of the question. also it has a discrete nvidia gt640m.

i know that this was mainly about the integrated gpu. [http://superuser.com/questions/851726/why-is-the-cpu-frequency-always-very-high-on-my-system](http://superuser.com/questions/851726/why-is-the-cpu-frequency-always-very-high-on-my-system)

BUT the last poster said something about the intel RST driver, again this laptop family (older model) in combination with a ssd (power management / ACPI + bad SATA / AHCI driver). that's why i included it. the integrated gpu might well be the culprit as well. you have to excuse my aproach. i'm shooting blindly here. just trying to rule out some issues and narrow it down. also, the gpu issue of the original poster was on a desktop system, which was showing similar problems. additionally his cpu refused to clock down, which it should do automatically. guess this is also the case on your machine. (but that's just because of the "workload", so it's just a symptom)

i'm not sure if i got it correctly. you replaced the hdd with the ssd, when the laptop was brand new. then after a while you replaced the power supply, which was workng fine, no symptoms shown. then you mention a power bar. do you mean a power bank / external battery or just the replacement power supply (another one?? :confused:)? 

cheap power supplies can cause problems at times, yes, but if they do, they usually do it with a bang and some fireworks, i.e. your machine would turn into an expensive paper weight. 
as long as it has the same polarity and wattage it sould do its job under normal circumstances - unless it can't sustain heavy workloads over an extendend period of time, in which case it would go bang. as it aparently did not, i'd say you're safe.

now back to the cpu / integrated gpu. if the driver is not working properly, it can cause the same symptoms as on that other guy's desktop. i.e. the i-gpu is not switched off, maybe the driver permanently tries to do so and causes the workload on one core. oddly enough, the thread does not get passed to other cores as it would usually do (i mean jumping across all cores), but i guess this is due to the inner workings of the kernel.
since your rig has hybrid graphics, did you install the proprietary drivers for the gt640m? if so, did you also install nvidia-prime? that's supposed to let you switch between the gpus while running the os. i'm not sure if you also need proprietary intel drivers. i think it's supposed to work with generic intel drivers.
quick info here: [http://askubuntu.com/questions/661922/how-am-i-supposed-to-use-nvidia-prime](http://askubuntu.com/questions/661922/how-am-i-supposed-to-use-nvidia-prime)
with ```
lspci -v | grep "VGA controller"
``` or simply ```
lspci -v
``` you should get a list of hardware. look for "VGA Controller" in brackets at the end of the line. that should show both gpus and point you to the active one. 
usually there's also a setting in the bios, where you can set / force the active gpu. could you check that maybe? what happens if you force it to use one, e.g. the integrated gpu, and boot into ubuntu (and on a second run, the other, discrete gpu)? is the k-worker still going nuts?


if it's the AHCI driver, the quickest and easiest way would be to take out the ssd for a few minutes and boot the rig via usb stick.
under windows, older intel chipsets might be bitchy, when they have to run with the generic microsoft AHCI driver. also the disks will show increased power consumption, because the generic driver is not using all acpi features. That's why most people install the intel RTS driver, even if they don't intend to use RAID. and as you might have read in these posts, it could mitigate cpu load hickups.
i honestly don't know how the linux ahci driver behaves in this case. usually it works well enough out of the box as it's integrated into the kernel. i know that some linux version of the intel RST driver exists, or that's at least what intel says on their website. other than that, no idea yet.


edit: most promising suggestions so far, including those from the first page of the thread

1. disable peripherials in bios and check for k-worker activity in ubuntu

[LIST]
[*]wifi 
[*]LAN 
[*]bluetooth 
[*]e-sata? / firewire? other crap 
[/LIST]

2. disable kernel modules as described (last resort imho)
3. check bios for GPU settings and check k-worker after each change
4. check drivers

[LIST]
[*]ahci, intel RST (unplug ssd for testing) 
[*]i-gpu intel 
[*]gpu nvidia gt640m 
[/LIST]

5. try a completely different distro (not too promising by now)

---

