---
title: "USB Thumb Drive will not mount"
date: 2008-08-25
forum: Hardware
---

### Post by balagosa on 2008-08-25
I have a thumb drive that was full of viruses coming from a Wind*** PC. I manually deleted them including a certain "autorun.inf". After the incident, I noticed the thumb drive did not work anymore. I replugged it and nothing happened. I plugged it to a Wind*** PC and still nothing happened.

Output of dmesg:
```

[ 5003.446669]  domain 0: span 03
[ 5003.446672]   groups: 02 01
[ 5003.714484] Clocksource tsc unstable (delta = -537189598 ns)
[ 5003.722465] Time: hpet clocksource has been installed.
[b]
[11128.443623] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11130.362682] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11132.282775] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11134.200879] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11136.119956] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11138.039033] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11139.958106] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11144.675857] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11147.587623] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11158.186375] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11164.518374] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11166.437401] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11168.356505] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11170.279562] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11172.203647] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11174.121732] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11176.040815] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11177.960890] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11179.878977] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11181.798090] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11183.717130] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11189.475407] printk: 2 messages suppressed.
[11189.475417] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11195.232607] printk: 2 messages suppressed.
[11195.232618] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11199.069780] printk: 1 messages suppressed.
[11199.069792] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11205.034923] printk: 2 messages suppressed.
[11205.034929] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[11209.003567] printk: 1 messages suppressed.
[11209.003580] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[/b]

```

---

### Post by ajgreeny on 2008-08-25
Try reformatting it with gparted or any other utility.

---

### Post by balagosa on 2008-08-25
It does not mount. It will not show on my system. Any idea how I can format it with the current situation?

I tried plugging it in before logging on and still no luck.

---

### Post by silkstone on 2008-08-25
You say it won't show on your system, but does that include gparted? If the formatting is corrupt, it won't mount or show in Places.

---

### Post by balagosa on 2008-08-26
Hold on to that thought. I will be trying GParted

Any additional info like: try GParted in liveCD, etc?

----------------------------------------------------------------------

That is a confirmed Negative. Even GParted can not see my Thumb Drive.

Question: How will I know if the USB was fried? (But if it was fried, then **[11128.443623] hub 2-0:1.0: connect-debounce failed, port 2 disabled** would not happen)

---

### Post by silkstone on 2008-08-26
Does the drive show in Windows Disk Management?

If not, it's probably deceased. The OS may know that something has been plugged in, but cannot resolve it.

---

### Post by balagosa on 2008-08-27
Closing this thread.

I consider no more hope for my thumb drive

---

