---
title: "PLEASE PLEASE help before I loose another MB."
date: 2009-06-13
forum: Hardware
---

### Post by sdd on 2009-06-13
Can we just agree that there IS an issue with Fan control and overheating in Ubuntu 9.04 and just get it sorted. 

I do not want to have to replace my Mother Board again. This is basic stuff, 8.10 could do it, XP and Vista can do it, Windows 7 will no doubt do it too. 9.04 does not do it, how can this be.

I love the idea behind Ubuntu and have supported it for years but things like this can do real damage to it's credibility.

I have a HP Pavillion dv9000 that has had Ubuntu on it (dual boot with Vista) for about 24 months. I always keep up to date so put 9.04 on it when it came out. Two weeks ago the MB failed. The GeForce go 7600 packed in. It had been running hot for a while but I had not taken much notice. 

So I now have a new MB, new BIOS, new Fan. Running Vista the fan ramps up when things get hot, slows down when the heat disipates. When I run Ubuntu 9.04 the BIOS speeds the fan up during POST and then it goes quiet. It is not OFF is is just quiet. Ubuntu starts and the fan stays quiet ALL the time. Nothing I do causes it to speed up.

Knowing this was a heat issue I installed lmsensors and the CPU Scaling applet set to On Demand. Both CPU's run at 1gig until I start somes apps and they scale up and down normally. 

The CPUs stay cool between 20c to 30c but the GPU (Thats GeePeeYou) just gets hotter and hotter. After a couple of minutes 60c, If I do any graphics intensive stuff it soon reaches 80c. THE FAN STAYS VERY QUIET.

I have tried lots of different fixes (from a quick Google) but nothing works.
I have raised a bug for this on Launchpad. I have seen loads of forum activity on this subject.
I have NEVER seen anyone say Yes it is an issue, we are fixing it.

My understanding is that this is a Kernel issue and I am certain that it is is a complex process to patch it. Do we know if anyone is looking at this.

One thing I am curious about is that the fan folder in ACPI is empty so I cannot set the speed. I CANNOT BUDGE THE FAN AT ALL. It is yery frustrating.

Can we get som expert advice here PLEASE.

SDD

---

### Post by 67GTA on 2009-06-13
Your problem might actually be Microsoft. Have a look here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051) I can help you fix your DSDT if that seems to be the problem. What is the output of these commands from a terminal?

```
cat /proc/acpi/thermal_zone/THRM/state
```
```
cat /proc/acpi/thermal_zone/THRM/trip_points

```
```
cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by sdd on 2009-06-14
Thanks for the prompt reply.

From :cat /proc/acpi/thermal_zone/THRM/state
No such file or directory
From :cat /proc/acpi/thermal_zone/THR1/state
state:                   ok

Form : cat /proc/acpi/thermal_zone/THR1/trip_points
critical (S5):           120 C
passive:                 92 C: tc1=2 tc2=3 tsp=50 devices=CPU0 CPU1 

From : cat /proc/acpi/thermal_zone/THR1/temperature
temperature:             32 C

This agrees with lmsensors for the CPU. I agree that this is nice and cool. However it is my GPU that concers me, just typing this reply and the GPU is at 64 C. If I start other things it gets much hotter but he FAN never changes speed, not at all. It is this that is the issue for me.

The process should be, when it gets hot, the fan comes on, it cools down, fan turns off. No mattrer what I do the fan never responds.

Thanks

Stuart

---

### Post by gradinaruvasile on 2009-06-14
What driver version u use for the vid card?
I had exactly the reverse problem with Quadro NVS 135 card - in some Nvidia driver versions (i think the default 180 and the 185.14 from the site) the fan ran full throttle all the time. I now use the 180.60 driver downloaded from the nvidia site and all seems well.

Maybe this helps.

---

### Post by 67GTA on 2009-06-14
Follow the how to in the link I posted above to the point of getting your dsdt.dsl file and post it here. I will look to see if that is the culprit. If not, you will probably want to file a bug on launchpad. Also, is there anything in /proc/acpi/fan?

---

### Post by sdd on 2009-06-14
I forgot to mention that I had a look at the 'HOWTO Fix A Buggy DSDT File' and even disassembled the file. However when it came to fixing the bugs I do not have the knowledge. I found bugs listed but did not know what to do in order to fix them. I checked out the links but found no real answers.

This is not somthing a user should be getting involved with, why are there bugs in here in the first place. 

I also could not find a fixed one for my laptop, nearest was HP Pavilion dv9000t. Does this do for ALL dv9000. Mine is a dv9288ea. This is pretty scary stuff for even for an experienced user. 

Still my fan just idles mockingly :-{

Stuart

---

### Post by sdd on 2009-06-14
Opps, sorry our replies crossed. I will attach the file, give me 10 minutes

---

### Post by sdd on 2009-06-14
Here is the dsdt.dsl file (attached as dsdt.dsl.tar.gz).

There is nothing in /proc/acpi/fan it is empty.

Thanks

Stuart

---

### Post by sdd on 2009-06-14
gradinaruvasile thanks for responding.

These are my Nvidia details

NVIDIA Driver Version:180.44
Server Vendor Version:1.6.0 (10600000)
NV-Control Version:1.17

Graphics Processor:GeForce Go 7600
VBIOS Version:05.73.22.50.a3

Slowdown Threshold:110
Core Tempreture is currently 67 C

Hope this helps.

Stuart

---

### Post by 67GTA on 2009-06-14
The Intel compiler made 971 fixes to your dsdt on top of the 13 things I fixed manually. The Microsoft compiler had really broken yours. I didn't see any errors in the sections that controlled temps though. If we are lucky, one of the fixes made automatically will *inadvertently fix the temp trouble. There were a few fixes made in the proc area. You need to copy the file I posted to /etc/initramfs-tools and then copy paste the commands in my how to to finish. Be sure to add the acpi_osi="Linux" definition to /boot/grub/menu.lst. per the how to. *[ATTACH]117693[/ATTACH]

---

### Post by sdd on 2009-06-14
Thank you very much for this. It is not often I get this level of assistance for free.

I have read your 'final stages' from your thread on HOWTO Fix A Buggy DSDT File. I will need some time to do this.

One thing I do not see there is how to restore to the original if the new one does not work or breaks. I think it was the 'Now cross your fingers and reboot' comment that got me wondering. 

What does the command 

sudo update-initramfs -u -k kernel-version

change, is it the BIOS or just part of the Linux Kernal. I am not worried if re-installing Linux will get me going again but could I break Vista or end up with an un-usable PC, is this a possibility.

I have read your thread and seen the positive comments and I am very impressed. It is just that I have had such bad luck with these things in the past.

If I backup /etc/initramfs-tools/DSDT.aml do the changes, reboot with no major issues can I restore it and do update-initramfs on the old one. 

I feel so close, just need some words to spur me on.

Thanks

Stuart

---

### Post by Amilo1718 on 2009-06-14
> **sdd said:**
> could I break Vista or end up with an un-usable PC, is this a possibility.
you should break vista :D
& an un-usable pc is not an option (or the hardware is failing you)

\\:D/

---

### Post by 67GTA on 2009-06-14
There is nothing to really worry about if you just follow the how to. The update-initramfs command updates the kernel to include the DSDT.aml file we added. The kernel has built in support to use custom a DSDT, and looks in the /etc/initramfs-tools directory for it at boot. There is no need to back up anything. The worst case scenario is Ubuntu doesn't boot. It will not touch Windows in any way. To revert the changes, you can boot into recovery mode, delete the DSDT.aml file we added, and run the update-initramfs command again to get rid of the symbolic link. To do that: ```
sudo rm /etc/initramfs-tools/DSDT.aml
``` and then ```
sudo update-initramfs -u -k kernel-version
```

---

### Post by sdd on 2009-06-14
We all agree that Vista is already broken and there is a new Patch coming soon called Windows 7.

But I love my laptop and I don't want it to break. I have just had a new Mother Board and a BIOS upgrade so the hardware is good.

I just need to know the risks.

---

### Post by sdd on 2009-06-14
Thanks 67GTA that's all I needed to know. 

It has been a pleasure

I will let you know the result.

Thanks to all who have contributed to this thread.

Stuart

---

### Post by sdd on 2009-06-14
No problem installing and rebooting :D 

Saw the dmesg output :D

Need to see the impact over time (Have to go to sleep now) but I will give Quake4 a go tomorrow and see how she goes.

There is still nothing in /proc/acpi/fan.

Quake will give it a good testing and I will monitor the temperature.

Thanks once again

Stuart

---

### Post by sdd on 2009-06-14
FAN came to life when I started Quake so it is looking good.:popcorn:

Thank you for all your help

Just two questions - 

For the next release of Ubuntu can I use the same DSDT.aml. From your comments I assume that it is for my particular laptop and would apply to all Linux installs?

Do I need to configure the file again if my kernel is upgraded to a different version?

Kind regards

Stuart

---

### Post by 67GTA on 2009-06-14
You can use the DSDT.aml for any Linux distro. Keep a copy of it in a safe place for future use. It is for your PC only. The DSDT in your BIOS will always be broken. This is just an error free copy of it. You will have to reapply the DSDT.aml anytime you do a clean install because the /root filesystem will be wiped out. A kernel upgrade won't hurt anything because it will trigger the update-initramfs command again, and pick up the DSDT.aml. Send me a copy of ```
sudo dmesg
``` from a terminal, and I will see if everything looks okay.

---

### Post by sdd on 2009-06-19
Here is my dmesg output.

Once again thanks for all your help.

---

### Post by 67GTA on 2009-06-19
Looks good to me;)

---

### Post by wcutrombonekid on 2009-06-22
what a beast, i have no idea what just happened, but what a beast!

---

### Post by Maheriano on 2009-06-22
I had the same laptop, it's a pile of steaming dog crap. The thing had so many recalls that HP had it more than I did and one of them was for the fan on the motherboard. I used to have the email they sent out about it but deleted it, it basically said the BIOS version for the motherboard that comes installed on the computer is faulty and doesn't properly control the fan. Some fans are just spinning out of control and burning out causing the motherboard to overheat and die, others are not spinning enough and the motherboard is once again overheating and dying. So if you still have the old board that burnt out on you, return it under warranty. As for the new board, return that too or just install the latest BIOS fix that HP released for that series. It addresses the fan issue as well as some issues with the wireless not working properly. I ended up selling my HP back to the store for 100% of my purchase price including tax a year after buying it. 

Since the issue is with your BIOS which is independent of your operating system, I think you owe the Ubuntu developers an apology.

---

