---
title: "Suddenly... the ram was not recognised"
date: 2013-10-07
forum: Hardware
---

### Post by piteur on 2013-10-07
Hi everyone,
I have a problem since a few days ago. A few months ago I bought a new PC , the processor is a 6x AMD FX-6300 Six-Core processor, with 15GB RAM (yes, I haven't saved money in hardware). Among the programs and utilities being installed, I installed prey ( preyproject.com ), a small program for computer tracking in case anyone steal it. I installed it and I have configured in prey control panel (all ok). I do need my computer always awake, even at night, even for several days in a row and my old pc never had any problems (surely the problem is not ubuntu).

So far so good, the pc is very fast and I'm satisfied with the purchase, if only for a few days, even if there is no one sitting in front of the screen, the computer restarts. I get a report on the panel of prey indicating that the hardware has been changed, by two ram modules to zero.
[IMG]http://thejoe.it/img/ram.png[/IMG]

Im using Ubuntu 13.04, my computer is a tower pc (not a laptop).

I've never had a problem like that, and I do not know how to fix because I have no idea what caused it. Any idea?

---

### Post by Copper_City on 2013-10-07
I would see if the ram is actually changing via the OS or BIOS, Maybe there is a bug or problem with the ram and/or mobo. If it's not dropping off via the BIOS or OS. I would suggest you have problem with the program itself.

---

### Post by piteur on 2013-10-07
Just to be clear... the ram now is working...

I see 15gb ram (which is ok) before and after the computer reboots itself. I will try to clean the ram pins this night and see in theese days if it happens again.

Is there a way to check for errors on the ram in linux?

---

### Post by sanderj on 2013-10-07
> **piteur said:**
> 

Is there a way to check for errors on the ram in linux?

Yes: it's in the GRUB boot menu (immediatly after the BIOS boot): "memtest86+".

... but my guess there is no problem in your RAM, but in the prey application / detection.

---

### Post by piteur on 2013-10-08
Okk, i've run memtest86+ from a live usb key (i had no entry like that in the GRUB menu). It cycled 4 times and found no errors. I'm also testing the RAM with memtester, no errors till now... so i'm guessing the RAM is ok.

I've run prey right now, it seems that there were non problems (the computer is still on, no malfuncions till now).

So I went in prey's settings to see what it does while checking for the ram... here's the interested lines of code:

```
get_memory_info(){
        local mem_in_kb=$(cat /proc/meminfo | grep "MemTotal" | sed 's/.*:[[:sp$

        system__ram_size=$(($mem_in_kb/1024))
        system__ram_modules=$(dmidecode --type 17 | grep Size | grep -v "No Mod$
}
```

For what i can understand it just reads the ram...

Anythin else i can check?

---

### Post by sanderj on 2013-10-08
First check: can you run that code from the command line? I don't think so: the ' and the " are not terminated.

---

### Post by piteur on 2013-10-08
Yes, you can! Sorry, i copy-pasted from nano... Theese lines are the good ones..

```
get_memory_info(){
	local mem_in_kb=$(cat /proc/meminfo | grep "MemTotal" | sed 's/.*:[[:space:]]*\(.*\) .*/\1/')

	system__ram_size=$(($mem_in_kb/1024))
	system__ram_modules=$(dmidecode --type 17 | grep Size | grep -v "No Module" | wc -l)
}
```

---

