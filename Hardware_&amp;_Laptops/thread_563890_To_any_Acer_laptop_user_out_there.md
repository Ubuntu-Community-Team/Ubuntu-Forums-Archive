---
title: "To any Acer laptop user out there"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by Rob500 on 2007-09-30
I am switching to Kubuntu as the sole operating system this week, however there is one thing I would lie to clear up first.

I've read that on some laptops the WLAN LED does not function correctly, meaning this has to be entered:

Create the file /etc/modprobe.d/ipw2200:

```
sudo nano /etc/modprobe.d/ipw2200
```

And add this line:

```
options ipw2200 led=1 

```

Now, I know this is a problem with the LED, but does it actually have any effect on the wireless adapter itself. Like, if I click disable wireless in Kubuntu, will it actually disable the wireless, or leave it active as the LED would suggest?

Many Thanks

---

### Post by Rob500 on 2007-09-30
Anyone?

---

### Post by Incursis on 2007-09-30
What is your wireless card? Intel? Atheros? Broadcom?

---

### Post by kerry_s on 2007-09-30
also put a line in /etc/modules > ipw2200
so it looks for that.

i have no idea if it works or not though, i set up a acer 3500 for grandma, but it didn't have wireless.

i would say, just install first, if you see that problem then try it. things change from version to version, it may already be fixed in the version you install. by version i mean> dapper, edgy, fiesty, gutsy.

---

### Post by Incursis on 2007-09-30
Did you also restart your computer after you modified the file?

---

### Post by Rob500 on 2007-10-02
> **Incursis said:**
> What is your wireless card? Intel? Atheros? Broadcom?

It's an Atheros adapter. It works okay, it's just the button that I'm concerned about because if the wireless does not disengage, that's battery life wasted needlessly.

I've only used the live CD and I did run it down with the wireless disabled (light on but options disabled) and it gave battery life to reflect the wireless was off, although the CD drive would have affected this because of power consumption.

> **Incursis said:**
> Did you also restart your computer after you modified the file?

I was using the live CD only.

---

