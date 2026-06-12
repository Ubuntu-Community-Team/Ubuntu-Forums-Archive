---
title: "acpi-cpufreq and cpufrequtils or powernowd/cpudyn?"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by cb474 on 2007-08-12
I just upgraded to Feisty. In the wiki there's a guide for enabling cpu frequency scaling: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features).

This guide suggests removing powernowd and cpudyn and installing cpufrequtils along with an appropriate cpumodule (acpi-cpufreq for my ThinkPad T60--for some reason the speedstep-centrino module which worked in Edgy doesn't in Feisty). 

Why make this change? Out of the box with powernowd frequency scaling was working for me in Feisty. Also why does Feisty have powernowd and cpudyn both installed out of the box. Aren't they redundant?

---

### Post by ddrichardson on 2007-08-12
I have Fiesty and powernowd is installed by default but cpudyn is not. Note as well that the link you give isn't "official" Ubuntu documentation.

It's also a hell of a lot more complicated than adding the frequency scaling desklet and doing:
```
sudo dpkg-reconfigure gnome-applets
```

To enable running with setuid.

---

### Post by cb474 on 2007-08-12
Yeah, I know it's more complicated, that wasn't really my question. My question was why would someone go to the trouble to do this? Since a whole guide has be written up on how to do it, I assume someone  believes it has some benefit. I did read a brief statement that enabling cpu frequency scaling at the kernel level is more "effecient" than operating frequency scaling from userspace (which I guess is what powernowd does). But that's all I've found. Any other thoughts about what advantages there might be to this?

Also, does powernowd work with laptop-mode?

---

