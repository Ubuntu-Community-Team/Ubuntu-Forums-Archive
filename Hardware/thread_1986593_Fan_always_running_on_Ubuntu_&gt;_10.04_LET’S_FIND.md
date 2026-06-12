---
title: "Fan always running on Ubuntu &gt; 10.04: LET’S FIND A SOLUTION!!!"
date: 2012-05-25
forum: Hardware
---

### Post by Ualpa on 2012-05-25
*Another post on this issue that affects many systems and, as far as I know, has not been solved yet.*

I’ve been running Ubuntu on my current notebook (DELL Studio 15 with ATI Radeon HD 3450) for years, since 8.04, always upgrading to the newest version as soon as it was available.

With the installation of ATI restricted drivers, the notebook has always been silent with the fan running only when needed. But in all the versions newer than 10.04 (or maybe 10.10, sorry but I can’t remember for sure), it seems there is no way to keep the fan from running all the time.

Recently I made a test installation of Precise on this same machine and the problem persists.

Say there are 3 fan speeds: speed 0, 1 e 2.

10.04 without ATI restricted driver > speed 2
10.04 with ATI restricted driver > speed 0  :)

12.04 without ATI restricted driver > speed 2
12.04 with ATI restricted driver > speed 1  :(

I tried to see if the problem is actually temperature (that is what fans are there for) and these are the values (just after boot, no programs running):

10.04  > temp1: +40.0°C, temp2: +42.0°C , temp3: +54.0°C
12.04  > temp1: +41.0°C, temp2: +44.0°C, temp3: +58.0°C

So no real difference, and if you consider that in this very moment on 10.04 - with temp1: +58.0°C, temp2: +52.0°C, temp3: +60.0°C - the fan is not running, I would say that it is not a problem of temperature.

In these years I tried several methods to solve this problem: no restricted driver, restricted driver via the Ubuntu repositories, restricted driver from the ATI website, and a number of other possible settings and workarounds, but none of them solved the issue.

So now I’m not even sure about the nature of the problem, if it is actually related to the graphics driver, or to power management, or what else...

Please share your experiences and, if any, possible solutions!

---

