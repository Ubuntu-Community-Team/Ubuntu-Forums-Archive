---
title: "Crazy heat problem"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by k0rv3n on 2007-04-23
HELP!!

I have a Toshiba P100-208 with a Geforce Go 7600 512Mb

I have installed gkrellm to monitor the temps on my comp since it seems to get hot using linux, the fans dont seem to start at all and the temp I read in gkrellm is 74 C !!!!

Is there anything I can do to controll the fans?

---

### Post by k0rv3n on 2007-05-08
bump... really need help.
Somtimes the screen gets all scrambled for a few seconds and I think it's beacuse of the heat on the GPU

---

### Post by jjordan on 2007-05-08
K0rv3n,

Are the fans coming on?  If you can hear them then the problem is likely dust in the heat sinks.  Turn it off and blow hard through the opening the fan forced air comes out of.  If you see a cloud of dust you have probably fixed it.

If the fans are not kicking on see if you **fnfxd,toshet and tosutils installed**.  Those programs allow you to control the fan.  Another thing you should look at is CPU frequency scaling it can save a lot of heat and prolong battery life.

-j

---

### Post by dmizer on 2007-06-05
in /proc/acpi ... is there a "toshiba" directory?

if so, you can manually start the fan with this command:
sudo echo "force_on:1" > /proc/acpi/toshiba/fan

---

