---
title: "Monitor max resolution not supported on ubuntu 15.10"
date: 2016-02-04
forum: Hardware
---

### Post by bacmsantos on 2016-02-04
Hello everyone,

I am struggling to use the maximum resolution of 1920x1200 on my iiyama ProLite E2607WS. This seems to be a edid issue as the screen appears listed as being a prolite 25'' not 26''. 

I have tried the usual xrand solution but it does not seem to work
```

:~$xrandr --output VGA1 --mode "1920x1200_60.00"xrandr: Configure crtc 0 failed

```

Does anyone has any idea how to solve this? so far my google-fu has failed to provide with any working solution

Forgot to add I am using the intel cpu integrated graphics 
```

:~$ sudo lshw -c video  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by Vladlenin5000 on 2016-02-04
Hi and welcome.

What connection are you using? I hope not the old VGA as modern digital equipment works better with digital connections, DVI, HDMI, DisplayPort, of wich your Iiyama has the first two. Choose either one and you should be fine.

---

### Post by bacmsantos on 2016-02-04
Unfortunately the motherboard only supports the VGA connection so yes I am using VGA

---

### Post by Vladlenin5000 on 2016-02-04
I'm sorry I cannot help you with it - hopefully somebody else will - because I stop using old graphics with new monitors almost a decade ago. 
My only suggestion would be to upgrade your hardware and that's probably something you don't want to do...

Good luck.

---

### Post by bacmsantos on 2016-02-05
> **Vladlenin5000 said:**
> I'm sorry I cannot help you with it - hopefully somebody else will - because I stop using old graphics with new monitors almost a decade ago. 
My only suggestion would be to upgrade your hardware and that's probably something you don't want to do...

Good luck.

And you conclude this was old hardware based on? It is new hardware less than half year old. This is an office computer provided by Dell and unfortunately they don't include any other port.

---

### Post by Vladlenin5000 on 2016-02-05
> **bacmsantos said:**
> This is an office computer provided by Dell and unfortunately they don't include any other port.

Please post the model and/or specs.
I would be really surprised if any current Dell desktop doesn't come with HDMI, including entry level office desktops. As a matter of fact what I see from all manufacturers is the opposite, i.e., they no longer come with VGA.

---

### Post by bacmsantos on 2016-02-12
It's a Dell Optiplex 9020
From the top of my head it has a i5 4690, 16GB of RAM and no external graphic card which is why no DVI or HDMI port is present

---

### Post by Vladlenin5000 on 2016-02-12
I'll be damned, you were right all along: The entry level mini tower Optiplex 9020 has VGA only (additional HDMI is optional) and is a current model. The problem is the old Intel integrated graphics; any newer Intel HD graphics, also integrated, comes with digital ports. As such, all the other 9020 variants, including those with the same form factor, have it.

Again, I'm not the one who can help with xrandr, arguably your only chance to make a proper resolution match for the monitor, of which I know nothing, never needed to use it. I hope someone else with experience comments here.

---

