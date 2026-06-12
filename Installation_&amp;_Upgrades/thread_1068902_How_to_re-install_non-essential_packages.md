---
title: "How to re-install non-essential packages"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by asundaresan on 2009-02-13
Hi:

I've a laptop with Hardy installed. X has weird problems in that when I switch to a console, I get a colorful blinking screen instead. I had installed fglrx and had 3D graphics earlier and now I can't get it to work. I think there is some problem with X and maybe other packages. I think removing packages (including config files) and reinstalling them would help. While I'm at it, I'd like to remove a bunch of non-essential programs as well. I see this as an alternative to actually reinstalling hardy which I don't want to do. 

Can anybody provide a better solution? Or alternatively answer the following questions? 

1. Is there anyway to "upgrade" to hardy from hardy (removing non-essential packages and reinstalling them?)

2. Where can I get a list of packages that come installed with hardy so that I can do a diff and manually remove all the packages? 

I'm a fairly experienced Linux user of 7 years and am looking for something elegant and not blunt hacks :)

Thanks,
Aravind.

---

### Post by asundaresan on 2009-02-13
In a related message, I have an ATI radeon card. At one point in the past, I used to be able to click on System->Administration->Hardware Drivers to be able to enable or disable proprietary drivers for my graphics card. The Hardware Drivers window is not blank. How can I install proprietary drivers in the official way now?

---

### Post by Taemojitsu on 2009-02-13
aptoncd lets you archive installed packages so you can download them again.

I believe apt itself lets you reinstall packages? There is probably a command you can do to reinstall multiple, or even all packages.


Getting proprietary drivers to show may be as simple as enabling all repositories and reloading. However I'm not quite sure of how it works; in Nvidia at least, there's a package which lists all the cards (by some unique value they report) supported by each driver, ATI may have something similar. In Nvidia I know the package comes by default on the LiveCD, so it knows proprietary drivers are available.

Again just for Nvidia, installing the driver without using the Proprietary Driver helper program is as simple as selecting, for example nvidia-glx-180, and installing it and all dependencies. It's probably just as simple for ATI. 

I found this ATI site recently while trying to fix problems on my notebook, I didn't skim it because it's ATI ony but it might be useful. Won't load for right now so I can't say if it has a Hardy version as well as the Intrepid one.
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by asundaresan on 2009-03-02
Hello:

I think I solved at least one of the problems. The package that controls the hardware manager is called jockey. So it is necessary to do the following 

```

apt-get remove jockey-common jockey-gtk jockey-kde

```

followed by 

```

apt-get install jockey-gtk

```
or alternatively for kde users **jockey-kde**.

Aravind.

---

