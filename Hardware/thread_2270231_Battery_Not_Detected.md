---
title: "Battery Not Detected"
date: 2015-03-21
forum: Hardware
---

### Post by gunksta on 2015-03-21
After installing Ubuntu on a Surface Pro 3, I am not able to see the status of the battery and when I unplug the laptop, the computer does not enter into a power saving state. For example, if I unplug the laptop and try to run powerstat, it refuses because my computer is not seen as discharging. Furthermore, 

```

 [FONT=monospace][COLOR=#000000]andy@optimus:~$ laptop-detect -v  [/COLOR]
We're not on a laptop (no relevant hint found) 
andy@optimus:~$ laptop-detect -V 
Version: 0.13.7ubuntu2

```

So, clearly, my laptop is not recognized as such. Any thoughts?
[/FONT]

---

### Post by gunksta on 2015-03-23
Based on this [GitHub repo]("https://github.com/danielquinn/Gentoo-Surface-Pro-3/tree/master/kernel"), it looks like this could be a common problem under the 3.19 kernel, which is interesting because it apparently worked on older kernels. 3.19.x is all I have ever installed on this particular hardware, so I lack the perspective. But the author of the GH repo is running Gentoo, so it does not appear to be a Ubuntu-specific problem.

ACPI digging is something I have never done before. How would I go about trying to make the kernel recognize the battery?

---

### Post by gunksta on 2015-04-01
At this point, this is really my last outstanding problems with Linux on the Surface Pro 3. If anyone knows what I can do to help debug this, I would greatly appreciate it.

---

