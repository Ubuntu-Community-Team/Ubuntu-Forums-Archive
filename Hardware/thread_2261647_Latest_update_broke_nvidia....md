---
title: "Latest update broke nvidia..."
date: 2015-01-20
forum: Hardware
---

### Post by naviathan on 2015-01-20
I'm not sure why this is constantly an issue, but it seems like every single time I update and get a kernel update it tries to ditch my nvidia driver and install nouveau. If I wanted nouveau I would install nouvea, now I cant get rid of it. After the latest update (I've been dealing with this for a few days now so latest is relative) my system boots to a black screen. The monitor shows an input, but there's no mouse cursor, desktop, etc... The system is running. I can't seem to ctrl+alt+F1 to any other consoles, but if I pull up screenconnect from another computer I can send commands through the limited command interface. Looking at my Xorg log it appears Xorg is looking for nouveau even though nvidia is installed and the module is loaded. I also notices that libdrm-nouveau2 is installed and if I try to remove it it tries to uninstall Xorg. I tried reinstalling nvidia-331-updates, but it does nothing. This has happened before but reinstalling nvidia would bring it back up again. HELP!

---

### Post by Pilot6 on 2015-01-20
How did you install nvidia driver?

---

### Post by naviathan on 2015-01-20
apt-get -y --reinstall install nvidia-331-updates

---

### Post by tokyobadger on 2015-01-20
> **naviathan said:**
> I'm not sure why this is constantly an issue, but it seems like every single time I update and get a kernel update it tries to ditch my nvidia driver and install nouveau. 
What versions of Ubuntu?
What's your hardware?
How did you install nvidia drivers?
What kernel are you running?
Has this pattern been occurring since installation/upgrade or did it start at a specific point in time after?

---

### Post by naviathan on 2015-01-20
Xubuntu 14.10
Kernel 3.16.0-30-generic
nvidia GTX 560 Ti
This problem started happening about 6 months ago. Everytime I would get a kernel update I would have to drop to a maintenance console and reinstall the nvidia drivers (apt-get -y --reinstall install nvidia-331-updates).

---

### Post by tokyobadger on 2015-01-20
Thanks for the info
Is that GTX560Ti the full-fat or the clipped OEM version (384 vs 352 CUDA cores)?
Kernel 3.16.0-30-generic vs my just (ie after reading your reply) updated Ubuntu 14.10 with 3.16.0-29-generic - do you have proposed switched on or did you install that kernel manually?

You might want to consider purging your drivers entirely and then installing again.
Another option would be again to purge the drivers and then install 346.35 from the xorg-edgers ppa

---

### Post by naviathan on 2015-01-20
Full fledged 560Ti, not OEM.

I tried Xorg-Edgers one time and it was a nightmare. I may have proposed on and not realized it.

---

### Post by tokyobadger on 2015-01-20
Try the purge install first and see what that gets you.

The xorg-edgers ppa is pretty smooth in the last 12 months or more and frankly the best "ubuntu way" (ie no manual downloads) to get the latest drivers, but I wouldn't go there until your base system is fixed

---

### Post by naviathan on 2015-01-20
No luck with the purge install. I purged both nouveau* and nvidia* then installed just nvidia-current and rebooted. Still no display.I did notice it's also loading the i915 display driver for my embedded GPU in the i5-2500k.

---

### Post by Yellow Pasque on 2015-01-20
> **naviathan said:**
> and install nouveau. If I wanted nouveau I would install nouveau, now I cant get rid of it

You don't need to uninstall any nouveau packages; you just need to blacklist the nouveau kernel module (and the nvidia or nvidia-updates packages does that for you automatically).

It sounds like something is not right with dkms. The next time you get a kernel update and have a problem, you should look for nvidia logs in /var/lib/dkms/

I'm also wondering whether this was a fresh install of 14.10 or if you upgraded from an older release. If you upgraded from an older release, you may have older kernels hanging around and causing problems.

---

### Post by naviathan on 2015-01-20
This was a fresh install and I always autoremove any excess kernels and headers. Another odd thing I've noticed is that if I go into maintenance mode then resume the desktop shows up, but the resolution is off and only one of two monitors shows up. If I restart I'm back at a black screen.

---

### Post by vinnywright on 2015-01-20
remove/purge all installed Nvidia drivers ,,,,,,,,,make sure you have "linux firmware", "linux-generic"(meta package) , linux-headers<your curent ver.#'s> , linux-image<your curent ver.#'s> linux-image-extras<your curent ver#'s> and the "dkms" packages installed (if missing any of these install them first)((of course you will have "linux-image<your curent ver.#'s or you wouldent boot at all )) then reinstall your Nvidia drivers ,,,,,, I suspect you are missing the "dkms" package and/or "linux-generic"/linux-headers<your curent ver.#'s>  the "dkms"will rebuild the Nvidia driver for a new kernel (it has to be) when you get one.

VINNY

---

### Post by naviathan on 2015-01-21
I tried removing and purging everything already. As a last resort I decided to throw xorg-edgers in there and see what happens. Well, I have a desktop. I don't get it. I don't know what the problem was, but it works.

---

### Post by tokyobadger on 2015-01-21
Wasn't aware that you had a multi-monitor set-up but as I have no experience with those I couldn't say if that was a factor or not. Good to hear you have a solution if not an answer to what was casuing the issue

---

### Post by naviathan on 2015-01-21
The true test will be the next kernel update...

---

### Post by tokyobadger on 2015-01-21
hmm - I run 2 GTX680 in SLI and I need to re-run
```
 sudo nvidia-xconfig --busid=PCI:2:0:0 --sli=AA
```
but that's after driver updates rather than kernel updates - just got me wondering what your xconfig looks like in light of dual(?) monitors and if there's any correlation between the kernel updates and the issues you faced...

---

### Post by startas on 2015-01-21
How do you even run linux right now with nvidia laptop graphics? I mean, nvidia drivers doesnt work much, there is 100% tearing even in ubuntu, games run terrible, linux kernel is going through some hard times, even virtual terminals doesnt work, not to mention broken xorg server. Is here anyone else with a laptop with newer nvidia graphics (i.e. 840m) ? Does ubuntu work for you ?

---

### Post by Yellow Pasque on 2015-01-21
> **startas said:**
> How do you even run linux right now with nvidia laptop graphics?

This thread is referring to a desktop card. Laptops with Nvidia GPU's are hybrid/"Optimus" setups, which are somewhat different. My point is that you should start your own thread or find one dealing with Optimus. You're just going to confuse people by posting in this one.

---

### Post by b-woznicki on 2015-01-30
I had blank screen issue with gt750ti and nvidia drivers when connected directly to that card , then i plugged to on board intel and removed graphics card from board including drivers , then reinstaled drived - power down - inserted graphics and that solved the problem for me. Thats would have help with desktop , just realised u talking about laptop.

---

