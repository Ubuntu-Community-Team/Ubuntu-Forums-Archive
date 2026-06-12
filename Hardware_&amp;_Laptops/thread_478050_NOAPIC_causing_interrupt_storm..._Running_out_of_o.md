---
title: "NOAPIC causing interrupt storm... Running out of options here... :("
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Keyper7 on 2007-06-18
Hi Guys,

I didn't know if I should post this in a new thread or in a HP DV6000 thread. I decided to create
a new thread because this might affect other laptops and I didn't find about this in older posts
(although there is a lot of ways to describe this problem and I might've used the wrong keywords).

Anyway, here is the problem:I have a HP Pavilion DV6258SE laptop. It has a Turion X2 and a
GeForce Go 6150. As it usually happens with machines from the DV6000 series, I needed

  noapic noirqdebug

to properly boot the Live CD. Actually, I only needed noapic or nolapic to boot. The nolapic option,
however, made me lose cpu frequency control and without noirqdebug the system would launch
a "disabling IRQ" every five minutes or so.

With noapic, I didn't experience loss of USB ports or sound not working like some DV6000 users
have reported. I had, however, a problem somewhat serious: one of the cores would be constantly
handling hardware interrupts (top accused 90%hi). That made the fan to be constantly on and the
ondemand cpu governor became useless, since it always thought the freq needed to be at 100%.

After I installed the nvidia binaries, I could boot without the extra kernel parameters and the cpu
went back to normal (both cores more than 99% idle when I'm doing nothing). However, without
the parameters I did notice some instability and eventual hanging. After some weeks of using, I
can safely say the interrupt storm is the *only* problem I've experienced using noapic.

Now, I didn't see other DV6000 users who used noapic mentioning this. So maybe...

1) there is a way of avoiding the cpu usage problem while using noapic

2) people who experienced this problem didn't care, and neither should I because it's harmless

I honestly hope (1) is the answer, because having of the cores constantly working scares the
hell out of me. I'd rather use NOSMP. (which DOES solve the problem, by the way, but buying
two cores and only using one is quite a letdown...)

Does anyone here knows how can I solve this problem?

Thanks in advance,
-Keyper7

---

### Post by Keyper7 on 2007-06-19
I forgot to mention one thing: when I'm using the nvidia-glx package, I can't switch to terminal
if I'm not using noapic. The machine hangs and I have to hard reset. Terminals are fine if I use
noapic with nvidia-glx and they are unreadable but not hanging if I use noapic and nvidia-glx-new.

I don't know if this is relevant, but considering that I could only boot without noapic after
installing the proprietary drivers, I thought this might be important to mention.

---

### Post by kerry_s on 2007-06-19
post your /var/log/syslog

gedit  /var/log/syslog

use  
sudo gedit  /var/log/syslog

if you get permission denied.

---

### Post by Keyper7 on 2007-06-19
Here is the syslog without noapic noirqdebug:

[ATTACH]35836[/ATTACH]

[ATTACH]35837[/ATTACH]

[ATTACH]35838[/ATTACH]

---

### Post by Keyper7 on 2007-06-19
Now with noapic noirqdebug:

[ATTACH]35843[/ATTACH]

[ATTACH]35844[/ATTACH]

Thanks in advance, kerry.

---

### Post by kerry_s on 2007-06-19
Have you tried with> pci=routeirq
it looks to me like your laptop is using alot of shared resources, try checking your bios and disable what your not using, like serial ports, printer port, bluetooth, etc... that will help free resources.

Also try using> lapic
to let it know you want that enabled

---

### Post by Keyper7 on 2007-06-19
Hi kerry_s,

I've tried irqpoll, noirqpoll, noapic, noapci, pci=noirqpoll, lapic... All without success.
However, just now I think I discovered the culprit. I noticed that, if I boot with noapic
but without noirqdebug, it does that "disabling irq". It was IRQ 7 that was being
disabled. Doing a cat /proc/interrupts I got

```


            CPU0       CPU1       
  0:      76896       5622    XT-PIC-XT        timer
  1:        986         49    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  5:       6175        521    XT-PIC-XT        libata
  7:      11259     140386    XT-PIC-XT        ehci_hcd:usb2
  8:         29         13    XT-PIC-XT        rtc
  9:       7881       1012    XT-PIC-XT        acpi, eth1
 10:      27155       2102    XT-PIC-XT        HDA Intel, eth0
 11:      19596       1307    XT-PIC-XT        ohci_hcd:usb1, ohci1394, sdhci:slot0, nvidia
 12:         85         39    XT-PIC-XT        i8042
 14:       1839        860    XT-PIC-XT        ide0
NMI:          0          0 
LOC:      82388      82390 
ERR:       1811
MIS:          0


```

So I did a modprobe -r ehci_hcd and... bingo. The interrupt storm stopped...
and I obviously lost ehci_hcd. Is there any solution that does not involve
me losing USB 2.0?

Thanks again,
-Keyper7

---

### Post by Keyper7 on 2007-06-19
Ok, now I've tried something weird:

1) removed both ehci_hcd and ohci_hcd (USB ports stopped working at all, as expected)
2) loaded ehci_hcd (/proc/interrupts associated it with usb1, ports worked again)
3) loading ohci_hcd (/proc/interrupts associated it with usb2, ports still working)
4) removed ehci_hcd

After this procedure:

1) /proc/interrupts still had ohci_hcd:usb2
2) the usb ports were working, but I'm not sure if they are USB 2.0 capable right now (how can I test this)
3) cpu usage is stable at low levels

Now, this leaves me with two questions:
1) does this procedure allows me to use USB 2.0?
2) if so, how can I make it permanent?

Thanks,
-Keyper7

---

### Post by Keyper7 on 2007-06-19
Impressive. Now that I've found the connection between my issue and ehci,
I could find tons of forum and mailing list posts about it... :) Unfortunately, they all
seem to agree that the best workaround is to blacklist ehci and leave it like that.

Still, USB 1.1 is still much better than constantly high CPU usage for me, I think...

Thanks a lot for the support, kerry.

-Keyper7

(crossing my fingers in hope that this is solved in Gutsy)

---

### Post by ArTaX on 2007-08-08
What was your solution?
I have a HP dv6383eu.
My problems are frequent hangs and the solution is to boot with the nosmp option...
but i want to use both cores...
Do you think that also my problem is correlated to ehci?

---

### Post by Cywolf1 on 2007-08-10
To all folks out there looking for an APIC/ACPI solution for Ubuntu AMD boot lockup problems:

**My Hardware:**
HP dv6324us
Gutsy Distro (Tested with feisty, seems to work)
2.6.22 Kernel
AMDx2 - 1.6
Nvidia 6150
Nvidia chipsets (All the goodies on HP)
bcm43xx driver
etc...

After many weeks of searching through kernel documentation, I think I may have found a permanent soluton to the kernel boot problem.  Most people can  temp. resolve the problem with either noapic noacpi or other kernel options that disable or impair the apic/acpi on the system.  Fear no more the loss of IRQs, use more than 2 usb devices all at once, and free yourself from the random loss of your wireless cards............... okay so now that everyone is anxious...simply append this to the kernel boot option

pci=conf1

so for the ubuntu (linux) rookies...
when grub boots, press esc to stop boot on a grub menu, press e on the kernel line, and at the end of the line append "pci=conf1" without the quotes....then press enter, and then b, and witness the glory.

It almost seemed too simple, and I nearly cried when the system booted up faster and smarter.  I've got all my APIC set to fasteoi and some on edge triggered, just like it should be.  I've also got all 8 USB ports found, full working display, wireless, nics, and even my battery stats appear to be more accurate.  I am also using compiz and it's running ten times faster (cause the kernel is not tweaking out).  Oh it's sheer beauty....I rarely post, but I figured it was time to share the love.  I know that I will be making so many folks with HP dv6000 series or other HP model owners supremely happy!!  :)  I know I AM... YEAH.  Hopefully the fix works on other platforms with similar issues.


Cyber///olf

---

### Post by Cywolf1 on 2007-08-10
One more thing.....my USB 2.0 works 100% too, and it's no longer eating up power and interrupt time....it's truely a godsend of a kernel option....now if the kernel guys can patch it or ubuntu can correct it in the gutsy distro, that would be awesome!!
:)
:)
:)

Sorry I am obviously happy....oh and regardless of the ubuntu ranking this forum has given me, I have been working with ubuntu for ever....I use it on servers (excellent server distro), I program on it, and have used it extensively for a workstation for a long long time...:)  


P.S. Ubuntu will take down the beast known as Microsoft one day, have faith dear brethren....once the system is more stable and noob proof, Microsoft will die....and Vista (The biggest pile of Microsoft manure) will die with them.

:)

---

### Post by inyearstocome on 2007-08-13
> **Cywolf1 said:**
> 

so for the ubuntu (linux) rookies...
when grub boots, press esc to stop boot on a grub menu, press e on the kernel line, and at the end of the line append "pci=conf1" without the quotes....then press enter, and then b, and witness the glory.

Cyber///olf

Sorry, i'm even more beginner than that.  I'm trying to install from the Feisty boot disk.  I assume you are refering to Grub on the boot disk, before installation, or do you mean Grub on the local drive after it is installed?  I cant figure out what the"press e on the kernel line" means.

If I try a regular install, it doesnt work and hangs at a black screen.  Any help is greatly appreciated.:)

EDIT, nevermind, i installed by appending noapic, and then I Figured it out on regular grub.  Thanks!

---

### Post by offchance on 2007-08-15
I've been having [issues with my usb ports]("http://ubuntuforums.org/showthread.php?p=3167333#post3167333") and I'm starting to think it's the noapic/nolapic additions to my boot command that might be causing the problem. I tried the pci=conf1 option but it caused the computer to hang during boot. is there anything else you recommend I try?

---

### Post by jcaveman on 2007-08-16
noapic appears to disable part of the interrupt system that USB needs to function in addition to noapic add irqfixup to the kernel options.  I tried pci=conf1 on my HP Pavilion 6119us and it seems to work about 1 out of 10 boot ups.  The rest of the time the machine locks up during boot.

---

### Post by corelogic on 2007-08-17
Cywolf1 >> I tried the pci=conf1 and encountered a black screen of death.

My laptop = DV6000 (DV6258SE) AMD Turion 64 x2 with nVIDIA chipset.

Since I am new I can not dive too deep into the kernel or config of Ubuntu, yet.  I am weening myself off of the Redmond software after 13 years.

An interesting point is that I purchased SLED 10 (SuSE Linux Enterprise Desktop) a couple months ago.  I just now installed it onto my DV6000 over-writing my Ubuntu 7.04 installation.  I did not have to use any options such as **noapic** or **nolapic**.

I am hoping that the engineers at Ubuntu will figure out what SLED10 did to make everything work from the install DVD and incorporate the fix in the next release.

---

### Post by offchance on 2007-08-17
I added irqfixup (in addition to the previous noapic nolapic) and it works great!

also of interest, a similar discussion at [hp's website]("http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1148213&admit=-682735245+1187352906447+28353475").

---

### Post by corelogic on 2007-08-18
I was searching for the nvidia chipset and came across the below tidbit:

"Other distributions - noapic kernel parameter
Other distributions (Ubuntu Feisty) come with buggy kernels and require noapic in order to boot properly. It can be fixed by compiling your own kernel (I used the same config as Slackware) from vanilla sources from kernel.org. Also, X.org 7.2 drivers work when APIC is disabled (otherwise you get a black screen instead of a login manager), but I recommend disabling APIC as a temporary workaround until the closed-source nVidia drivers are installed.

noapic is only meant for debugging. noapic might cause more problems (such as with USB) and piling on more kernel parameters to work around the workaround will disable power management and CPU frequency scaling."

From: [http://red.caek.org/slack-dv6258se.html](http://red.caek.org/slack-dv6258se.html)

A side note:

My DV6000(DV6258SE) uses the nVIDIA chipset nFORCE 430/410 and video GeFORCE Go 6150.  I could not find that information anywhere and thought I would post it here so Google.com could crawl the information.

---

### Post by heatonx23 on 2007-08-19
I have to say that adding "pci=conf1" to the boot was amazing. I have an HP dv6436nr (dv6000 series), and the noapic was not doing it for me. It allowed me to boot and everything, but my system would hard freeze randomly for no apparent reason. I tried about 10 billion different kernel parameters, like noapic, nolapic, irqpoll, irqfixup, pci=routeirq, and many others. Nothing seemed to work, and my system locking up was getting really annoying.

I was convinced it was an nvidia driver issue, but even on a clean ubuntu 7.04 (feisty amd64) install with no nvidia drivers or 3d effects (i.e. beryl/compiz), my system would still freeze. So I figured it had to be a kernel issue of some sort.

To make a long story short, the first time I tried your "pci=conf1" suggestion, it did NOT work. I don't know why, but it wasn't unti I removed the "quiet" option that it finally worked successfully and consistently. So maybe people having trouble could try that if they're still having a similar issue.

Anyway, thanks for the tip, and hopefully it helps others out, as well.


**UPDATE: **Actually, I spoke too soon. Although my system did run great for more than a day, eventually it froze up where the mouse would still move but nothing would work. I had to do a hard reset, and the "pci=conf1" parameter never successfully let me boot up again. I also tried the latest gutsy alpha, and it didn't work there either. I get one of three errors, which seem to rotate: (1) Booting freezes at "loading hardware devices", (2) Booting freezes at "configuring network interfaces", or (3) Bootup seems successful and looks as though it's going to load X, but it just hangs on a black screen.

Any additional insights would be great, I can't seem to figure this stupid thing out, and it's really annoying to have my system freeze all the time. Is there an alternative kernel to the generic one that comes with the amd64 ubuntu? Maybe that could help.

---

### Post by Cywolf1 on 2007-09-07
Okay, I originally posted that pci=conf1 works.......and I was right, for the first 4 boots, but mine finally froze too.  I got a little ahead of myself....guess I was giddy that I finally got it to work after months of searching for an answer. 

Now, I have tracked the issue down to the RTC system clock.  I am pretty sure this is the issue.  I have run tons of debug, and the HP dv6000 series (Mine is a dv6324us) seems to needs a higher clock speed.  To fix the problem with booting and to eliminate the freezing issues while booting, the following fix is working for me now.  I hope it continues to hold.

So in /etc/sysctl.conf put this line, and end your woes!!

dev.rtc.max-user-freq = 1024

or just

echo "dev.rtc.max-user-freq=1024" >> /etc/sysctl.conf


After you boot, cat /proc/sys/dev/rtc/max-user-freq should return1024 not 64 (I think thats default).  I have rebooted a couple of times, and I have been running the system for over 2 hours without issue.  I am anxious to have others test this out.  If it fixes the problem, then I will hopefully have made tons of people happy.  I am happy.  I can finally see all my interrupts and devices, no problems with USB....it's nice..I said that before, but I have a good feeling about this one.

Cyber///olf

---

### Post by Cywolf1 on 2007-09-07
So I forgot that a lot of new users might be reading this.  Basically you will need to boot as you normally would with the noapic option first to get the computer to boot.  Once you have booted into gnome of kde....run a terminal and paste the command below into the terminal.

echo "dev.rtc.max-user-freq=1024" >> /etc/sysctl.conf

What this is basically doing is telling the system control config file to change the default real time clock frequency to 1024 instead of the 64...or whatever the default ubuntu install is.  So once again, hope this helps....I'll will monitor this thread and ensure that everyone gets the hopeful message.

So far like I said, mine is running well for now.

---

### Post by rbrewer on 2007-09-13
I got one successful boot out of this, but it never worked again for me.  I tried a lot of other things too, and have found that your irqfixup idea is better than what I was using before.  My current boot options are "noapic irqfixup".  powertop shows about 250 spurious ehci interrupts per second, but my system is very stable.  If anybody would like to help figure this out for the gutsy release there is a bug thread here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746)

As I just posted on the bug thread, the SimplyMEPIS liveCD (64-bit) seemed to boot fine without any options on my system.  I think it is running the 2.6.15 kernel.  So somewhere between 2.6.15 and the current kernels something went awry.  Perhaps bisecting the kernel changes between that release and the current ubuntu kernels can help us find which changeset introduced the problem.

---

### Post by Keyper7 on 2007-09-18
In terms of hanging, noapic is undoubtely the most stable option for me: with noapic enabled, 100% of my boots and shutdowns work. However, there's a high price to pay for it:

1 - having to choose between losing USB 2.0 or having of the cores 100% occupied by spurious interrupts generated by ehci_hcd module.
2 - losing suspend and hibernate (can't get them to work with noapic, but both work flawlessly without it)

As far as I know, I noticed no other problems while using noapic, so if those two were solved I could accept keeping it in the parameter list.

---

### Post by Keyper7 on 2007-09-18
Actually, I just found out that I can suspend and hibernate with noapic. I think the kernel upgrade to 2.6.22 had something to do with it.

Anyway, that means my only problem are the spurious ehci_hcd interrupts. Any progress on this?

---

### Post by Keyper7 on 2007-09-18
Update: I recently found these links:

  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235)
  [http://lists.debian.org/debian-kernel/2005/02/msg00179.html](http://lists.debian.org/debian-kernel/2005/02/msg00179.html)
  [http://kernelfr.traduc.org/ftp/2.6.15/a_traduire/drivers/usb/host/Kconfig](http://kernelfr.traduc.org/ftp/2.6.15/a_traduire/drivers/usb/host/Kconfig)

The problems described in the first two links are different than mine, but it seems
that there some experimental ehci options that might be buggy in some cases.

Does anybody here tried to recompile the kernel without those options?

---

### Post by rbrewer on 2007-09-18
I think noapic is clearly just a workaround for us to use our laptops until we get the root cause of the problem fixed.

I'm not aware of anyone trying those ehci compile options.  See the last few messages in this thread for what I have been recently trying:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746)

---

### Post by Keyper7 on 2007-09-18
rbrewer, this might be interesting:

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17-7.19/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17-7.19/changelog)

It seems the experimental ehci modules I mentioned were enabled after 2.6.15.

---

### Post by rbrewer on 2007-09-19
keyper: a while back I found that "rmmod ehci_hcd" seemed to help my interrupt problems.  At the time I attempted to boot with that module completely disabled but was unsuccessful (despite my attempts the module kept getting loaded).  I think I just realized that the module was probably included on my initrd which I never changed in that process.  Perhaps a good test would be to prevent ehci_hcd from being loaded at bootup and see if it allows us to boot without noapic.  Some poking around with update-initramfs might yield how to do this and should be much easier than kernel compiles.  If you have some older kernels still on your box, perhaps mucking with one of those would be better so you can be sure you don't damage your main boot kernel.

---

### Post by Keyper7 on 2007-09-19
Actually, I already did that before: blacklisting ehci_hcd and doing a update-inittramfs indeed works. As far as I can remember, this procedure was 100% successful in allowing me to boot with noapic but without spurious interrupts. The obvious problem was losing USB 2.0 support, which is not acceptable for me because I do a lot of file transfers through the ports.

That's why those ehci parameters I mentioned got my attention recently: they seem to be experimental features enabled by default, but disabling them in kernel compilation does not mean disabling the module itself.

Another thing I'm thinking right now is that the problem might be caused by two devices conflicting and reallocating the IRQs might solve the problem. However, my BIOS settings do not give such option and I'm looking for a software alternative.

---

### Post by Keyper7 on 2007-09-22
Finally, some progress: I found out that using

noapic acpi_irq_balance

avoids loading one of the cores with the spurious interrupts. There are still such
interrupts, as cat /proc/interrupts shows ERR growing like crazy. But  they seem
to be being redirected into oblivion instead of occupying a core.

Overall, I still feel some performance losing, but so far this is being much more
acceptable than just using noapic. I have USB2, suspend and hibernate working
perfectly.

I have a feeling that acpi_irq_balance worked because no device was allocated
to IRQ 7. Perhaps it's not an ehci_hcd problem, but a IRQ 7 allocation problem? I
stumbled across acpi_irq_balance exactly because I was looking for an option
that allowed me to change the irq table.

(By the way, my compiz fusion freezes seem to be more rare since I started
using this parameter. But it could be just an impression)

---

### Post by phssthpok on 2007-11-12
Here is what I did to fix my issue and boot without the noapic kernel flag. 

Symptoms: without noapic kernel flag, boot hangs on "loading hardware drivers". Giving noapic forces you to remove the ehci_hcd module in order for USB to work. Spurious interrupts on IRQ7 and nontrivial processor time spent handling hardware interrupts.

Outcome after fix: USB 2 works all the time, no spurious interrupts on IRQ7, CPUs consume less than 1% of processor time handling hardware interrupts.

(1) Make a backup of /etc/network/interfaces. This might come in handy later.
(2) Edit /etc/init.d/udev and change instances of 

/sbin/udevtrigger

to

/sbin/udevtrigger --subsystem-nomatch="*misc*"

(3) Disable hwclock scripts in /etc/init.d/ (there are 2) (look around the forums for how to remove startup scripts using update-rc.d

(4) Reboot. If you are running Gnome you may have a problem with gnome-settings-daemon not loading. I fixed this by commenting out all the IPv6 lines in /etc/hosts. I have also heard of people finding that references to the loopback device have disappeared from /etc/network/interfaces (thus the backup; if anything has changed, restore it to how it was).

(5) Un-blacklist ehci_hcd if you have added it to /etc/modprobe.d/blacklist.
(6) Reboot. At this point, everything started working for me.

Good luck.

---

### Post by gnelson on 2007-11-21
I'm still an ubuntu newb, but I was having problems with my HP DV6324us so I braved it and tried this fix.  NOAPIC NOLAPIC worked okay, but I was unable to use my USB external hard drive.  So far this solution lets me boot without NOAPIC and my USB hard disk works perfectly.

Thank you!

> **phssthpok said:**
> Here is what I did to fix my issue and boot without the noapic kernel flag. 

Symptoms: without noapic kernel flag, boot hangs on "loading hardware drivers". Giving noapic forces you to remove the ehci_hcd module in order for USB to work. Spurious interrupts on IRQ7 and nontrivial processor time spent handling hardware interrupts.

Outcome after fix: USB 2 works all the time, no spurious interrupts on IRQ7, CPUs consume less than 1% of processor time handling hardware interrupts.

(1) Make a backup of /etc/network/interfaces. This might come in handy later.
(2) Edit /etc/init.d/udev and change instances of 

/sbin/udevtrigger

to

/sbin/udevtrigger --subsystem-nomatch="*misc*"

(3) Disable hwclock scripts in /etc/init.d/ (there are 2) (look around the forums for how to remove startup scripts using update-rc.d

(4) Reboot. If you are running Gnome you may have a problem with gnome-settings-daemon not loading. I fixed this by commenting out all the IPv6 lines in /etc/hosts. I have also heard of people finding that references to the loopback device have disappeared from /etc/network/interfaces (thus the backup; if anything has changed, restore it to how it was).

(5) Un-blacklist ehci_hcd if you have added it to /etc/modprobe.d/blacklist.
(6) Reboot. At this point, everything started working for me.

Good luck.

---

### Post by old_salt on 2007-11-21
I've been fighting this for a long time but I've tried everything listed in this topic and even combos of recommendations and nothing works for me. All attempts were fresh installs without any restricted drivers in use. BASE INSTALL.......Everything locks up on boot. Leaving noapic in to get booted results in even higher Interrupt usage than before. 

HP Dv9000z AMD Turion x2 2.2Ghz
All nVidia hardware and chips.

Oh and removing the clock startups locked my system dead even with noapic. I can't recall how many wipe and reloads I've done today testing these suggestions out. 



I really wished the Canonicla staff would give some attention to this issue as a large market share of users run these laptops. They certainly have more knowledge and talent than we can as average users to resolve this quickly enough. They could compile a special kernel for us that saves everyone a lot of time and certainly make even more happy users.

---

### Post by gnelson on 2007-11-25
> **phssthpok said:**
> Here is what I did to fix my issue and boot without the noapic kernel flag. 

Symptoms: without noapic kernel flag, boot hangs on "loading hardware drivers". Giving noapic forces you to remove the ehci_hcd module in order for USB to work. Spurious interrupts on IRQ7 and nontrivial processor time spent handling hardware interrupts.

Outcome after fix: USB 2 works all the time, no spurious interrupts on IRQ7, CPUs consume less than 1% of processor time handling hardware interrupts.

(1) Make a backup of /etc/network/interfaces. This might come in handy later.
(2) Edit /etc/init.d/udev and change instances of 

/sbin/udevtrigger

to

/sbin/udevtrigger --subsystem-nomatch="*misc*"

(3) Disable hwclock scripts in /etc/init.d/ (there are 2) (look around the forums for how to remove startup scripts using update-rc.d

(4) Reboot. If you are running Gnome you may have a problem with gnome-settings-daemon not loading. I fixed this by commenting out all the IPv6 lines in /etc/hosts. I have also heard of people finding that references to the loopback device have disappeared from /etc/network/interfaces (thus the backup; if anything has changed, restore it to how it was).

(5) Un-blacklist ehci_hcd if you have added it to /etc/modprobe.d/blacklist.
(6) Reboot. At this point, everything started working for me.

Good luck.

Ok, now I need help.  I tried this workaround and it did manage to get by external USB hard drive working and seemed to work all of the way around.  However, I started having issues with the system clock.  It was often wrong and I would even get error messages at boot about the system clock being drastically wrong (like 1999).

Is there an easy way to undo these changes?

---

