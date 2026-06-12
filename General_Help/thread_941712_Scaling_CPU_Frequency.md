---
title: "Scaling CPU Frequency"
date: 2008-10-08
forum: General Help
---

### Post by es926 on 2008-10-08
Hello,

I installed cpufreq and gave suid root to the gnome applet for it so that I can easily control it. Something keeps changing the allowed range for frequencies every time I restart, plug in the power cord, or unplug it though. What program is changing these settings? I would really like to just control it myself and it gets annoying having to type sudo cpufreq-set -d ".8GHz" -u "2.4GHz" over and over.

Thanks

---

### Post by Yellow Pasque on 2008-10-08
It's probably the cpufreqd (daemon). Try removing it (through Synaptic or apt-get remove) and seeing if the scaling functions properly. If you have to reinstall it, you can configure it by editing /etc/cpufreqd.conf

---

### Post by fjgaude on 2008-10-08
This always works for me:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

That permits you to control from the tray applet.

---

### Post by mdurham on 2008-10-12
> **fjgaude said:**
> This always works for me:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

That permits you to control from the tray applet.

Thanks for that fjgaude, I wondered what the problem was.
Mike

---

### Post by soccerush10 on 2009-01-06
> **fjgaude said:**
> This always works for me:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

That permits you to control from the tray applet.
Thank you for your post!  This worked like a charm for my HP tx1320us, and I'm sure it could work for other people as well.  Now I can switch from Userspace, to Ondemand as needed...this is great! Thanks again.

---

