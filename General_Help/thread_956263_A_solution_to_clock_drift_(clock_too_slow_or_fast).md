---
title: "A solution to clock drift (clock too slow or fast)"
date: 2008-10-23
forum: General Help
---

### Post by rak6502 on 2008-10-23
Over the years, I have clock problems with various Linux distributions and a variety of hardware. I see this issue addressed many times with an answer that the CMOS battery should be replaced. This is not necessarily the problem, and since I just addressed this issue yet again, I'd like to help anyone out there who might be misled. 

Here's the solution, which I've had to use on multiple distributions/versions/kernels and with various hardware; both AMD and Intel processors. This assumes you use grub (which is the default for Ubuntu)

Open **/boot/grub/menu.lst** and look for the kernel section, which looks something like this:

[FONT="Fixedsys"]title           Ubuntu, kernel 2.6.20-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-17-generic root=UUID=4a2fee06-6ef5-491d-8113-576b465998ed ro quiet splash
initrd          /boot/initrd.img-2.6.20-17-generic
quiet
savedefault
[/FONT]
On the end of the kernel line, I change it by adding **clock=tsc**, so the kernel line is now:

[FONT="Fixedsys"]kernel          /boot/vmlinuz-2.6.20-17-generic root=UUID=4a2fee06-6ef5-491d-8113-576b465998ed ro quiet splash [COLOR="Blue"]clock=tsc[/COLOR]
[/FONT]
Save **/boot/grub/menu.lst** with this change, then reboot. No more clock problems.

I should also mention that if this doesn't work for you, here is another kernel line modification that has worked for me in the past:

[FONT="Fixedsys"]kernel          /boot/vmlinuz-2.6.20-17-generic root=UUID=4a2fee06-6ef5-491d-8113-576b465998ed ro quiet splash [COLOR="Blue"]noapic nolapic[/COLOR]
[/FONT]
I believe that **clock=tsc** is a better option than **noapic nolapic**, but both have worked for me in every case.

[COLOR="Red"]The kernel line in the above examples are for my setup, your UUID will be different and your kernel might be different. The only change is the option(s) added to the end of the line.
[/COLOR]
More information:

When my clocks have drifted, I've experienced drifting ranging from 5 to 20 minutes per hour. It's good to get ntp running to constantly sync with a timeserver, but when you have too much drift, it seems that ntp cannot compensate. I've seen ntp offered as a solution, but it's only good once you fix the root problem. Once you implement this fix, ntp keeps things perfect.

It's important that I also mention that when a kernel is updated, **/boot/grub/menu.lst** is modified to reflect the new kernel. Because this line is modified, this change is lost, and must be put back in place. I'm sure somebody can chime in and mention a better way to do this, so the change is retained. I just haven't had the time to look into it.

Finally, I want to mention that I'm surprised that I've encountered this problem so often. Especially the most recent time, which was with a genuine Intel motherboard with a Core 2 Duo processor. I'm not sure why this issue isn't caught in testing and dealt with. Not complaining, just genuinely curious.

If anybody has anything to add that will help people, please feel free. It's been a frustrating issue to deal with, so I hope this is helpful to others.

---

### Post by PocketDog on 2008-10-23
Bugger all that, what Gnome needs is a fuzzy clock.[quote=Gnome Fuzzy Clock]"It's nearly 6pm or thereabouts"[/quote] That would do me lovely.

---

### Post by smcleish on 2008-10-24
> **rak6502 said:**
> It's important that I also mention that when a kernel is updated, **/boot/grub/menu.lst** is modified to reflect the new kernel. Because this line is modified, this change is lost, and must be put back in place. I'm sure somebody can chime in and mention a better way to do this, so the change is retained. I just haven't had the time to look into it.

Instead of adding clock=tsc to each entry you want it to apply to, find the line

# defoptions=quiet splash

and add it there, to get

# defoptions=quiet splash clock=tsc

This defines what is appended to a new default boot option further down.

Similarly, alter the # altoptions line to add options to non-default boot options.

Then run

sudo update-grub

and these options will now appear at the end of each line. Part of the new kernel update process will run update-grub, so the new options will persist.

Cheers,
Simon

---

### Post by Yellow Pasque on 2008-10-24
I've read that using clock=hpet is the best option if the motherboard/BIOS supports it. I know my system often gives me a "clocksource tsc unstable" message, so I wouldn't want to use it for the system clock, and using apic for the clock should be avoided if possible. [http://kerneltrap.org/node/8306](http://kerneltrap.org/node/8306)

Use this command to check your available clock sources:
```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource
```

---

### Post by rak6502 on 2008-10-25
Thanks for the replies. I've put the options on a defoptions line. This is exactly what I was looking for, so now I won't have to worry about it changing when the kernel is updated.

As far as clock=hpet:

cat /sys/devices/system/clocksource/clocksource0/available_clocksource

for my system shows:

acpi_pm jiffies tsc

So, it looks like tsc is the best option available to me. Fortunately, it hasn't caused me any trouble. I'll keep hpet in mind for future machines.

Thanks again!

---

### Post by TransitMan on 2008-10-26
So I have both tsc and hpet listed from your code.
```
tsc hpet acpi_pm jiffies 
```
Which way would you suggest I use to make the alteration to my grub menu?

---

### Post by bttb on 2008-10-26
I have an nforce2 box that has a huge clock drift when Spread Spectrum is enabled in its BIOS. But this is a hardware bug (see this [link](http://www.uwsg.iu.edu/hypermail/linux/kernel/0410.1/1505.html)).

---

### Post by rak6502 on 2008-10-27
> **TransitMan said:**
> So I have both tsc and hpet listed from your code.
```
tsc hpet acpi_pm jiffies 
```
Which way would you suggest I use to make the alteration to my grub menu?

It sounds like since you do have hpet, you should give it a try.

---

### Post by derEremit on 2009-06-29
could it be that the default value for Ubuntu is HPET.

I just got this problem when i changed HPET to 64bit in BIOS.
because i thought that would be better since i'm using 64 bit Ubuntu.

---

