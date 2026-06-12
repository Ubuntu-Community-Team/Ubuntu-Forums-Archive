---
title: "Additional Driver Advice"
date: 2012-09-07
forum: Hardware
---

### Post by samarthmath on 2012-09-07
I have a well working ubuntu system. But in the additional drivers section, there are two inactivated drivers.

I was wondering if it is a smart move to activate those drivers, or just let things be since, the system works fine for me.

---

### Post by sudodus on 2012-09-07
I guess those drivers are proprietary drivers for your graphics card/chip. You can read about that in the information on the same page that is showing the drivers.

Such drivers should activate more features of the graphics, so that you can get faster or more advanced graphics. But if you are satisfied with the system as it is now, with the built-in driver, that's good, because there is always a risk, that your graphics might fail with a proprietary driver.

---

### Post by samarthmath on 2012-09-07
Yes, they are proprietary drivers:

the Broadcom STA wireless driver and
the ATI/AMD proprietary FGLRX graphics driver.

Any opinion on these specific drivers?

---

### Post by coffeecat on 2012-09-07
> **samarthmath said:**
> 
the Broadcom STA wireless driver

Is your wireless working well? If so, then it is one of the Broadcom chipsets that is supported by the in-the-box open source brcmsmac driver. Some people get better performance with the proprietary STA driver but I suggest that if it's working OK now, leave things as they are.

What is your wireless chipset? If you don't know, run this terminal command:
```
lspci
```

There will be a line with "wireless" and/or "802.11" in it. That will be the wireless device.

> **samarthmath said:**
> 
the ATI/AMD proprietary FGLRX graphics driver.

For most ATI graphics cards, the default open source driver works well enough for most people. I don't bother with the fglrx driver for my ATI card. If you are a gamer you might need the better performance the proprietary driver might give you, but otherwise, as for your wireless device: if it's working OK for you, I suggest you leave things be.

If you want to know what GPU your graphics device is, have a look at the output of lspci again, the line with "VGA" in it.

---

### Post by samarthmath on 2012-09-07
> **coffeecat said:**
> Is your wireless working well? If so, then it is one of the Broadcom chipsets that is supported by the in-the-box open source brcmsmac driver. Some people get better performance with the proprietary STA driver but I suggest that if it's working OK now, leave things as they are.

What is your wireless chipset? If you don't know, run this terminal command:
```
lspci
```

There will be a line with "wireless" and/or "802.11" in it. That will be the wireless device.



For most ATI graphics cards, the default open source driver works well enough for most people. I don't bother with the fglrx driver for my ATI card. If you are a gamer you might need the better performance the proprietary driver might give you, but otherwise, as for your wireless device: if it's working OK for you, I suggest you leave things be.

If you want to know what GPU your graphics device is, have a look at the output of lspci again, the line with "VGA" in it.

My wireless chipset is Broadcom corp. BCM43224 802.11a/b/g/n
and my graphics card is ATI technologies Inc Manhattan Mobility Radeon HD 5000 series

I suppose the best thing might be to let things be.

---

