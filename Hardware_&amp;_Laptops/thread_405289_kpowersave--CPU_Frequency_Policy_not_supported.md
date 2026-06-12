---
title: "kpowersave--CPU Frequency Policy not supported?"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-04-09
OK...

Why does kpowersave reports that setting the CPU frequency policy is not supported on my computer, but I can run "powersave -l" or "powersave -f" or "powersave -A" to change my CPU frequency. I want control over this in kpowersave, as it is quite a bit more conveinant than opening up a console and typing a powersave command every time. This worked in edgy, but in feisty it does not.

What's going on?

---

### Post by tensor on 2007-04-13
Same for me kpowersave does not allow me to change CPU scaling policy.
I am running an LG LM40a Pentium-M 1,6 MHz notebook.

---

### Post by moixa on 2007-04-13
I think it's because your CPU frequency policy is directly controlled by your kernel already, so userspace instructions are ignored.

If you change the frequency governors to "userspace" it SHOULD resolve your concern.
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

but I would rather the kernel takes care of the frequency for me automatically

---

### Post by tensor on 2007-04-14
After doing 
```

# modprobe cpufreq_userspace
# echo userspace > scaling_governor

```

and restarting kpowersave I still do not have the option to control the policy in kpowersave.
BTW, are policy and governor the same thing?

---

### Post by enigma_0Z on 2007-04-14
> **tensor said:**
> After doing 
Are policy and governor the same thing?

Yes.

I've found a fix... add

```

your-cpu-chipset
cpufreq_ondemand
cpufreq_userspace
cpufreq_powersave
cpufreq_performance

```

And replace "your-cpu-chipset" with the powersave module for your CPU (powernow-k8 for me, centrino, acpi, powernow-* etc for others)
to /etc/modules... This will work:

```
echo "your-cpu-chipset
cpufreq_ondemand
cpufreq_userspace
cpufreq_powersave
cpufreq_performance" |sudo tee -a /etc/modules
```

Reboot and enjoy. Seems that these modules must be present before /etc/powersaved is run, otherwise things bork. Restarting powersaved won't work either, need to reboot.

---

