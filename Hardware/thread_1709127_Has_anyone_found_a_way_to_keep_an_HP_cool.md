---
title: "Has anyone found a way to keep an HP cool?"
date: 2011-03-17
forum: Hardware
---

### Post by AliceKingsley on 2011-03-17
I have an HP tx2500, and it gets hot enough to crash multiple times a day. 

I have spent days trying to find a solution, but every other thread dead-ends with "Yea, me too."

This appears to be an issue for HP laptops across the board, but here are details: 
HP tx2635us running Kubuntu 10.10 64bit

The folder that should have a fan setting file (/proc/acpi/fan/) is empty. [This thread]("http://ubuntuforums.org/showthread.php?t=1631519") got me to look in that folder. 

I found [this guide]("http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu") to lm-sensors. I installed it, but it's not helping. Here's what I'm getting:

sudo sensors:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +78.0°C                                    

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +82.4°C  (high = +70.0°C)
```

sudo pwmconfig:

```
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

I can't get any farther on my own. Any help would be awesome.

---

### Post by azzamite on 2011-03-17
Hi AliceKingsley
I did various thing:
1 - Installed the bios update from hp since there was a bug with the fan (the app says its dangerous so do it at your own risk)
2 - Bought an external laptop fan (there are of all sizes)
3 - Sacrificed a little performance lowering the maximim cpu frequency of my processor

The first and third points are what worked for me. I elaborate only in the third which has worked alone (the lower the frequency of your processor the cooler it gets).

First check the "steps" of your processor (you may need to install cpufrequtils)
```
me$ cpufreq-info | grep steps
  available frequency steps: 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
```

I decided 1.60GHz was enough for me, so I put it to be the maximim working speed:
```
me$ sudo cpufreq-set -u 1.6gh
me$ cpufreq-info | grep current
  current policy: frequency should be within 800 MHz and 1.60 GHz.
  current CPU frequency is 800 MHz (asserted by call to hardware).
```

This configuration only lasts until you reboot your laptop, so you have to call cpufreq-set every time (or put the command in the init script).

Hope this helps

---

### Post by tgalati4 on 2011-03-17
Perhaps there is too much thermal paste on the heat sink.  Too thick a layer will interfere with heat transfer to the cooling fins.  Sounds like a manufacturing error.

---

### Post by AliceKingsley on 2011-03-18
Thanks for the reply. Running at 550MHz it's still hot to the touch, so could you please explain how to update the bios? (All I can find is an .exe, and I don't dual-boot.)

---

### Post by Favux on 2011-03-19
Hi Alice,

I'm not sure /proc/acpi/fan/ is suppose to be populated anymore.  Wasn't there something about reading from the kernel starting with Lucid?

Anyway with:
> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
have you checked if *lm-sensors*, and *libsensors*, and *fancontrol* are installed.

---

### Post by AliceKingsley on 2011-03-19
Favux, all three are installed. 

I would be perfectly happy if I could just turn the fan on high manually, for the record. 

Thanks again for the suggestions.

---

### Post by AliceKingsley on 2011-03-20
When I restarted my computer I noticed that in the few seconds before Ubuntu booted up, the fan was running just fine. Once it started booting up the fan turned off. 

azzamite, can you give me some info on updating my bios? I found threads on it, but there are half a dozen ways to try, and the one you used would probably have a good chance of working for me.  

In the mean time, what is a safe temp? I can use lm-sensors to check the current temp, so at what point should I turn it off to avoid damage? (For example, 82 degrees C seems too high, but is a very common reading.)

---

### Post by AliceKingsley on 2011-03-21
Any ideas on why the fan only works while the OS isn't running? Would this mean I need to mess with the OS itself? (And if so, is there a way to revert to 10.04 w/o wiping my hard drive?)

Any thoughts would be appreciated. I'm frustrated & confused at this point, and I just can't figure this out on my own. I can't use my computer the way I could 3 months ago, and I don't know why. (It took me a while to realize that there is something really wrong, rather than just the normal heat issues this laptop is known for.)

---

### Post by Favux on 2011-03-21
I'm assuming you used canned air and blew out any dust bunnies in fan etc.

If I didn't know better I'd think you have an old DSDT bug that was fixed with a BIOS update.  The only real safe way to update the BIOS is through Windows.

Have you tried any of the DSDT kernel command-line options?  Sometimes those work.

---

### Post by AliceKingsley on 2011-03-21
Favux, it's definitely a problem with the fan speed. You can hear that it doesn't ever speed up. (I can't tell for sure whether it's off or just very low. There is a little bit of noise, but it is soft & constant, could just be the rest of the computer running.)

I don't know anything about DSDT, and the brief search I did wasn't helpful. I'll look harder, but if you want to be really fantastic and explain I'll be eternally grateful. 

[I also wanted to mention that I have been actively looking for the answers to my questions throughout the forums and the internet as a whole. I'm just not an advanced enough user to be able to sort it out.]

---

### Post by Favux on 2011-03-21
Well they don't let us fix the DSDT and use a customized DSDT anymore.  But 67GTA's old thread is still active.

The command line options I was thinking of are like this:
```
acpi_osi="!Windows 2006"
acpi_osi="Windows 2006"
acpi_osi="Linux"
acpi_osi="Windows 2001 SP2"
```
and I'd think you'd want the Linux one.

My command of Grub 2 is still shaky but I think you add a kernel command line option by doing:
```
sudo nano /etc/default/grub

```
Add to whatever's there:
```
GRUB_CMDLINE_LINUX="... acpi_osi="Linux" ..."

```
Then run:
```
sudo update-grub
```

---

### Post by AliceKingsley on 2011-03-21
I cannot thank you enough. My fan works! I can use my computer again!

I edited /etc/default/grub and changed 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\"
updated grub and rebooted, and the fan turned on as soon as it booted up.

---

### Post by Favux on 2011-03-21
Outstanding!  :)  My shot in the dark worked, lol.

Did you really use the two pairs of 3 backslashes in the added option?  If intentional educate me as to what they are for please.

---

### Post by Hedgehog1 on 2011-03-22
> **Favux said:**
> Outstanding!  :)  My shot in the dark worked, lol.

Did you really use the two pairs of 3 backslashes in the added option?  If intentional educate me as to what they are for please.


Isn't this is because of using "" inside ""?

The first two '\\' become '\', and the '\"' becomes '"', meaning '\"'.

But it still looks like too many '\'s.  But it does appear to work...  Hmmm...

***The Hedge***

:KS

---

### Post by Favux on 2011-03-22
Hi the Hedge,

That's what I was wondering.  Is Grub 2 doing that?

So do you need something like?:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='Linux'" 
```
To avoid the syntax error, or whatever it is that Grub may be correcting?

---

### Post by AliceKingsley on 2011-03-22
I tried it with ```
...=Linux
```and ```
...="Linux"
```with no luck. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1297008&page=5") which suggested adding all the slashes for Grub 2. The explanation given is just > the problem is that grub2 does not honor quotation marks without the \\\ added
Of course, I didn't have any clue about what Grub is until a day or two ago (and I still don't really know anything about it), so I really don't understand what I did. I just kept trying suggestions until something worked.

---

### Post by Hedgehog1 on 2011-03-22
steve161's orignal post from November, 2009 reads:
> 
This worked for me. Open /etc/default/grub as root. Look for the line that ends with quiet splash. Add acpi_osi=\\\"Linux\\\"" to the line so it looks like this
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
 
Then run sudo update-grub from the terminal.
 
I saw a similar parameter posted earlier, but the problem is that grub2 does not honor quotation marks without the \\\ added. Btw, I have a toshiba laptop and my fan now kicks in (quietly) at 56C and turns off at 42C. I found this after googling and some trial and error so I can not explain the logic behind this. Also, I am not sure this will give the user any direct fan control.
 
Later in that thread steve191 posted:
>  can't find the page where it discusses the reasoning behind the parameter, but here is a short explanation of the parameter and the change needed for grub2
 
[[COLOR=#444444]http://forums.linuxmint.com/viewtopic.php?f=60&t=18222[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=60&t=18222")
 
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...b2/+bug/411597[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/411597") 
 
Lots of folks running 10.10 on laptops have noticesd hotter CPUs. This is an Awesome find **Favux** & **AliceKingsley** - we need to share it with others.
 
But I have a little reading to do first....
 
***The Hedge***
 
:KS

---

### Post by Favux on 2011-03-22
Nice find The Hedge.  I completely missed Steve161's posts as I'd guess Alice did.  I suppose because they were about a Toshiba.

Anyway that fits.  To make Grub 2 accept quotes in a quote you preceed it by \\\.  So the correct syntax becomes:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

```
But that still leaves by original question.  Does a single ' quote work.  Like it would in Python or whatever?

---

### Post by AliceKingsley on 2011-03-23
I figure I should mention that while this did allow my fans to work at all, it still runs hot. Just not so hot that I have to shut it down. (Not a huge problem, just info for anyone else trying to fix this issue.) I can keep it under 80°C, which seems to be the best I'm going to get. 

I tested the single quotes. The temp seemed to drop more slowly, but to be sure I'd have to try it again.

---

### Post by AliceKingsley on 2011-04-30
I updated to 11.04, hoping that whatever changed between 10.04 and 10.10 to f*ck up my cooling system would have been changed back. No such luck. Minecraft took me to (I really, really hope this is wrong) 99.6&#7506;C. 

I followed the steps in [this thread]("http://ubuntuforums.org/showthread.php?t=1287819&highlight=fancontrol") because it's about k10temp, which seems to be my driver: ```
alicekingsley@CheshireCat:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C                                    

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +62.9°C  (high = +70.0°C)                  

```
No change. 

Anyone come up with any new solutions? I looked at the grub file I changed before, and it's the same as I left it. As always, I'm willing to try just about everything. Let me know if there's more information that would be useful. Thanks.

P.S. I've seen quite a few threads about making fans quieter; as long as they work, I don't care how loud they are.

---

### Post by iForce1 on 2011-04-30
I had the same problem with temperatures in Natty, but after installing ATI driver Catalyst 11.4 everything is ok now.

---

### Post by AliceKingsley on 2011-05-05
Thanks, iForce1. That helped a bit. Seems like there must be a few *different* cooling issues. I just need to keep chipping away at it. 

Anyone know how to find out what temp I can go to w/o risking damage? I try to keep it under 90&#7506;C, but if I want to run anything that uses my graphics card, the best I can do is hover around 95&#7506;C. The highest it's gotten (that I know of) is 101&#7506;C. (I now have xsensors sitting on my desktop so that I can keep track.)

---

