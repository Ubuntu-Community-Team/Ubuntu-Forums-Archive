---
title: "[SOLVED] Nvidia graphics card help."
date: 2008-07-05
forum: Hardware
---

### Post by dodle on 2008-07-05
I just reinstalled xubuntu on my system and downloaded the nvidia-glx-new graphics driver from synaptic.  I have attempted, many times before, downloading the driver directly from nvidia.com and manually installing.  I never succeed though.  

My question is whether the driver from Nvidia's website is better than the one offered in the Ubuntu repositories, or is it basically the same driver?

I have an Nvidia GeForce 6600.

---

### Post by starcannon on 2008-07-05
I prefer the latest stable drivers from Nvidia's website; however, the drivers found in synaptic package manager are likely the easiest to administrate. For instance, if the updater gives you a new kernel, and you have used the driver module from the synaptic package manager, then assuming all went as it should you will not have to mess with anything; but, if you use the drivers from nvidia's website,[S][SIZE="1"]*then anytime the kernel changes you will have to run the installer again..*[/SIZE][/S]
then be sure to use the link in vor's post directly below mine, THANKS vor for the excellent guide.

If you don't mind running the install program every once in awhile, then try my guide here:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and don't skip steps.

---

### Post by sdennie on 2008-07-05
> **starcannon said:**
> if you use the drivers from nvidia's website, then anytime the kernel changes you will have to run the installer again..


Not completely true: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

;)

---

### Post by dodle on 2008-07-06
Thanks for the info.  I'm going to stick with the repository's driver for a while.  If I get a little braver later on I'll try your methods to install from nvidia.com.

---

### Post by starcannon on 2008-07-06
> **vor said:**
> Not completely true: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

;)

@vor

thanks for that post, do you mind if I link that up with my guide? that makes it ideal (not that running the install script was hard, but I like your method better).

---

### Post by sdennie on 2008-07-06
> **starcannon said:**
> @vor

thanks for that post, do you mind if I link that up with my guide? that makes it ideal (not that running the install script was hard, but I like your method better).

Not at all.  In fact, I hope nvidia sees it and makes it part of the driver install.  It's a very simple fix to a common problem.

---

