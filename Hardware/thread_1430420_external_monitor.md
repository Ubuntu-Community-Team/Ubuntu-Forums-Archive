---
title: "external monitor"
date: 2010-03-15
forum: Hardware
---

### Post by jim001 on 2010-03-15
Hi

I want to use external LCD monitor instead of laptop monitor. I do not see an option "Do nothing when lid is closed". So I have "blank screen when lid closed" selected.

The external monitor is displaying the same info as Laptop screen. So external monitor works fine. However when I close laptop lid, everything is put on suspend, which I don't want.

I just want to be able to continue using external monitor, while laptop lid is closed in order to save some power/energy.

How can I achieve this?
How can I acheive dual monitor mode, where laptop screen is used for something and external monitor is used for something?

Thanks
Jim

---

### Post by Fxy on 2010-03-15
I don't think this is possible as once you close the lid of your laptop it is put on hold/sleep...

---

### Post by AGlory on 2010-03-15
> **jim001 said:**
> Hi

I want to use external LCD monitor instead of laptop monitor. I do not see an option "Do nothing when lid is closed". So I have "blank screen when lid closed" selected.


Annoying, ain't it?  Here's the fix (sudo isn't necessary):
```

gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_ac  "nothing"
gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_battery  "nothing"

```Cheers.

---

### Post by jim001 on 2010-03-18
Hi
 
Do I have to run these 2 commands every time I restart?
 
Thanks

---

### Post by era86 on 2010-03-18
You can just go to the Power Manager application from the main menu.  You can set what the action is when the laptop lid is closed.  I have mine set to just turn the screen black, thus allowing me to keep the external monitor on for working while the lid is closed.  This is what you are trying to achieve right?

---

