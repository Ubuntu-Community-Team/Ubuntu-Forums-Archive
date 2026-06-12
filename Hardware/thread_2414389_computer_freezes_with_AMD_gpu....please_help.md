---
title: "computer freezes with AMD gpu....please help"
date: 2019-03-09
forum: Hardware
---

### Post by kashei on 2019-03-09
i have a little problem :))  my computer freezes randomly after inactivity sometimes after 3 min, sometimes after few hours, i might go for days without a freeze and then starts doing it every couple of hours.....the way i would get around it is to go to TTY mode before i leave, but for the past couple of times it even started freezing in TTY which is very strange, 
i've tried a few things that could find on google...playing around with screen saver...power safe mode (i have desktop).....switching between opengl2.0 and 3.1...tearing prevention and few other things 

im running kubuntu, but i tried ubuntu with gnome, arch, 

and the problem only happens with  AMD GPU ... with nvidia gpu never had that issue 
and i tried with original mesa drivers (amdgpu) that come with ubuntu and i tried  with amdgpu-pro drivers....nothing helps 

PLEASE HELP 

P.S. 
one more thing, one time when my pc froze and i couldn't use my mouse or keyboard i had d a KDE connect open on the phone and i was able to move cursor and open folders,basically i was using phone as a touchpad, but after about 30 sec it froze on me too 


im running amd 1700x 
amd vega 64

---

### Post by QIII on 2019-03-09
Hello!

It might be helpful if you specified the model of the GPU.

Cheers!

---

### Post by kashei on 2019-03-09
right now i have vega 64......i had same issue with rx580

[FONT=monospace][COLOR=#000000]sudo lshw -C video[/COLOR]
```

  *-display                  
       description: VGA compatible controller
       product: Vega 10 XT [Radeon RX Vega 64]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:72 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe600000-fe67ffff memory:c00
00-dffff

```[/FONT]

---

### Post by mastablasta on 2019-03-11
what is the temperature? is the fan spinning when it freezes?

you can monitor temp using psensor.

i saw that sometimes after inactivity the fan doesn't spin back up. while at other times it works OK. but this is on very old chip. 

however lately after replacing the inside fan and later replacing the PSU it all works well.

edit: also check all the logs after it freezes, to see if anything unusual was happening or if there are any error messages.

---

### Post by kashei on 2019-03-11
> **mastablasta said:**
> what is the temperature? is the fan spinning when it freezes?

you can monitor temp using psensor.

i saw that sometimes after inactivity the fan doesn't spin back up. while at other times it works OK. but this is on very old chip. 

however lately after replacing the inside fan and later replacing the PSU it all works well.

edit: also check all the logs after it freezes, to see if anything unusual was happening or if there are any error messages.


i have fancontrol installed so it keeps gpu around 30-35 degrees, so basically fan is always spinning 
ill check the logs next time it freezes (it hasn't happen in couple of days)

---

### Post by kashei on 2019-03-28
so it started to freeze again.  In the past couple of day it froze a few times after inactivity 

here is the log file before it froze 

```


[FONT=monospace][COLOR=#000000]Mar 28 10:30:28 kashei-1 systemd[1]: Started Daily apt download activities.[/COLOR]
Mar 28 11:02:41 kashei-1 systemd[1]: Started Run anacron jobs.
Mar 28 11:02:41 kashei-1 anacron[23478]: [COLOR=#000000]**Anacron 2.3 started on 2019-03-28**[/COLOR][COLOR=#000000][/COLOR]
Mar 28 11:02:41 kashei-1 anacron[23478]: [COLOR=#000000]**Normal exit (0 jobs run)**[/COLOR][COLOR=#000000][/COLOR]
Mar 28 11:17:01 kashei-1 CRON[24740]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 28 11:17:01 kashei-1 CRON[24741]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 28 11:17:01 kashei-1 CRON[24740]: pam_unix(cron:session): session closed for user root

```

can someone help please[/FONT]

---

### Post by AnotherBrian on 2019-03-28
your bios may record events.  check to see if there are any thermo events.

---

### Post by kashei on 2019-03-28
> **AnotherBrian said:**
> your bios may record events.  check to see if there are any thermo events.



its dual boot machine when im in windows it runs fine 
and actually my amd card runs hotter on windows then on ubunutu

---

