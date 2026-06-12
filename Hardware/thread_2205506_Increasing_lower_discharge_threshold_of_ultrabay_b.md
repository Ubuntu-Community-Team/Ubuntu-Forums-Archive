---
title: "Increasing lower discharge threshold of ultrabay battery before switching Lenovo T43s"
date: 2014-02-14
forum: Hardware
---

### Post by andradx on 2014-02-14
Sorry for the long title. I have a Lenovo Thinkpad T430s with an Ultrabay battery and a main one. When I plug in the two batteries, it will start draining my Ultrabay battery until it drops all the way down to 0% until switching to the main battery. However, I want to keep the discharge within reasonable limits - 10~15% of capacity - before switching to the main battery. I want to enjoy more capacity without having to physically remove my ultrabay battery in order to preserve it.



According to [http://www.thinkwiki.org/wiki/Tp_smapi#Model-specific_status](http://www.thinkwiki.org/wiki/Tp_smapi#Model-specific_status), Ivy bridge Lenovo do not support tp_smapi which is used to implement a script called tp-bat-balance ([http://www.thinkwiki.org/wiki/Talk:Code/tp-bat-balance](http://www.thinkwiki.org/wiki/Talk:Code/tp-bat-balance)) that balances the usage of both batteries. I have installed tlp from [http://linrunner.de](http://linrunner.de), which allows some tweaking to the minimum and maximum charging thresholds, but not to the min discharging thresholds for the ultrabay battery.



Has anyone found a workaround this?

---

### Post by tgalati4 on 2014-02-14
I have a T43p with an Ultrabay.  I think it is hardwired in BIOS.  Perhaps look for a BIOS upgrade to see if there are any switches inside the BIOS.  I think the current settings are fine when the batteries are new, but when the batteries get old, the hand-off can be risky.  IBM/Lenovo's solution is to buy new batteries.  The battery's charge and monitoring circuitry is quite sophisticated, but if one cell has started to degrade, the entire battery pack becomes a liability for your data.

You could write a script using *notify-send* to check the battery level (every 10 minutes) and give more advanced warnings at 20% so you can save your work and prepare for the switchover.  Then use *acpitool* to eject the Ultrabay device at 15%.  I would try this a few times to make sure that the handover is clean.

```
man acpitool
```

---

### Post by andradx on 2014-02-14
I still have to try it, but I don't think there is a problem with the switchover. When depleted the ultrabay, the laptop just starts consuming the main battery. Problem is only the 0% discharge that will suck the life out of the cells in no time.



I will check on BIOS updates.

---

### Post by linrunner on 2014-02-16
Hi,

the behaviour of discharging the ultrabay battery first and down to  0% is a well known and often critizised ThinkPad feature. Afaik the only way to change this is to use some kind of balancing script. 

You'll have to use [tpacpi-bat]("https://github.com/teleshoes/tpacpi-") to achieve this because the T430s (as all ThinkPads of the Sandy Bridge generation and newer) is not supported by tp-smapi. You may use the version integrated into TLP: **/usr/lib/tlp-pm/tpacpi-bat**.



Btw: TLP does not provide such a feature intentionally.

---

### Post by tgalati4 on 2014-02-16
The on-board battery charge and discharge circuitry protects the cells.  So although 0% seems like sucking the battery dry, if you measure the voltage at 0% you will find that it is within acceptable limits for lithium ion cells.  The real issue is when the cells are a few years old, the 0% gets crossed very quickly into a low-voltage/high-current situation.  That will cause an immediate current overload fault and shutdown--possibly losing your work or not handing off properly to the main battery.  You only get ~300 charge-discharge cycles so when you go from 100% to 0% or 80% to 20%, you might increase the cycles by a few percent, but you decrease the running time by a lot.  It's a tradeoff.

---

