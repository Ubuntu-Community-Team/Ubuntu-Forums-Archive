---
title: "Shut down don't shut the computer down"
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by Erikhh on 2004-11-16
When I shut down from Gnome, Ubuntu does all the right things, except the computer doesn't turn off. ACPI seem to function all right. What is wrong?

Erik

---

### Post by iminj on 2004-11-16
[QUOTE=Erikhh]When I shut down from Gnome, Ubuntu does all the right things, except the computer doesn't turn off. ACPI seem to function all right. What is wrong?

Erik[/QUOTE]

Other users have reported that adding the line "apm" to the file /etc/modules enables their system to completely power off. You can do this by entering the following into a terminal:

sudo gedit /etc/modules

Add 'apm' (no quotation marks) to the list of modules, and save the file.

I should add that this solution doesn't work for me, and I am unable to power down. I dual-boot my system, and complete power-down works reliably on the Win98 side - so I don't seem to have any BIOS or MoBo issues. It's a mystery.

iminj

---

### Post by jdong on 2004-11-16
If you want to use APM to send your computer to Linux pseudodeath (err, shutdown), you must also add **apm=power-off** to your boot options.

---

### Post by iminj on 2004-11-16
[QUOTE=jdong]If you want to use APM to send your computer to Linux pseudodeath (err, shutdown), you must also add **apm=power-off** to your boot options.[/QUOTE]

Thanks jdong ! Let me see if I understand you ..

I should add 2 lines to /etc/modules ? One line is **apm** and the 2nd line is **apm=power-off** ? Please clarify this .. thanks

iminj

---

### Post by TravisNewman on 2004-11-16
No apm goes in /etc/modules and apm=power-off goes at the end of your kernel line in /boot/grub/menu.list

---

### Post by az on 2004-11-16
You can just try adding the module to /etc/modules.  The apm=poweroff thing never made any difference for me.

---

### Post by HungSquirrel on 2004-11-16
This issue is a bug in ACPI in the 2.6.8.1 kernel if I recall correctly.

---

### Post by iminj on 2004-11-16
Looks like it a bug to me. To satisfy my own curiosity, I tried all 3 methods discussed so far:

(1) 'apm' added to /etc/modules
(2) 'apm' AND 'apm=power-off' added to /etc/modules
(3) 'apm' added to /etc/modules AND 'apm=power-off' added to kernel line of /boot/grub/menu.lst

All 3 methods failed to shut down my system.

I will continue to use the only reliable method I know of - pressing the power button on my PC for 7-8 seconds until the box shuts off. It works, and I can always delude myself into thinking that I'm getting an aerobic exercise benefit from doing it this way.

iminj

---

### Post by kmi on 2004-11-17
Hello !
I've only added 'apm' in /etc/modules and it worked on my Compaq Deskpro (PII)  :smile:
Will try it asap on my Toshiba Satellite Pro 4290...
Thanks a lot for these very newbie-oriented posts !

Update : It works on the Satellite too !

---

### Post by az on 2004-11-17
"All 3 methods failed to shut down my system."

What power management settings do you have in your bios?

---

### Post by iminj on 2004-11-17
[QUOTE=azz]"All 3 methods failed to shut down my system."

What power management settings do you have in your bios?[/QUOTE]

OK, we're talking about a legacy system. 

Dell Dimension XPS D266 - Pentium II - circa 1998
Dell BIOS ver. A09 -circa 1999

I checked Dell's website, and AO9 is still listed as the "latest" BIOS for this machine. 

I went into BIOS to examine the Power settings. It's not very verbose, and no mention of APM or ACPI (Dell proprietary, maybe?). The "Power" tab has the following 4 configurable settings:

Power Management = Enabled
Inactivity Timer = Off
Hard Drive = Enabled
VESA Video Power Down = Standby

thnx
iminj

---

### Post by duff on 2004-11-17
[QUOTE=HungSquirrel]This issue is a bug in ACPI in the 2.6.8.1 kernel if I recall correctly.[/QUOTE]
really? Do you have a bug report link?  This would explain a lot.  I've been using ACPI on my laptop for over 2 years, and I just installed Ubunutu on it a week ago and ACPI's doesn't work on it (even manually loading the module).  Any idea if they're going to provide the 2.6.9 kernel, without going through hoary?

---

### Post by az on 2004-11-17
For some bioses, you need to append
acpi=force 
to your kernel line in the grub menu.  The acpi module does not load for certain bioses for safety.

Insofar as APM, what does dmesg say when the module is loaded.

dmesg |less

or 

dmesg > file
nano file

---

### Post by HungSquirrel on 2004-11-17
Try adding "acpi=force" to your kernel line in /boot/grub/menu.lst while I look for the bug report if it exists.  My memory isn't the greatest so I may be mistaken.  ;)

---

### Post by duff on 2004-11-17
[QUOTE=azz]For some bioses, you need to append
acpi=force 
to your kernel line in the grub menu.  The acpi module does not load for certain bioses for safety.[/QUOTE]

[QUOTE=HungSquirrel]Try adding "acpi=force" to your kernel line in /boot/grub/menu.lst while I look for the bug report if it exists.  My memory isn't the greatest so I may be mistaken.  ;)[/QUOTE]

Ah!  I think I actually had to do this in Gentoo when I switched to 2.5.70...just so long ago I forgot about it.  Thanks to both of you, it worked.

---

### Post by jdong on 2004-11-17
as always, make sure you comp is okay after that, especially temperature-wise!

---

### Post by Erikhh on 2004-11-18
Thanks for your answers, but none of it works for me, sadly. I like Ubuntu a lot, but with this problem and the issue with lack of support for mp3, i feel compelled to move on to another distro,

---

### Post by ynef on 2004-11-18
[QUOTE=Erikhh]Thanks for your answers, but none of it works for me, sadly. I like Ubuntu a lot, but with this problem and the issue with lack of support for mp3, i feel compelled to move on to another distro,[/QUOTE]
Ubuntu lacks support for mp3s? Then what am I listening to right now? :confused:

You're not thinking about Fedora, right?

---

### Post by jdong on 2004-11-18
There are plenty of howto's here that show you how to install mp3 plugins from Universe.

---

### Post by Erikhh on 2004-11-18
Yes, but I dont have an internet connection on my computer. I have to go to work to acess the internet, so I cant get these mp3-programs - at least I havnt found an internetadress yet. If you have one, please tell me. When I enter the "universal"pool all I find is zipped files but no programs.

---

### Post by mr_ed on 2004-11-18
Yeah, that's all you'll see are zipped files.

So what you do then is create your own local repository.
Do you have a CD burner at work?

This is what I would try:

Download the packages for your correct architecture (I'll assume it's i386 from here on)
Download the Packages.gz, Packages.bz2, and Release from
[http://archive.ubuntulinux.org/ubuntu/dists/warty/universe/binary-i386/](http://archive.ubuntulinux.org/ubuntu/dists/warty/universe/binary-i386/)
and burn them onto CD, from the "dists" folder on.
/dists/warty/universe/binary-i386/Packages.gz
/dists/warty/universe/binary-i386/Packages.bz2
/dists/warty/universe/binary-i386/Packages.Release

Hopefully it fits on one CD.  :(

Assuming it does, change your /etc/apt/sources.list (or use Synaptic alternatively)
by adding
deb /media/cdrom0/ warty universe

Then make sure the CD is mounted (there should be a CD icom on your desktop)
and type in "sudo apt-get update"

If that didn't work, I'd try running "apt-cdrom add"
and then the apt-get update command.

Thoughts anyone?

---

### Post by Erikhh on 2004-11-19
Wow, thanks, I'll try that over the weekend. Great!

---

### Post by sembazuru on 2004-11-26
[QUOTE=Erikhh]When I shut down from Gnome, Ubuntu does all the right things, except the computer doesn't turn off. ACPI seem to function all right. What is wrong?

Erik[/QUOTE]
Erik:
I encountered this same problem with another Debian based distro. I learned that the problem was my outdated BIOS. I know nothing about configuring files. I had my computer plugged into a surge protector/power strip and was told that once the OS had shut down it was perfectly all right to just shut off the computer via the switch on the power strip. That's what I did and never had any problems.

---

### Post by Erikhh on 2004-11-29
Thanks. My only problem in relation to that is, that my computer is new. I dont know, if an opdate will do anything.

---

### Post by hashimoto on 2004-11-29
I had the "no shutdown" problem earlier in Mandrake. If memory serves I was able to fix the probelm by adding "nolapic" to lilo boot comments. But really, this is just a faint memory (and I have no idea why it was added and what it did). 

Hashimoto

---

### Post by robaid on 2008-02-27
I tried all options apm and apm=power-off but still i have the problem, is there any other solutions for this problem

---

### Post by spider74801 on 2008-03-10
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/archive/index.php/t-521540.html](http://ubuntuforums.org/archive/index.php/t-521540.html) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				gksudo gedit /etc/modules

then add this line:

apm power_off=1

hope this works

i found the solution here-- [http://ubuntuforums.org/archive/index.php/t-521540.html](http://ubuntuforums.org/archive/index.php/t-521540.html)

---

### Post by ellalan on 2008-03-10
sudo gedit /boot/grub/menu.lst (l here  is small L not 1)
Find the line
kernel /boot/vmlinvz-2.6.22-14-generic root...........ro quiet splash
after the word splash leave a space and type   acpi=force
It worked for me. HTH

---

### Post by fondoo on 2008-06-23
i had no luck with all the suggestions here. maybe i should just update the bios. i have a ibm thinkpad 570e.

---

### Post by Nucleus2008 on 2008-06-28
Greetings Kubuntu/Ubuntu users!

I found a temporary workaround for Kubuntu/Ubuntu systems failing to power down on shutdown (runlevel 0) and to reboot (runlevel 6) using sysrq key calls.

It's neither a fix nor any sort of solution but maybe some sort of workaround for some people.
I'd like to point out that there's absolutely no warranty of any kind that this won't damage your system with your specific configuration. At least it works fine for me.

Here it goes:

1. ENABLE SYSRQ KEYS
====================
open a terminal
edit "/etc/sysctl.conf" and append "kernel.sysrq=1"
call "sudo sysctl -p"

2. POWER DOWN
=============
the default shutdown command in "/etc/init.d/halt" is "halt -d -f -i $poweroff $hddown".
edit "/etc/init.d/halt" and comment out that line
add the following 3 lines afterwards:

echo s > /proc/sysrq-trigger
sleep 1
echo o > /proc/sysrq-trigger

The "/proc/sysrq-trigger" can be used to make sysrq key calls just like if you were pressing the corresponding shortcut (i.e. Alt + PrintScr + s).

"s" attempts to sync all mounted filesystems. This shouldn't be necessary since "/etc/init.d/halt" is only called after all filesystems are unmounted. But it does no harm - so better be safe ;)

"o" attempts to power down if your system supports it (this should be the case if power down worked for you before everything got screwed).

I added "sleep 1" because I don't know if sysrq key calls are synchronous, meaning if the next statement will not be executed before the predeceasing statement is finished and returns (does anybody know?). But since all filesystems are unmounted anyway this isn't really important, I think.

WARNING: "o" will power down immediately and doesn't care about unsynced filesystems, so make sure filesystems are unmounted should you want to try that shortcut manually!

3. REBOOT
=========
The default reboot command in "/etc/init.d/reboot" is "reboot -d -f -i".
Comment out that line and add the following 3 lines afterwards:

echo s > /proc/sysrq-trigger
sleep 1
echo b > /proc/sysrq-trigger

"s" see 2.
"b" attempts to reboot the system
"sleep 1" see 2.

Good luck!

Nucleus2008.

---

