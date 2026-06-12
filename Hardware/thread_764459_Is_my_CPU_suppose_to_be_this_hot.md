---
title: "Is my CPU suppose to be this hot"
date: 2008-04-23
forum: Hardware
---

### Post by InsertNameHere on 2008-04-23
Hi,
I have a Toshiba Satellite A100, I was wondering if my CPU tempature is normal, the CPU is Core 2 Duo T5500.

I use Core Temp on Vista (waiting for hardy) I heard the safe limits is 30-60 C, but mine is reaching 70s-90s just by listening to music on WMP and sufing the net.

I have this leathery table that I use this laptop on, the laptop has legs that are suppose to lift it from the table, because there's a cooling vent under it (I think) but as with the table I'm using, the vent is completely blocked. There's another vent on the right side of the laptop.

Some hours after operation (vista) I can feel it getting extremely hot, under the laptop.

Can someone tell me if this is normal??

(useually, with the leathery table, it's 80 degrees, but if I lift it with my hand for 20 mins I can reduce it to 60-65, but 60's is still pretty high from what I've read.

---

### Post by overdrank on 2008-04-23
HI and I have found it is a great investment for a laptop cooler. They are about 20 bucks and keeps the laptop cool :cool:

---

### Post by gunashekar on 2008-04-23
I don't have a Toshiba but my HP/compaq was heating up too. I upgraded the bios and that solved the problem. your manufacturer's website would most likely have the latest bios.

---

### Post by Lord Xeb on 2008-04-23
You need to cool that sucker down!!! 70C is a a really good stopping point. But 90C!!! 100C is the boiling point of water. A processor should NEVER get that hot. So yes, do what gun said and also, take a book an set it your laptop up on it as so that is at an angel. This will provide airflow under the laptop and cool it. Also try to find a tutorial on how to clean your laptops heat sink. That could be another reason why it is getting so hot.

---

### Post by snipedu1st on 2008-04-24
Is it the OS that is making the laptop hot?  My laptop has been running XP Pro for 3 years.  It never ran this hot.  I just installed Ubuntu yesterday and it keeps rebooting because it's exceeding 83c?  Why would Ubuntu make my laptop get this hot?

---

### Post by InsertNameHere on 2008-04-24
This is on Vista.
I'll download Ubuntu 8.04 today and install conky and see how it goes.
I'll take a book and set it at an angle and see how it goes today.

I brought this thing a year ago, it shouldn't be dirty (yet), I take good care of it.

When windows boots up it reports 50 degrees (47-51).

Also my BIOS is latest from Toshiba.

Edit : With a book and an angle, under the same circumstances (WMP and surfing the net) it's around 60 C (59-63)ish. Is that normal?

---

### Post by hessiess on 2008-04-24
clean the cpu heatsink, and run 'top' in the terminal to see what aplications are running. are the fan(s) working?

---

### Post by InsertNameHere on 2008-04-24
I'm currently not running ubuntu (still downloading hardy)
I'm running vista (I know it sucks)

I'm starting to wonder if Vista had anything to do with it, anyways, I'll probably install Hardy tonight and see what it says.

Erm. also when I turn on a visualization called G-Force in WMP, it skyrockets to 80-85 C.

---

### Post by dicecca112 on 2008-04-24
it doesn't have anythign to do with vista.  Your laptop is not venting well, either due to dust clogging the intakes, or it not being on a surface that allows proper venting.  Does you fan run when these temps are reported?  How are you getting these temps in Windows?

---

### Post by InsertNameHere on 2008-04-24
I can hear the fans run, and I'm using coretemp.
The fans are running, I can hear the noise.
Also it didn't use to be this hot in XP

Also, the more programs I ran the higher the tempature gets, the reaction is almost immediate.

---

### Post by 1440 on 2008-04-24
> **InsertNameHere said:**
> This is on Vista.
Edit : With a book and an angle, under the same circumstances (WMP and surfing the net) it's around 60 C (59-63)ish. Is that normal?
These are normal temperatures for a CPU. My temps are around 60C too.

---

### Post by InsertNameHere on 2008-04-24
Are you sure? because I heard 30-60 is normal.

---

### Post by thebigham on 2008-04-24
What program can i use to display the temperatures on ubuntu for dell laptpos?

On vista, my latop goes over 70C on startup, it cools down to around 50s-60s after a minute or two.

---

### Post by InsertNameHere on 2008-04-24
I used Conky to display that stuff on ubuntu.
Core temp on vista.

---

### Post by wastedfluid on 2008-04-24
Here's some info for you(hope this helps)

os[Linux 2.6.24-16-generic i686] distro[Debian lenny/sid] cpu[2 x AMD Turion(tm) 64 X2 Mobile Technology TL-50 (AuthenticAMD) @ 800MHz] mem[Physical: 882.7MB, 75.9% free] disk[Total: 90.8GB, 68.8% free] video[ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]] sound[HDA-Intel - HDA ATI SB]

top - 20:34:02 up  1:12,  2 users,  load average: 0.43, 0.57, 0.54
Tasks: 117 total,   1 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.2%us,  2.6%sy,  0.5%ni, 80.2%id,  3.9%wa,  0.3%hi,  0.4%si,  0.0%st
Mem:    903892k total,   891780k used,    12112k free,    24088k buffers
Swap:  1052216k total,       16k used,  1052200k free,   534208k cached

fluid@wasted:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +50.0°C                                    
Core1 Temp:  +43.0°C                                    

fluid@wasted:~$ 


This is @ 800mhz.. with xchat, pigdin, evolution, Transmission(helping out for the torrent people out there), banshee playing music.. and browsing.  I do have the Notebook Coolre ZM-NC1000.. so it's kind of cheating, though.  Keeps it 4-6f cooler all the time.

---

### Post by wastedfluid on 2008-04-24
> **thebigham said:**
> What program can i use to display the temperatures on ubuntu for dell laptpos?

On vista, my latop goes over 70C on startup, it cools down to around 50s-60s after a minute or two.

A simple way is "sudo apt-get install lm-sensors" - and then just type "sensors" in any terminal, and it'll output like:

```

fluid@wasted:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +50.0°C                                    
Core1 Temp:  +43.0°C                                    

fluid@wasted:~$ 

```

---

### Post by MikeRussell on 2008-04-25
I think the surface might be playing a big role in your issue.  My core2duo laptop generally idles around 40-50C on a glass table.  I have noticed when I move it to a leather couch for surfing the web that it jumps about 10-15 degrees, and I can only assume it is because it doesn't vent as well.  You can also use a program (i8kutils) to monitor temps and tell your fans when to kick in.  This helped on my GFs Inspiron 1501 which seemed to run unusually hot.

---

### Post by cafg10 on 2008-04-25
Everyone with a Core 2 CPU which goes any higher than 50 C should be warned, according to Intel.

The 50 C is the top temperature that those chips can support safely without suffering thermal harm, any hotter than that steadly decreases your processor life spectatives.

However, thats mostly for the desktop chips like the E6600 or the E6750, also it might be different for the E8X00 processors.

If your laptop is a little older, you should take it to replace the thermal compound between the chip and the heatsink, also you should check for all your fans working and looking into BIOS for fan control.

Myself, I have some experience with AMD processors temperature, which tolerate a little higher temperature (60 C Windsor vs 50 C Conroe) than the Intel ones, but because they are different, it is not that one is better than the other in thermal efficiency.

---

### Post by InsertNameHere on 2008-04-25
it's not too old 
my BIOS is a Toshiba BIOS and its completely useless (no useful settings)

Also isn't the safe limits 100C?

Also I tried installing sensors but this came up

Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
I ran sensors-detect as root, and said yes to everything, still shows that message

Nevermind, I rebooted and works.

---

### Post by dicecca112 on 2008-04-26
> **cafg10 said:**
> Everyone with a Core 2 CPU which goes any higher than 50 C should be warned, according to Intel.

The 50 C is the top temperature that those chips can support safely without suffering thermal harm, any hotter than that steadly decreases your processor life spectatives.

However, thats mostly for the desktop chips like the E6600 or the E6750, also it might be different for the E8X00 processors.

If your laptop is a little older, you should take it to replace the thermal compound between the chip and the heatsink, also you should check for all your fans working and looking into BIOS for fan control.

Myself, I have some experience with AMD processors temperature, which tolerate a little higher temperature (60 C Windsor vs 50 C Conroe) than the Intel ones, but because they are different, it is not that one is better than the other in thermal efficiency.

You have proof of this.  I have always read from Intel it was 60-70c was fine for load, 80C was too high.

---

### Post by urutoraman on 2008-04-26
Reports of overheating, high CPU usage and cpu fan blowing all the time are starting to come out.... So it seems that Hardy Heron was not ready for prime time after all.

I used to have Gutsy with wireless, Nvidia restricted and FULL Compiz effects and cube without any temperature issue.

It is not a BIOS problem.
It is not a dirty fan or heat sink problem.

It is damn Hardy!!!

If not then you experts, EXPLAIN why it does not happen with Gutsy.
With Hardy my Pentium 4 doesn't comes down from 67C.  My laptop is dual boot.  With XP it runs under 40C.

Accept it Hardy Heron is flawed, Canonical needs to do something to fix this... or people will always says "You get what you pay for.." when their machines and CPU get fried.

---

### Post by Yellow Pasque on 2008-04-26
urutoraman, perhaps there is a problem with Hardy's interface to lm-sensors.
Do you have the CPU speed monitoring applet somewhere in one of your panels? Do you have Speedstep working? Is something constantly loading your processor? (look at usage with System -> Administration -> System Monitor)

---

### Post by Charlie708 on 2008-04-26
> **cafg10 said:**
> Everyone with a Core 2 CPU which goes any higher than 50 C should be warned, according to Intel.

The 50 C is the top temperature that those chips can support safely without suffering thermal harm, any hotter than that steadly decreases your processor life spectatives.

However, thats mostly for the desktop chips like the E6600 or the E6750, also it might be different for the E8X00 processors.

If your laptop is a little older, you should take it to replace the thermal compound between the chip and the heatsink, also you should check for all your fans working and looking into BIOS for fan control.

Myself, I have some experience with AMD processors temperature, which tolerate a little higher temperature (60 C Windsor vs 50 C Conroe) than the Intel ones, but because they are different, it is not that one is better than the other in thermal efficiency.

Intel rates the C2D and C2Q up to 68C; Xeon based Conroe and Kentfield chips are rated up to 85C.

Does Hardy not use deep power states?  The added heat also means a big chunk out of battery life too.

---

### Post by dicecca112 on 2008-04-26
> **urutoraman said:**
> Reports of overheating, high CPU usage and cpu fan blowing all the time are starting to come out.... So it seems that Hardy Heron was not ready for prime time after all.

I used to have Gutsy with wireless, Nvidia restricted and FULL Compiz effects and cube without any temperature issue.

It is not a BIOS problem.
It is not a dirty fan or heat sink problem.

It is damn Hardy!!!

If not then you experts, EXPLAIN why it does not happen with Gutsy.
With Hardy my Pentium 4 doesn't comes down from 67C.  My laptop is dual boot.  With XP it runs under 40C.

Accept it Hardy Heron is flawed, Canonical needs to do something to fix this... or people will always says "You get what you pay for.." when their machines and CPU get fried.

Please keep your spam out of this thread.  How does this help the user?

---

### Post by dicecca112 on 2008-04-26
> **Charlie708 said:**
> Intel rates the C2D and C2Q up to 68C; Xeon based Conroe and Kentfield chips are rated up to 85C.

Does Hardy not use deep power states?  The added heat also means a big chunk out of battery life too.


Good idea.  OP install Powertop, and see if you can get your processor down to its lowest states.

---

### Post by urutoraman on 2008-04-26
> **dicecca112 said:**
> Please keep your spam out of this thread.  How does this help the user?

Help is to stay away from Hardy and go back to Gutsy, while the issue is being fixed.

It is really frustrating, to try every fix posted and keep getting the hot air out of the vents of your computer.  It is not fun to let user try fixes with the risk of burning out the CPU/GPU or any other component.  If you don't find this a serious issue then you are welcome to experiment.

I have tried the following already without any single step down on CPU temperature:

powertop
powernowd
Adding acpi_osi=Linux and acpi_apic_instance=2 to /boot/grub/menu.lst

I have the CPU temperature applet sitting on a panel, showing temperatures going up instead of down when I use the computer and lot of hot air coming out from the vents.  The synaptic touchpad is not usable because is really hot to the touch. I can hear the fans blowing from 2 rooms away where the computer is.

The CPU is a Pentium 4 with HT, older than a C2D.  Reports of overheating spotted in this forum are coming from users with different CPUs: AMD, C2D, P4, etc.  There is something almost common, the majority of the reports are coming from laptop users including myself.

---

### Post by pt_lam on 2008-04-27
I'm a Toshiba A100 user too.
It runs well with Windows XP, but when it runs ubuntu it's much hotter, at least I can feel the heat from my laptop's case.
Still the same after upgrading to Hardy.

---

### Post by Medo42 on 2008-04-27
I'm using an A100 as well, and my top temperatures have been around 85°C. It only happened after running with full load for some time when it was also quite hot outside, but I figured that was unhealthy. Now I've undervolted my processor, and it hardly gets warmer than 65°C, and under full load I'm saving around 12 Watts.

Edit: Maybe I should add that this is in general, the high temeratures were NOT specific to Hardy or even Linux.

---

### Post by hidinginthemountains on 2008-04-27
I'm also on a Toshiba A100. I've runn Gutsy since October and saw my temps usually 50-55. I hadn't even been running a monitor since installing Hardy, so I just took a look, and...

...no difference. My laptop has been running non-stop for 10 hours as I type this. I don't have Vista installed anymore, so I can't tell you what temp it is under MS, but I can't see any reason it would be lower.

I can only suggest what others have said already. Use your laptop on a hard surface, use a cooler (I'm not, but sounds like you could use it), and clean the heat sink (sometimes they clog up awful quick). Gook luck!

(and yea, the BIOS on these things has NO useful settings)

---

### Post by dicecca112 on 2008-04-27
> **urutoraman said:**
> Help is to stay away from Hardy and go back to Gutsy, while the issue is being fixed.

It is really frustrating, to try every fix posted and keep getting the hot air out of the vents of your computer.  It is not fun to let user try fixes with the risk of burning out the CPU/GPU or any other component.  If you don't find this a serious issue then you are welcome to experiment.

I have tried the following already without any single step down on CPU temperature:

powertop
powernowd
Adding acpi_osi=Linux and acpi_apic_instance=2 to /boot/grub/menu.lst

I have the CPU temperature applet sitting on a panel, showing temperatures going up instead of down when I use the computer and lot of hot air coming out from the vents.  The synaptic touchpad is not usable because is really hot to the touch. I can hear the fans blowing from 2 rooms away where the computer is.

The CPU is a Pentium 4 with HT, older than a C2D.  Reports of overheating spotted in this forum are coming from users with different CPUs: AMD, C2D, P4, etc.  There is something almost common, the majority of the reports are coming from laptop users including myself.

Hmm that's odd because I have been using it since the Alpha's and no issues, so have most of my friends, whose laptops run the gambit from an old P4-M, to newer C2Ds like mine.  None have the issue.  

You gotta remember that this is use at your own risk software, its free.  So if you don't like it go to another distro.  And have you filed a bug yet? I doubt it.  You just want to spam the users.

---

### Post by Muflon on 2008-04-27
I don't know if this is the same problem that I have been having with my laptop and Hardy.

[http://ubuntuforums.org/showthread.php?t=739892](http://ubuntuforums.org/showthread.php?t=739892)

My problem is due to the fan going off and staying off.  I have raised this as a bug.

[https://bugs.launchpad.net/ubuntu/+bug/211980](https://bugs.launchpad.net/ubuntu/+bug/211980)

If your problem is the same as mine, can you please update the bug report and add your details.

Muflon

---

### Post by napolperro on 2008-04-27
Well since I moved to Ubuntu (some 3 or 4 months ago) I did notice a subtle increase in temperature on my laptop (dell inspiron 6400). When under load it would hit ~65° but almost always idles at around 45 C... in XP the idle temp is about 40, so maybe the little difference is because of the compiz effects or something like that, not really that severe.

I think a good solution would be finding another work surface, as it has been said before, you know leather can get pretty hot :)

Edit: I also opened it about 2 months ago and cleaned all the dust with compressed air, maybe that could help you (if you do it carefully and also if your warranty has expired, which was my case... try looking for some guides on opening your specific model, or maybe kjust take it to a technician who knows what he is doing :P)

---

### Post by InsertNameHere on 2008-04-27
I just installed Hardy on Friday, it works pretty well (and FAST might I add), I see no difference between hardy and MS (used hardy for 4 hrs stright).

I'm not sure about this but alot of people suggested that the tempature is normal if I put it on a hard surface.

A person above posted that Hardy has problems, so I wont boot it until something is said about it (eirther it doesn't exist or fixed).

I could never hear my fans running clearly, eirther it's always on or never on.

---

### Post by daimaru on 2008-04-27
I just posted a thread to fix the nvidia gpu on toshiba p100's not sure if this also helps with your A100 model. but you could give it a try. 


[http://ubuntuforums.org/showthread.php?t=771223](http://ubuntuforums.org/showthread.php?t=771223)

---

### Post by DublinPCservices on 2008-04-27
> **InsertNameHere said:**
> Hi,
I have a Toshiba Satellite A100, I was wondering if my CPU tempature is normal, the CPU is Core 2 Duo T5500.

I use Core Temp on Vista (waiting for hardy) I heard the safe limits is 30-60 C, but mine is reaching 70s-90s just by listening to music on WMP and sufing the net.

I have this leathery table that I use this laptop on, the laptop has legs that are suppose to lift it from the table, because there's a cooling vent under it (I think) but as with the table I'm using, the vent is completely blocked. There's another vent on the right side of the laptop.

Some hours after operation (vista) I can feel it getting extremely hot, under the laptop.

Can someone tell me if this is normal??

(useually, with the leathery table, it's 80 degrees, but if I lift it with my hand for 20 mins I can reduce it to 60-65, but 60's is still pretty high from what I've read.

That laptop is running too hot.
Split the case, make sure the fan is clear of fluff,
remove, clean, and repaste the CPU and cooler.

---

### Post by urutoraman on 2008-04-28
> **dicecca112 said:**
> Hmm that's odd because I have been using it since the Alpha's and no issues, so have most of my friends, whose laptops run the gambit from an old P4-M, to newer C2Ds like mine.  None have the issue.  

You gotta remember that this is use at your own risk software, its free.  So if you don't like it go to another distro.  And have you filed a bug yet? I doubt it.  You just want to spam the users.

I wasn't sure if it was a bug or not, but after long hours of struggling I finally found the solution posted on this web site:

[http://howtoforge.com/cpu_frequency_scaling_ubuntu]("http://howtoforge.com/cpu_frequency_scaling_ubuntu")

The CPU frequency scaling module wasn't enabled by the installation script for some reason. What a pain, I guess that for other processors it is doing the same.  After I enabled it, temperature went down from 68C to 55C and the fan stopped running.  55C still higher than Windows XP 40C but, I am a happy camper now. :guitar:

---

### Post by urutoraman on 2008-05-01
**[COLOR="Red"]Claim victory too soon.[/COLOR]**

After a reboot it didn't work, and the sudo modprobe p4_clockmod , p4_clockmod, command is showing "command not found" now.

Worst thing is the laptop is shutting down abruptly.

Went back to a different flavor of Gutsy distro. 

This time Linux Mint 4,  now the computer is working perfectly, no overheat, no crashes.  Good Bye Hardy Heron, will wait for the next Ubuntu version (8.10??).

:mad:

---

### Post by emsed1 on 2008-05-02
HP notebook with Hardy Heron x1 week.

Core 2 Duo 2.2Ghz

Under Vista power management and cpu scaling work fine.  After trying hardy 64-bit, 32-bit and Kubuntu 8.04 32 bit I can't find a way to scale the core 2 cpu.  I have tried every utility (powersave(d), cpufreq(d), powertop, etc etc.)

The CPUs run from a low of 59C to 75C and the thing blows hot air no matter what I do... I can't even GET the cpu that hot with vista.

I compiled my own kernel, etc. blah blah... searched every forum for a week, added modules... no help.

I just want to turn my CPU speed down because it is literally burning my hands and lap.. (before you start, the thing has an extended 12-cell battery that props the back end up about an inch and there is plenty of air flow and the fan is not blocked by lint, etc etc.)

I am at my wit's end and this thing is whipping me.  I don't WANT to use Vista.  64-bit Hardy absolutely SCREAMED on this thing but a lot of i386 apps won't install.  32-bit isn't bad but I don't need a space heater.

HP dv2700t
Core 2 Duo 2.2Ghz
3 GB RAM

Any thoughts?  Not wanting to sound cynical but a LOT of folks have this problem and I havent' found any answers.

Thanks!

---

### Post by cgrenier on 2008-05-03
This is not just a laptop problem.  My AMD64 x2 3800+, a bit old but reliable, having run earlier Ubuntus and Vista without a problem for over two years, overheats with Hardy... every single time.  It gets to over 90C and then shuts down.  I don't know how to enable CPU scaling, but it needs to happen.

---

### Post by Yellow Pasque on 2008-05-04
You need to lower the shutdown temperature in the BIOS unless you want to risk burning out the CPU.

You also need to reseat the CPU and make sure your case is getting good airflow.

---

### Post by conceptrat on 2008-06-18
Other problem could be processes like tracker or beagle going flat out indexing everything in your home directory.  I noticed this a while ago with I think 6.04.

Just a thought as well as the cpu scaling option.

Cheers
Julz

---

