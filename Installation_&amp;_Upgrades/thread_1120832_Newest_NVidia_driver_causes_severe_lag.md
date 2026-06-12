---
title: "Newest NVidia driver causes severe lag"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by The Clown on 2009-04-09
Hi,

I know NVidia is a proprietary, closed-source driver, but I was wondering if anyone could shed some light on this issue.

Today, I installed the newest version of the NVidia driver (v. 180), and after the reboot, my laptop started lagging significantly when I would do things like switch workspaces or minimise a window. A few times, I thought it was locked up and was ready to reboot when it started moving again.

Is this an issue with NVidia, or is Ubuntu (using Intrepid) not built to handle the newest driver yet? Or is it a hardware issue on my part? I can provide any hardware specs you need to see if that's the problem.

It's not a super big deal, as after I rolled the driver back to a previous version everything started working fine again, but it's that mentality of "MY DRIVERS AREN'T CURRENT! AAAHHHHH!" that's getting to me.

EDIT: Come to think of it, this may be an issue with Compiz. The computer would only really lag when it was doing something that involved a Compiz effect.

---

### Post by upchucky on 2009-04-09
open a terminal then do this

```
glxgears
```

you should see frame rates of 11,000fps or more

if not then nvidia is not set up right.

---

