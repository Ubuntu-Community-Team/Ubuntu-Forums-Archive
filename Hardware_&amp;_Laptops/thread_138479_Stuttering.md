---
title: "Stuttering"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by ate50eggs on 2006-03-02
**UPDATE:**

this is deffinitly an overheating problem. More specific details:

- ThinkPad 2626 70U (I beleive it is in the ThinkPad 390 series)
- The battery is broken (doesn't work in Windows either), so I am always on AC power
- I am running breezy with wdm and xfce as reccomended here:
[https://wiki.ubuntu.com/Installation...C%28systems%29](https://wiki.ubuntu.com/Installation...C%28systems%29)
- The fan turns on during startup (because it is under BIOS control ?) so the harware is not the problem

some things I have tried:

-putting 'acpi=off' (or 'acpi=off apm=on') in /boot/grub/menu.lst

this does not cause the fan to turn on at startup. the file changes don't get overwritten, it just doesn't work.


-manually activating the fan with: 'echo 0 > /proc/acpi/fan/FAN/state'

this turns the fan on right away, but a side effect is that kacpid starts taking up over 90% of CPU resources and the compter slows down dramatically. manually de-activating the fan with 'echo 3 > /proc/acpi/fan/FAN/state' reverses this. I also tried setting the priority of kacpid to 20 (also tried 19), but it goes right back up to the top of the usage list and the mouse keeps stuttering.



################################################## ##

**IGNORE**
> I am running breezey on an old pos (pII 64m) labtop. I am getting this weird problem where the laptop will suddenly get really really slow. the mouse stutters. I don't dare try and open anything new. I'm lucky if I can reboot without it crashing/hanging forever. I thought it might be a memory/processor issue. I re-installed with just the base system and installed xfce4 (I followed one of the instructions in the wiki for low memory systems). I'm still having the same problem.

so i'm thinking it could be a few things:

-Still low on memory/processor power. if this is the case I can install an even lighter system with fluxbox, dillo and not much else. That will be a pain (the most supported fluxbox needs to be compiled from source) and it will give up some functionality.

-Wireless. when I get the slowdown/stuttering I always notice that the lights on my wireless card are going nuts. I'm thinking maybe i'm using up a ton of resources disconnecting, and trying to re-connect a million times. not sure if this is even plausible and no idea how to fix it. is there some way to change the timeout or some setting. totally lost on this, but it's my favorite theory so far.

-Hard drive. the hard drive is effed. if this is the case I'll have to replace it. some easy way to track this down?

-Temp. maybe this happens when the comp gets too hot. not sure I really beleive this, but I haven't really been paying attention to temp and it varies a lot in my apt.

Hopefully someone has already had this problem and figured it out and I can just pack up my bs hypotheses and apply some easy fix.

---

### Post by cronholio on 2006-03-02
When it happens next time, press Ctrl-Alt-F1, log in and run "top". You will see which process is blocking your system. If it's non-vital, you can simply kill it and remove it from the init scripts.

---

### Post by ate50eggs on 2006-03-06
This is deffinitly an overheating problem. It always happens after a period (15-45 min) of running normally. Also, if the computer is shut down and restarted, it stutters after only a few minutes. I also noticed that the case fan is not moving.

Checked /proc/acpi/fan/FAN

there's only one file, "state" and it has only one line:

status:     off

---

### Post by cronholio on 2006-03-07
What if you boot with "acpi=off" (modify /boot/grub/menu.lst)? Does the fan work?

---

### Post by ate50eggs on 2006-03-07
I tried booting with acpi=off as recommended above. no difference in fan activity, but I know it did something because the shutdown command doesn't shut off the laptop anymore. I also tried:

acpi=off
apm=on

as recommended in other threads, but the results were the same as acpi=off as far as I can tell.

I discovered that i can turn on the fan by doing (as root):

echo 0 > /proc/acpi/fan/FAN/state

this turns the case fan on almost immediately, but the laptop still overheats in about the same ammount of time as before. it wasn't doing this under windows. the 'top' command gives a list of several processes running, but the cpu usage is always between %1 and %2.

##Edit:
the above command turns the fan on and also *causes* stuttering. my processor usage jumps to over 90%. the 'top' command shows that a process 'kacpid' is responsible for nearly all of the usage. when I turn the fan back off with:

echo 3 > /proc/acpi/fan/FAN/state

the machine stops stuttering, kacpid drops to very low processor usage and the total prossessor usage drops back down to %1-%2
##

this was not happening under windows, so I don't think the inside is simply gunked up. maybe a cpu scaling problem?

one other piece of info - I am always using this laptop with a/c power. the battery (or whatever it hooks into) is broken and I wasn't really planning on replacing it. I've seen some posts where people had overheating problems only with a/c.

---

### Post by ate50eggs on 2006-03-09
edit: 
<deleted>

oops.accidental dup post while editing first post.

---

### Post by ate50eggs on 2006-03-15
I finally got the fan working by switching to APM. I tried a few different sets of instructions, the solution that worked was provided by bsherman in this thread:

[http://www.ubuntuforums.org/showthread.php?t=2620&highlight=%22acpi%3Doff%22+apm](http://www.ubuntuforums.org/showthread.php?t=2620&highlight=%22acpi%3Doff%22+apm)

> 
ACPI is also somewhat broken on my IBM Thinkpad T23, well, APM seems to work much better anyway.

Here is a much simpler way to switch to using APM.

Edit your boot config using this command:
sudo nano /boot/grub/menu.lst

You'll want to change the kernel line to add the items in red.
Code:

kernel /vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash acpi=off noacpi

In order to make sure this change propegates to future kernel upgrades, you'll also want to edit the default lines:
Code:

## You can have ONLY one nonaltoptions line # nonaltoptions=quiet splash acpi=off noacpi


CTRL-X to save, and your boot config is updated.
One last thing, ensure you load the apm module.

sudo nano /etc/modules

Simple add a new line with the module name "apm":
Code:

psmouse mousedev ide-cd ide-disk ide-generic apm



Reboot, and you're running APM, not ACPI.

---

