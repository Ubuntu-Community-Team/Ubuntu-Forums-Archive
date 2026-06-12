---
title: "fullscreen on 13.10 with radeon 7870"
date: 2013-10-23
forum: Hardware
---

### Post by mark541374 on 2013-10-23
So I have a new machine and it features a readeon 7870 for graphics. I installed 13.10 64bit and everything looked nice and normal but trying to run anything with graphics was terrible. The system testing utility confirmed that the card was not active so I switched to the proprietory fglrx drivers. They both work in terms of the graphics card passing the tests and graphics applications running well, but the desktop is not actually using all of the screen. The system settings say it's running at 1920x1080, and it is using the full resolution in the area it's in, but there ishalf an inch of unused space around the outside of the desktop.

So... are there any drivers that do work with 13.10? or is there a fix to get the full screen? or would it be worth trying 12.04?

---

### Post by mark541374 on 2013-10-23
So it's apparently something called underscan that was causing the fglrx drivers not to use all the screen. No idea about how to fix the default driver but to fix the underscan on fgrrx I did:

```

[FONT=arial]sudo amdconfig --initial
[SIZE=2]sudo amdconfig -set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
sudo reboot[/SIZE][/FONT]

```

---

