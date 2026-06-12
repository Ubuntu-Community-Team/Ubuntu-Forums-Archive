---
title: "Hardware Issues with Acer Aspire 5 (A515-47)"
date: 2024-05-08
forum: Hardware
---

### Post by 4r7if3x on 2024-05-08
I've installed Ubuntu 24.04 LTS on my brand-new Acer Aspire 5 (A515-47) laptop and I noticed a few issues with hardware compatibility:

[LIST]
[*]The APU **Fan** is running continuously (Ryzen 7 5825U)
[LIST]
[*]It's on medium/high speed and there is no silent moment, even if no app is running on a fresh installation. 
[*]TopHat reports the CPU temperature to be around 75-85 degrees. At this very moment, it's 83° while web browsing only. 
[/LIST]
  
[*]The **webcam** module isn't recognized (Quanta) 
[*]**Disk Capacity** is Unknown (Micron 2400 SSD) 
[*]The combination of **Fn + Arrow Right/Left** keys doesn't do anything
[LIST]
[*]I'm very much used to this shortcut to move the cursor at the end/beginning of the line. 
[/LIST]
  
[*]Only **30.7GB of 32GB RAM** and **14.9GB of 16GB Swap** seem to be accessible according to htop. More than **100-200GB of the 1TB SSD** is missing as well. It's just too much to be taken as normal... 
[/LIST]

Are there any solutions to these?

---
[B]
UPDATE 1:[/B] I've found the solution for the webcam issue and it's fixed now: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947/comments/129](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947/comments/129)
**UPDATE 2:** I've created custom keyboard shortcuts, binding Ctrl+Arrow-Right/Left to End/Home keys using [dotool]("https://git.sr.ht/%7Egeb/dotool") command.

---

### Post by gezzer2 on 2024-05-08
to tell you the honest truth i would wipe the system and reinstall and see if that fixes the issues.

i had problems on my oldish dell with 24.04 and had to reinstall 22.04 were everything just works
but i would try a reinstall of 24.04 and see if there is improvements, sometimes thats the only way to fix things, before trying 22.04.

sorry if that is not of much help ..

---

### Post by 4r7if3x on 2024-05-08
> **gezzer2 said:**
> to tell you the honest truth i would wipe the system and reinstall and see if that fixes the issues.

i had problems on my oldish dell with 24.04 and had to reinstall 22.04 were everything just works
but i would try a reinstall of 24.04 and see if there is improvements,  sometimes thats the only way to fix things, before trying 22.04.

sorry if that is not of much help ..

Thanks for your response, but unfortunately that wouldn't be an option for me. I've been using Ubuntu 23.10 for quite some time and I'm used to Gnome 45+ and going back to 44 would be a huge setback. Besides, these problems might have nothing to do with the Ubuntu version, but some Kernel-level issues and a lack of suitable drivers. I hope someone here can let me know how I can resolve them...

---

