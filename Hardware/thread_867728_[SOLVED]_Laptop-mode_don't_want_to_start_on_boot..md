---
title: "[SOLVED] Laptop-mode don't want to start on boot."
date: 2008-07-23
forum: Hardware
---

### Post by piter_aspire5920g on 2008-07-23
Hello!

In laptop-mode.conf I chose to run laptop-mode either on bettery and AC.

```
#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=1
```

Also laptop-mode has runlevel 2,3,4,5 during the boot sequence. And it autmaticaly turns on when I use batteries.

But on AC the command:
```
cat /proc/sys/vm/laptop_mode
```

shows 0

What to do?

---

### Post by sdennie on 2008-07-23
There could be a number of things going on here.  First, /proc/sys/vm/laptop_mode is not the same as the init process laptop-mode.  The former being a kernel tunable that tries to group together disk writes and the latter being a script.  

Second, Hardy contains a package called pm-utils that is generally not well behaved and will probably clobber or ignore a lot of the settings you make in more traditional places.

To fix your problem, you can either look through /usr/lib/pm-utils/power.d/laptop-tools to change what you want or, you can simply run:

```

sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

```

That will disable the part of pm-utils that is causing you the problem.  You'll need to plugin and unplug your machine at least once before you see a change.

---

### Post by piter_aspire5920g on 2008-07-23
Wow! It works!

Could you tell me about the consequences of such changes? What did I do exactely?

---

### Post by sdennie on 2008-07-23
> **piter_aspire5920g said:**
> Wow! It works!

Could you tell me about the consequences of such changes? What did I do exactely?

The pm-utils package blindly overrides settings from laptop-mode or /etc/sysctl.conf so, by doing a chmod -x on the part of pm-utils that does that, you've just told pm-utils to stop running that script when the power is switched from AC to battery.  It's the least destructive way to do this because, at a later date, if you decide you want to re-enable that part of pm-utils, you can simply run the exact same command but substitute, "+x" for "-x".

---

### Post by esscrow on 2008-09-13
**vor,**
what do I actually switch off when I use your instruction? When I applied your proposal I have observed strange thing.  
After restart and 
```
cat /proc/sys/vm/laptop_mode
```
screen shows 2 however laptop behaved asif the set-up defined in laptop-conf (file located in /etc/lapop-mode/) were not applied. 

For example load cycle e.g. parking head and speed down of HDD increased dramaticly  although in my laptop-conf this parameter should not allow parking head and speed down at all.It means that laptop-conf was not upload or other configuration was used.I do not understand what configuration for laptop power management set-up was applied and from.

Another thing is also interesting. When I returned to the +x for pm-utils/laptop-tools and after restart command ```
cat /proc/sys/vm/laptop_mode
```shows 0.However, load cycle behaved as it was defined in /etc/laptop-mode/laptop-conf. Strange!:confused: 

Summing up what to do, where to search the answer? How to properly control laptop-mode and where to define power management parameters?

---

