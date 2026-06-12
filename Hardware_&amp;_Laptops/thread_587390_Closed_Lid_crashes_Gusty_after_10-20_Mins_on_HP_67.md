---
title: "Closed Lid crashes Gusty after 10-20 Mins on HP 6710b"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by rogirwin on 2007-10-22
I have an HP 6710b that I have installed Gusty Gibbon on and it all works fine until I close the lid and walk away.

When I come back the screen is on as I left it but the system has frozen. This only happens when I leave the lid down and after about 10-20 mins. If I open and close the lid for a short time it doesn't crash.

I have tried deleting /etc/acpi/lid.sh and commenting out /etc/acpi/events/lidbtn to:

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid
# event=button[ /]lid
# action=/etc/acpi/lid.sh

Is there a way to monitor what is causing it to crash? There are no relevant entries in /var/log/messages or syslog.

/proc/acpi/button/lid/C153/state works correctly showing when the lid is open/closed.

I have been using this laptop with Slackware 12.0 using a 2.6.21 kernel with no problems closing the lid. I'm guessing this is something to do with the way that ubuntu handles the lib closing event and then maybe running another event such as maybe CPU throttling or disable the wireless? Does ubuntu do this and how can I disable it?

Thanks.

---

### Post by kast on 2007-10-22
I had something like that with my Think pad i added

**noapic nolapic acpi=off  apm=power_off**

to my /boot/grub/menu.lst at the end of the current Kernel line i was using.
[B]
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=59113df3-2089-46e1-bc87-4c7c3ba65264 ro quiet splash noapic nolapic acpi=off  apm=power_of[/B]f

just a little snip-it, worth a shot.

---

### Post by rogirwin on 2007-10-22
Yes this is one solution and I'm pretty sure will fix the problem but it possibly introduces a new and much more server problem.

Have you seen: [http://gentoo-wiki.com/HARDWARE_HP_Compaq_6710b](http://gentoo-wiki.com/HARDWARE_HP_Compaq_6710b) and the warning about barbecuing.

**Barbecue issue with 2007.0 and older**
Warning: A BIT FAT ONE: I have almost fried my computer during install, because Gentoo 2007.0 LiveCD kernel 2.6.19 has old ACPI 20060707 (cat /proc/acpi/info). This old ACPI does not handle thermal_zones of HP 6710b and that's why the fan is always LOW on spinning (temperatures rise above 60 °C)!

Am I in any danger of barbecuing my laptop If I run without acpi enabled? Without acpi there isn't a way to monitor the CPU temp.

What I was thinking of is to recompile the kernel without the acpi_button enabled. I was hoping that there might be a way to solve with without having to do this. My thinking is that a script is being run somewhere within ubuntu to cause the crash or can someone confirm it's a kernel issue?

---

### Post by kast on 2007-10-22
Sorry rogirwin not sure if its a kernel issue, and i would keep it the way it is if your worried about burning out pc.

---

### Post by rogirwin on 2007-10-22
Thanks, It's a good suggesting. I'm just a little paranoid that I could fry my laptop without the acpi enabled. I've managed to brick a router once by wiping the firmware and really don't want to do the same to my laptop. It was a good lesson on what happens when you do things without really knowing what you are doing...

---

### Post by tgalati4 on 2007-10-23
Sounds like your laptop is going into suspend mode, comes out of suspend mode with the lid closed, heats up, then locks up.

With a thermal halt, there is no opportunity for Linux to write any log files so its a mystery to figure out what is causing it.

Perhaps it's time to dual or triple boot and keep Slackware, as that seems to work correctly.

I would install lm-sensors and a temperature gdesklet on your status bar with temperature logging turned on with 4 or 8 second logging.  When your machine locks up, you at least will have a temperature log and you may be able to correlate the hang with a temperature condition.

---

### Post by rogirwin on 2007-10-23
I have just run a test to check that possibly with a simple bash script.

#/bin/bash
COUNTER=0
while [  $COUNTER -lt 10 ]; do
        cat /proc/acpi/thermal_zone/TZ*/temperature >> temp.log
        sleep 2
done

The last recorded temperatures are:

temperature:             45 C
temperature:             40 C
temperature:             36 C
temperature:             27 C
temperature:             50 C

These are all in the normal range of operation.

---

### Post by Repabil on 2007-10-23
I am also getting these crashes with closed lid on my HP Compaq 6710b. Is there a way to fix it via Gnome's power management? Should we report the problems as a bug?

---

### Post by rogirwin on 2007-10-23
> **Repabil said:**
> I am also getting these crashes with closed lid on my HP Compaq 6710b. Is there a way to fix it via Gnome's power management? Should we report the problems as a bug?

Nice to hear that someone can confirm the problem. Are you also using Gusty?

I think that it's a kernel bug with acpi button or related script somewhere. None of the power management setting solved the problem for me.

Other than the scripts mentioned above I don't know of any others that are run when the lid is closed or opened. I have also disabled suspend and hibernate in /etc/default/acpi-support

# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

# ... Cut off here ...

The only thing left is the kernel and disabling acpi button but the will only make the problem go away if it fixes it. It won't prove the fault or find the real cause.

---

### Post by Repabil on 2007-10-23
> **rogirwin said:**
> Nice to hear that someone can confirm the problem. Are you also using Gusty?Yes, I'm running Gutsy (the 64 bit version to be exact).

I've added a link to this thread from [https://wiki.ubuntu.com/LaptopTestingTeam/HP6710b](https://wiki.ubuntu.com/LaptopTestingTeam/HP6710b).

Think we should post this as a bug on launchpad?

---

### Post by rogirwin on 2007-10-23
**Partial solution**

cd /lib/modules/2.6.22-14-generic/kernel/drivers/acpi/
sudo mv button.ko /root                   # (or somewhere safe)

Now reboot your computer.

You should no longer have /proc/acpi/button and linux can't tell if the lid is open of closed.

This reduces the number of crashes and should help on any model of laptop that crashes when the lid is opened / closed.

---

### Post by rogirwin on 2007-10-25
I have now removed these packages:

acpi
acpi-support
acpid
powermanagement-interface
ubuntu-desktop

So far my computer hasn't crashed and I have left it with the lid down a number of times. If this fixes the problem I'll enable the button module to load. At the moment I'm thinking it's a bug in one of the top 3 acpi packages and not in the kernel. Removing these packages means that the acpi still loads on boot but you should check yours ( ls /proc/acpi ) to see that it's loaded if you do the same.

At the moment I can't tell if the battery is charged but other then that it all seams to be running fine. I'll get that sorted when I norrow down the problem further.

---

### Post by koresko on 2007-10-29
I'm seeing the same issue with an Acer Aspire 5100.

In general, Gutsy seems much worse than Feisty in terms of stability.  It's crashed my laptop more in the last week than Feisty ever did.

So far it looks like the problems are associated with two things:

* The ACPI subsystem, especially the part that deals with the lid button.  The laptop no longer suspends when the lid is closed on battery power (as it's configured to do via the Gnome Power Manager), and now it turns out that the system locks hard when the lid is closed with the AC plugged in.  My system is configured NOT to sleep on lid close with the AC on, just to turn off the backlight.

* The bcm43xx driver.  This driver seems to work fine when the system is first booted, but suspending the system, resuming, and re-connecting causes a hang.  The last kernel message is the one that says the link is ready.  I've worked around this by turning off the bcm43xx firmware in the Restricted Drivers Manager, and using ndiswrapper instead.

---

### Post by koresko on 2007-10-29
Just to add another data point:

My laptop hung again.  This time the lid was OPEN and the machine was sitting idle for maybe 20 minutes; it was hung when I returned to it.  The backlight was on and the screen looked normal.  The fan was running, and I don't think the machine had overheated (it wasn't abnormally warm to the touch).

This happened with the button module not loaded, so apparently removing that was not a cure.

Given the timing, I suspect that some power management function kicked in and triggered the hang, but I have no idea which it could be.

There was no suspicious message in /var/log/messages.

EDIT: Well, that hypothesis was not correct.  The laptop hung up again in the middle of a web-browsing session.  So it's presumably not a power management function getting triggered by inactivity.

I remembered a case from years ago, in which another laptop exhibited similar random crashes.  I thought it had to be a hardware issue, so I sent the machine back to the manufacturer (NEC) for service.   Their service dept was prompt, courteous, and efficient, the very opposite of what I've seen more recently from Compaq.  Anyway, they said the CMOS settings had gotten corrupted; they reset them and returned the machine, which worked fine for years after that.

LESSON: if your system goes down hard, it could corrupt the CMOS and cause weird problems later.  The corruption is not obvious in the bootup settings menu.  I think the solution is to 'Reset to Factory Defaults', Exit with Save, reboot, put your CMOS settings back the way you like them, shut down to cold power-off, and boot gain.

Anyway, I did that with my laptop, and it hasn't crashed since (though that's not a strong confirmation that the problem is cured, since it occurs at random.)

SPECULATION: maybe the corrupt CMOS causes really aggressive timings somewhere, so that the machine is on the verge of failure.

---

### Post by rogirwin on 2007-10-29
Without acpid installed my 6710b with gusty is totally stable. It hasn't crashed at all since I removed it.

Problems with doing this are: Screen blanking when idle doesn't happen with the lib open, Can't monitor battery level with "Battery Charge Monitor" but can with acpi from the cli ("sudo modprobe battery" is needed first).

I can monitor CPU temp with sensors-applet and have seen TZ5 (CPU) reach up to 80°c with extended heavy usage. Should it get that hot? The fan seems to be working OK.

CPU Frequency Scaling Monitor shows that it's working too.

---

### Post by Repabil on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/157691](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/157691) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks for investigating this. I may try one of your solutions. Disabling the button killing screen when it's lid is closed seems safest. I hope the bug you reported will be fixed.

---

### Post by charon79m on 2007-11-11
I, too, am in this boat.  I have an HP 6710b that crashes with lid close.  I have removed the acpi button; however, I am still experiencing the lockup issues.

---

### Post by charon79m on 2007-11-11
After some research I've found that if I close the lid and open it again, everything is fine.  The second time I do this, the system locks up.

I can also confirm that if I leave the lid closed for 15-20 minutes or more, the system is locked up when I open it again.

Does anyone know if a bug has been submitted on this yet?

Mike

---

### Post by charon79m on 2007-11-11
A little more info..  The system is so well locked that it does not respond to Sysrq keys.  The thing is just plain locked up.

I'm heading to bugtrack now to see if this has been submitted.

Mike K.

---

### Post by charon79m on 2007-11-12
I too have removed the acpid package and found my system to be stable.  I agree with rogirwin's assessment:

"Problems with doing this are: Screen blanking when idle doesn't happen with the lib open, Can't monitor battery level with 'Battery Charge Monitor'"

In all, It'll work but I hope for a real solution soon.

---

### Post by xpertbg on 2007-11-18
Hello,
I'm using Debian unstable + 2.6.23 kernel from [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/](http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/) on HP 6710b and have the same problem - when I close the lid the laptop freezes. In my case removing acpid didn't work. When using boot parameter acpi=off the problem was gone. I found out that video.ko acpi module was causing the problem.

In [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.23.y.git;a=commitdiff;h=a21101c46ca5b4320e31408853cdcbf7cb1ce4ed](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.23.y.git;a=commitdiff;h=a21101c46ca5b4320e31408853cdcbf7cb1ce4ed) I found the solution for my problem:

# echo 1 > /proc/acpi/video/*/DOS

Could you please check if it works for you too.

Best regards,
Hristo Hristov

---

### Post by rogirwin on 2007-11-18
I think you have cracked it. I just reinstalled acpid under gusty. I then rebooted

cat /proc/acpi/video/C098/DOS  returned DOS setting: <4>

Did as you suggested and set it back to 1 and as yet I haven't managed to get it to crash.

I did notice that without acpid the value was set to 1.

---

### Post by thatvetguy on 2007-11-22
when i try to do that, i get a "Permission denied" message. using sudo like this doesn't work neither:

```
sudo echo 1 > /proc/acpi/video/*/DOS
bash: /proc/acpi/video/C098/DOS: Permission denied

```

how to do it correctly?

---

### Post by rogirwin on 2007-11-22
You need to become root first. Easiest way is to type:sudo -s and enter you password.

---

### Post by Mike Armstrong on 2007-11-22
May be of use Think I have solved this!!!!

At long, long last!

For suspend I followed the instructions here:

[http://ubuntuforums.org/showpost.php...9&postcount=12](http://ubuntuforums.org/showpost.php...9&postcount=12)

For hibernate I followed the instructions here:

[http://blog.paulbetts.org/index.php/...isty-and-edgy/](http://blog.paulbetts.org/index.php/...isty-and-edgy/)

Thanks to spikyit and Thursday Night. Very much appreciated!!!

---

### Post by gregorej on 2007-11-30
Looks like these links are broken. Could you post working ones?

---

### Post by David Gerard on 2007-12-01
I'm getting this on my 6710b as well (GR684ET) - freeze with the lid down. It doesn't come back from suspend, either - seems to come back, but the screen doesn't switch on.

By the way, if you want to monitor temperature, ktemperature is the easy way. Lives in your systray in both KDE and GNOME. Click on the 'NA', set it to /proc/acpi/thermal_zone/TZ0/temperature and you'll have a bright numerical display at all times.

---

### Post by Sproid on 2008-01-15
Hello. well it works but when I reboot DOS setting returned to <4>.  I have to use 
sudo -s
sudo echo 1 > /proc/acpi/video/*/DOS
each time I turn on my laptop 6710b
Any idea how fix this will be very appreciated.

---

### Post by rogirwin on 2008-01-15
sudo -s
pico /etc/rc.local 

and edit /etc/rc.local to look something like this:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


echo 1 > /proc/acpi/video/C098/DOS

exit 0

---

### Post by Bram-NL on 2008-04-10
> **rogirwin said:**
> [...]This does not work for me. I just did a fresh install, but it keeps freezing.
Should I maybe do any BIOS settings also?

---

### Post by boomdiddly on 2008-05-02
This has not been fixed in the release of hardy eather, i'll try these changed when i get home this evening.

Cheers

Paul

---

### Post by benitto on 2008-06-02
I thing I have solved this problem :)
I am currently using Fedora 9 but the problem is also in F8 and F9.. 
the first thing is to set the flag of /proc/acpi/video/*/DOS to 1 and then the lid works right, but when you suspend the machine it will not resume itself. If that /proc..../DOS flag is set to 0 everything works fine.
So the way how to do it is to set the flag to 0 just before going to sleep and to put it back to 1 after resume.
Ubuntu uses pm-utils to suspend (I hope) so you have to modify the suspend and resume script in /usr/lib64(or lib)/pm-utils.
I wrote this already to my blog:

1. set the /proc/acpi/video/*/DOS to 1 (echo 1 > /proc/acpi/video/*/DOS)
(if you want it to be persistant write it to the /etc/rc.d/rc.local
This should change this flag to 1 and after that the problem with lid button is gone (in my case) but display is not lighted up after suspend.

2. if you are suspending via kernel (it means no swsusp or linuxonice) modify /usr/lib64/pm-utils/modules.d/kernel. (or maybe /usr/lib/pm-utils...)
Add this line into the second function (do_suspend) into the else statement as follows.

else (this else is already written in the file)
  echo 0 > /proc/acpi/video/*/DOS (!add this line!)
  echo -n "mem" > /sys/power/state
fi (also included :) )

This should change the video flag back to 0 just before the suspend.

3. To set the flag to 1 after computer wakes up you have to modify /usr/lib64/pm-utils/sleep.d/99video and it's function resume_video()
add this line to the beginning of the function:
echo 1 > /proc/acpi/video/*/DOS

4. That's it. I know it is little bit "dirty" but it works.. Finally

I hop eit will help somebody 
Benitto

---

