---
title: "How can I make Ubuntu more efficient for my laptop?"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by OpticalIllusion on 2006-09-29
So, I notice that Windows makes my laptop run a lot cooler and gives me a lot more battery life.  Reasons for both of those are an easy-to-use i8kfangui and Notebook Hardware Control to undervolt my CPU.  Is there anyway I can undervolt my CPU or set it up to only run on the lowest multiplier when on battery power?  Is there maybe I way I can use Wine to install Notebook Hardware Control?

Is there any graphical version of i8kfangui?

---

### Post by BitTorrentBuddha on 2006-09-29
I believe the CPU Frequency Scaling Monitor panel applet lets you scale it. Not sure though. Give it a try.

---

### Post by OpticalIllusion on 2006-09-29
> **BitTorrentBuddha said:**
> I believe the CPU Frequency Scaling Monitor panel applet lets you scale it. Not sure though. Give it a try.
I thought it might too, but how do I do it?  I tried to double click it and right click on it and clicked  Preferences and I don't see an option anywhere.

EDIT:  Nevermind, found a How To and got it enabled.

Now, is there any form of a graphical i8kfangui for Linux?

---

### Post by NooneReally on 2006-09-29
left clicking on the appplet gives me the option of explicitly setting the frequency. Otherwise the system manages the scaling just fine. The setup for that was handled automatically by the 6.06.1 installation.

For the i8kfan issue, I have a policy file setup which governs when the fans go on/off. There is no need for any gui of any sort. 

the file is called .i8kmon (place in home directory) and mine looks as such:

```

set config(0) {{- 0}  -1  30  -1  35}
set config(1) {{- 1}  25  50  30  55}
set config(2) {{- 2}  45  70  45  75}
set config(3) {{- 2}  60 128  65 128}

```

first column is fan speed, second/third are plugged in threshholds, and fourth/fifth columns are battery thresholds...set as you wish.

Gnome sensors applet will then display the core temps and any fan rpms it can detect. You might have to figure out what the multiplier is though so the rpms display at the correct rate...my multiplier is 0.034

---

### Post by OpticalIllusion on 2006-09-29
Well, I got i8kfan a setup to be a little easier to use now.

I set up 3 buttons on my top panel that do the following commands:

```
i8kfan 0 0
```
Wich turns both fans off.
```
i8kfan 1 1
```
Turns both fans on low.
```
i8kfan 2 2
```
Turns both fans on high.

I think it's a decent setup.  This way I have full control over when I want my fans to run and on what speed to run them at.

Now, if only there was a program that allows me to undervolt my CPU for less heat and more battery. :-k

---

### Post by NooneReally on 2006-09-29
full control but you better not forget to turn them on high if you leave your machine running with any load...i wouldn't like to see what happens with no fans and a full load.

now that i think about it, frequency scaling might be handled by powernowd...so make sure that is running.

---

### Post by Old Pink on 2006-09-29
Edgy is apparently set to include some fancy battery monitoring features, you should try installing that on a partition?

---

### Post by ltmon on 2006-09-29
There are some kernel patches that allow CPU undervolting (see [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)).  I think they might be in the Edgy kernel, but I'm not at all sure.

L.

---

### Post by OpticalIllusion on 2006-09-30
> **NooneReally said:**
> full control but you better not forget to turn them on high if you leave your machine running with any load...i wouldn't like to see what happens with no fans and a full load.

now that i think about it, frequency scaling might be handled by powernowd...so make sure that is running.
Unless i8kfan for Linux works differently than the version for Windows, the fans will still come on without me turning them on manually.

The fans are still controlled by the BIOS, I'm pretty sure.

> **ltmon said:**
> There are some kernel patches that allow CPU undervolting (see [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)).  I think they might be in the Edgy kernel, but I'm not at all sure.

L.
Awesome, thanks.  I'll give that a try tomorrow, if I get time.

---

### Post by OpticalIllusion on 2006-10-02
> **ltmon said:**
> There are some kernel patches that allow CPU undervolting (see [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)).  I think they might be in the Edgy kernel, but I'm not at all sure.

L.
It appears that I don't have a compatible kernel to use the patch with.  I have the 2.6.15-27-386 kernel.  Where can I get one of the compatible kernels?  I don't see one in the Synaptic Package Manager. :-k

```

Kernel Flavor | Kernel Version | Patch          | Status

Ubuntu        | 2.6.15-26.45   | ubuntu-2.6.15  | Clean
                 |------------------------------------------
                 | 2.6.17-5.15    | ubuntu-2.6.17  | Clean

```

---

### Post by OpticalIllusion on 2006-10-05
Anyone know where I can get these kernels in the list above?  I don't know if I should go ahead and attempt to patch the my current kernel or not.

---

### Post by iam_foo on 2006-10-05
i use gkrellm for my fan control ..it has an i8k plugin that lets you control the fan automatically according to temp,
say if you wanted to leave it unattended with a load working
once it hits a certain temp the fans adjust..or manually where each fan has a GUI with 3 click options  off/low/high. works great..it also tells you the speed of your fans in rpms.

---

