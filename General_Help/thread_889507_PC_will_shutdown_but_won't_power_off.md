---
title: "PC will shutdown but won't power off"
date: 2008-08-14
forum: General Help
---

### Post by Redsandro on 2008-08-14
Hi,

I have this Pentium 4 800 MHz running Xubuntu 8.04 [SIZE="1"](Fully updated as of 8-8-2008)[/SIZE] that - when told to shutdown - does the shutdown stuff and then freezes in the shutdown graphic screen (you know, the same one you see when starting up).

Then I hear a click; I THINK the hard drive is shutting down. But the fans keep blowing and the screen keeps showing. Back when it was running XP, it did power off, so I know it's got the proper hardware for that.

Also, sometimes [SIZE="1"](looks random to me)[/SIZE] when told to shutdown, it partially reboots, showing me a *'what to do next'* screen. Also sometimes, it just goes back to the login manager, as if I restarted X by ctrl+alt+backspace. In both cases, I disipline the computer by switching the power (at the back of the computer) off[SIZE="1"], because if I wanted to play games I wouldn't tell it to shut down.[/SIZE]

PS - I remember my P2 266MHz had the exact same problem a million years ago with Red Hat 5. It was fixed when I installed Xubuntu 6.

---

### Post by unutbu on 2008-08-14
Redsandro, do you use any special kernel options to boot -- such as "acpi=off"? ACPI is usually in charge of powering off the machine, if for some reason ACPI is not working, there is a workaround, which is to use the apm module instead. (See below).

---

### Post by unutbu on 2008-08-14
[list=1]
[*] 
```
gksu gedit /etc/modules
```
Add 'apm' to the bottom of the file. Save.

[*]Create the file /etc/modprobe.d/power:
```
gksu gedit /etc/modprobe.d/power
```
Add the line
```
options apm power_off=1 realmode_power_off=1
```
Save and quit.

[*]Now try booting again, but this time with kernel option "apm=on". ([See below]("http://ubuntuforums.org/showpost.php?p=5586563&postcount=4") for how to boot with a kernel option)
[/list]

This information comes from: [http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)

---

### Post by unutbu on 2008-08-14
There are two ways to boot with kernel options:
[list]
[*] **The temporary way:**
This  method inserts the kernel boot option for only a single boot session. When you reboot, the kernel boot option will be gone. This is good for testing new options.
[list=1]
[*] When you power up the machine, first a BIOS or manufacturer's splash screen usually appears. Wait for that to disappear.
[*] The next screen is mostly black, with a bit of text in the upper left corner. This is a sign that GRUB has taken over the boot process. Press the escape (ESC) key. You usually have about 3 seconds to press the ESC key before GRUB decides to boot the default OS.
[*] You should now be at the GRUB menu. Each line of the GRUB menu represents a different OS to boot. Press 'e' to edit the boot options for a particular OS. (Use the up/down arrows to select the OS)
[*] You should now see something like this:
```

root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```
Use the down arrow to select the line that begins with the word "kernel"
[*] Press 'e' to edit the kernel line
[*] Press End (or use the arrow keys) to move to the end of the kernel line.
[*] Type in the new kernel option, e.g. "apm=on", then press return. The new kernel line should now look like this:
```

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash **apm=on**

```
[*] Press 'b' to continue the boot process
[/list]
[*] **The permanent way:**
This is the method to use once you are confident you want to use a particular boot option.
[list=1]
[*]```

gksu gedit /boot/grub/menu.lst

```
About 2/3 of the way down you'll see lines that look somewhat like this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Look familiar? Again go to the line which begins with the word "kernel", and add your kernel option (e.g. "apm=on") to the end of the line.
[*] Save and quit. The next time you boot the machine, the kernel option will be used.
[/list]
[/list]

---

### Post by botokely on 2008-08-14
> **Redsandro said:**
> Hi,

I have this Pentium 4 800 MHz running Xubuntu 8.04 [SIZE="1"](Fully updated as of 8-8-2008)[/SIZE] that - when told to shutdown - does the shutdown stuff and then freezes in the shutdown graphic screen (you know, the same one you see when starting up).

Then I hear a click; I THINK the hard drive is shutting down. But the fans keep blowing and the screen keeps showing. Back when it was running XP, it did power off, so I know it's got the proper hardware for that.

Also, sometimes [SIZE="1"](looks random to me)[/SIZE] when told to shutdown, it partially reboots, showing me a *'what to do next'* screen. Also sometimes, it just goes back to the login manager, as if I restarted X by ctrl+alt+backspace. In both cases, I disipline the computer by switching the power (at the back of the computer) off[SIZE="1"], because if I wanted to play games I wouldn't tell it to shut down.[/SIZE]

PS - I remember my P2 266MHz had the exact same problem a million years ago with Red Hat 5. It was fixed when I installed Xubuntu 6.

Just to say that I've the same problem SOMETIMES with my EEE PC (not exactly the same problem but it is analogue, I think).

After shutting it down, my laptop won't power off. The fans keep blowing and the little light showing that it is plugged :( doesn't switch off (even if I've unplugged it and it runs on my battery). But the screen doesn't show anything else anymore. And if I try to switch on my computer it won't switch on (I have to reset it [-o< ).

I've no idea where does the problem come from and how to fix it :confused: ?

---

### Post by Redsandro on 2008-08-14
Hey **unutbu**,

Thanks for your extremely elaborate response. There was no need to be so explicit, but I appreciate you took the time!
While checking the bootoptions, I rediscovered something and it's **VERY** stupid that I forgot about it! I manually added *acpi=off* some time ago after upgrading from Xubuntu 7 to 8 because the PC suffered random crashes (hangs) with it turned on. After that I went on a vacation and I totally forgot about it. I forgot about it so hard that I was sure I had no extra boot options applied and I didn't find it necessary to take a look.

I've turned it back on, gonna let it run a few days to see if some update fixed the issue already. [SIZE="1"](I think not - I rarely see bugs that only affect older computers fixed.)[/SIZE] If I catch it hanging again, I will switch to **apm**. You showed me how to do that - thanks!

**botokely**, maybe you should check the above presented option to see if it works for you. I've seen an 10" EEE PC and it's something really cool. Could you tell me, how is it to run Linux off of it? I really love linux on my server and media center because it's really versatile. But to be honest, I've never seen any of my computers boot Ubuntu less than twice as slow as Win XP, and the one place I actually do care about boot times is on my laptop. So I ditched Ubuntu for XP on my laptop.

---

### Post by unutbu on 2008-08-14
Hello Redsandro,
  Glad to hear you've got the problem pretty much solved. Sorry if my response was too much. Although I wanted to help you, I'm also getting tired of typing similar things over and over, so I'm now trying to post in a form that I hope will be reusable in the future.

---

### Post by Redsandro on 2008-08-15
Hi,

That's actually a very good idea. There isn't really room for question (how do I ...) in your explenation so I bet is very reusable.

I tried your method anyway because I had some more problems with APCI. Unfortunately I found that it didn't work (computers shuts down but doesn't power off) in this case. So back to APCI I have the problem that coming back from suspend-to-memory or suspend-to-ram leaves my monitor off even if I switch to a terminal. I can ssh to the computer from another one to tell it to reboot, and then it's okay.

I tried adding *SAVE_VBE_STATE=false* and *POST_VIDEO=false* to */etc/default/acpi-support* but no success.

---

### Post by unutbu on 2008-08-15
Hm. Sorry to hear it didn't work. It seems to work for some machines ([http://ubuntuforums.org/showpost.php?p=5537814&postcount=20](http://ubuntuforums.org/showpost.php?p=5537814&postcount=20)), but apparently not for others. Did you try "apm=on" alone or in conjunction: "acpi=off apm=on"? 

If neither work, then I'm out of ideas...

---

### Post by Redsandro on 2008-08-15
yes, I tried a bunch of them
```
acpi=off apm=on
acpi=off apm=on noapic nolapic
noapic nolapic
acpi=on noapic nolapic
```
etc. but no luck.

Thanks for helping anyway! At the moment I've postponed solving this problem because after an update my sound is gone, and on a mediacenter that's even more crucial!

I guess this just ain't my day on linux :P

---

### Post by dragos240 on 2008-08-15
If all else fails.... reinstall Xbuntu. Good luck with your problem. But if nothing works theres nothing like good ol' reinstalling the os. Installing ununtu took me 30 minuites, so it's not very risky for me, or time consuming. Hope all goes well!
Dragos240

---

### Post by Redsandro on 2008-08-15
Thanks. I am so pissed off at Ubuntu now. And maybe at myself, too. Because I didn't think I'd have to reinstall Ubuntu before the LTS ran out, so I only created one partition. Now I have to back everything up on a slow drive.

So.. it's doing that for 2 hours now and I haven't even come to reinstall yet. Anyway I'm going off topic.. when everything is back, I might revive this topic because no way THIS problem will be gone.

---

### Post by tinman162 on 2008-08-31
This is a great thread!!!!!

Thanks to unutbu's posts #2,3 and 4 I was able to fix my shutdown issues. I was having a very similar issue with my old Compaq Persario. Xubuntu would go through the shut down procedure and get to that last screen just like the other user. The HDD would shut down and so would the fans but the screen would remain on with that last screen. Editing the files like unutbu said worked perfect the first time. 

I want to add that when I'm booting into Xubuntu there is a message of some kind stating something to the effect of "bios date (1999) requires 2000 forcing acpi" This is way off from what it actually says but I'm sure some one that knows better will understand this. 

Another note.... Windows XP on this same machine had the same issue, is also a workaround withing XP that resolved this issue as well.


Thanks once again.

---

### Post by DetroitLibertyPenguin on 2008-10-30
I know this post is several months old. But I had similar issues, and was able to resolve it more simply. 

from terminal i entered sudo shutdown now

once this activity was created I chose the fix X option

It ran some scans, then posted a message about needing to reconfigure the x11/xconfig file and that I may loose some custom settings. 

now all is well (except the scroll buttons on my trackball don't work anymore, but if its a trade off, its a good one). Though any insight on this would be well appreciated

---

### Post by errorxp on 2009-02-13
long story short...

use

*acpi=force*

it solved my shutdown issues

---

### Post by ddmdllt on 2009-02-13
> **botokely said:**
> Just to say that I've the same problem SOMETIMES with my EEE PC (not exactly the same problem but it is analogue, I think).


Not sure at all that it is the same causes.

Did you have a look at [https://help.ubuntu.com/community/EeePC/Fixes#Shutdown]("https://help.ubuntu.com/community/EeePC/Fixes#Shutdown") ?  This is a frequent problem for eeepc users, there is something wrong with a module remaining active (snd-hda-intel, related to the sound system).

Hope this helps,

David

---

### Post by kerry_s on 2009-02-13
look at the thread dates. ;)

---

### Post by errorxp on 2009-02-13
yes i know it's an old thread but the problem is still the same isn't it so why create a new one.

---

### Post by ddmdllt on 2009-02-13
Oops : kernel failure : looked at the "last post" date but not at the date of the message I quoted/answered ;)

---

