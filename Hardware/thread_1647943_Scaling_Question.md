---
title: "Scaling Question"
date: 2010-12-18
forum: Hardware
---

### Post by vmarcano718 on 2010-12-18
I have a Acer 2.13 Ghz Laptop. I am trying to work on power saving options. I want to scale down the freq. While in the cpufreq folder i tired to:
sudo "value" > cpuinfo_cur_freq
but i get-
bash: cpuinfo_cur_freq: Permission denied
 
My question is why can't i get the permission, even w/ using sudo, and sudo su?
 
Also, i want to view avialable freq, and scale down to lowest freq. 
Thanx.
No trolling pls

---

### Post by vmarcano718 on 2010-12-19
> **vmarcano718 said:**
> I have a Acer 2.13 Ghz Laptop. I am trying to work on power saving options. I want to scale down the freq. While in the cpufreq folder i tired to:
sudo "value" > cpuinfo_cur_freq
but i get-
bash: cpuinfo_cur_freq: Permission denied
 
My question is why can't i get the permission, even w/ using sudo, and sudo su?
 
Also, i want to view avialable freq, and scale down to lowest freq. 
Thanx.
No trolling pls
 
- powertop. Open source program by intel. great program. easy to use. helps with battery consumption. not what i was looking for, but it helps.

---

