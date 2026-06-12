---
title: "Lenovo V100 laptop runs hotter in linux"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by k-zed on 2007-03-11
I have a Lenovo 3000 V100 laptop dualbooting Edgy and XP. This laptop was advertised as relatively cooler and quieter than other laptops, and in Windows, it certainly is. However, when in Ubuntu, it gets quite warm rather quickly, and the fans turn on often as well.

I'm running Ubuntu Edgy with the stock kernel (2.6.17-11-generic x86_64).

As far as I could gather from /sys/devices/system/cpu/cpu{0,1}/cpufreq, frequency scaling does work (available frequencies, it says, are: 1.833, 1.333, 1ghz; now and almost always it's using 1ghz; the current scaling_governor is ondemand).

/proc/acpi/processor/CPU{0,1}/throttling says <not supported>, I don't know whether this is supposed to be normal or not.

While this doesn't make linux unusable on this laptop (hardly.. I use it almost exclusively), it's certainly "uncool" and somewhat uncomfortable. I guess it also would affect battery life.

Has anyone any idea how to fix this?

Edit: forgot to say it has an Intel Core 2 Duo CPU.

---

### Post by tschneiter on 2007-03-11
I am running into the same problem on a dell 640m. I found that if I take out the battery and run only on AC, the situation improves dramatically. Maybe this can point you, or someone, in the right direction of what the heck is going on here.

---

### Post by tschneiter on 2007-03-11
Well, I just upgraded to feisty and my heat troubles are no longer plaguing me. You might want to give that a try!

Good luck,
-T

---

### Post by AdamWill on 2007-03-18
Hmm, hi from the enemy! :)

If you do:

ls /proc/acpi/fan

you will see nothing, right?

I am told (by no less than Keith Packard) that the problem is that a bug in either our laptop's BIOS (I have the same model) or the kernel prevents the kernel from seeing the laptop's fans, and consequently from controlling them. So they never spin up when things get hot.

This is what he recommended me to do:

(keithp) yeah, you can get the AML disassembler and look through your ACPI data then you can debug the fan driver in the kernel to find out why it can't see the stuff in the ACPI table

At this point I ran from the channel screaming.

I'm going to try and find a smart kernel person who will be comfortable doing this stuff.

Doesn't seem like it's a simple problem to fix, anyway.

I tried updating to the latest BIOS to see if that helped. It didn't, but on the plus side, it seems to have massively increased the screen's brightness level when running on AC...

---

### Post by k-zed on 2007-03-30
Yep, there's nothing in /proc/acpi/fan.

Looks like our only option will be waiting for a Smart and Brave Kernel Person to fix this...

BTW, I upgraded to feisty too and the heat problem is as before.

---

### Post by Ariccanfly on 2007-04-04
Mine too, wtf is this im a dead man if my computer fries.

Mu gpu was at 115c when i got back, others please post your temperatures, you can see them with kgrellm, press f1 for configuration...


Should i go back to windows... well its broken from some update, and anyways and i dont want to! PRIORITY bug guys pleeease fix this!!!!!

My lappy is a hp dv2120ca..

---

### Post by cmavr8 on 2007-04-11
My temperatures are almost always below 70 degrees celcius.

Exception: [http://ubuntuforums.org/showpost.php?p=2430130&postcount=12](http://ubuntuforums.org/showpost.php?p=2430130&postcount=12)

---

### Post by krazyd on 2007-04-11
Actually guys a bug in the BIOS of your computer is, by definition, not a bug in the kernel.. :KS 

Read all about the real problem here:
[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)
[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

Now, apparently the latest feisty kernel has the custom DSDT patch applied. Search the bugs on launchpad for more info.

Unfortunately I wasn't able to find a custom DSDT for any of your laptops... :(

Also, I haven't actually tried using a custom DSDT (though my lappy has a couple of power-related bugs which I suspect might be fixed by this)

hope the info helps! :)

---

### Post by nicksukharev on 2007-04-11
> **k-zed said:**
> Yep, there's nothing in /proc/acpi/fan.

I have nothing in this folder either and my laptop (Dell XPS m1210) seems to control fans OK. It certainly gets warm sometimes but then it does this under windows also. What is controlling my fans? :)

---

### Post by AdamWill on 2007-07-04
For krazyd, I'm pretty sure the problem here is not the DSDT: I checked it, and it contains only one error and a few warnings. I fixed the error, but with the fixed DSDT, the fan behaviour is no different. I don't know how to fix the warnings but I don't think they relate to this issue.

For the others experiencing this problem, I finally got tired enough of it to file an upstream bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=8713](http://bugzilla.kernel.org/show_bug.cgi?id=8713)

please feel free to add your experience there, but only if you actually have the same laptop model (lenovo v100). thanks.

---

### Post by cmavr8 on 2007-07-04
I have the V100  0763-44U model s/n and it does not go higher than 85 degrees Celcius.

The problem is serious, though, when you have it on your lap! It gets HOT!

---

### Post by AdamWill on 2007-07-04
You can't get it to hit 100 unless you put it under heavy load for a few minutes - for me it usually hits 100 and shuts down if I try to build something that takes longer than two or three minutes. Also, I'm in a very hot room =) But yeah, it shouldn't be going over 80 anyway. We're probably shortening the life expectancy of various components quite a bit.

---

### Post by k-zed on 2007-07-05
Actually mine never goes above 70-80-ish, even under sustained load. The situation even got perceptably better with gutsy. Still worse than in Windows, though.

---

### Post by AdamWill on 2007-07-05
That's interesting, actually. What's the temperature of the room you're in? Do you actually notice the fans spinning faster? Have you checked what speed the CPUs are running at? Maybe they're always being throttled to the lowest speed, or something. If I force the system to throttle the CPUs to 1GHz (instead of 1.667GHz) permanently, then I can keep it under 100...

---

