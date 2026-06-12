---
title: "[SOLVED] Which package for NVIDIA Geforce 7000M"
date: 2008-06-03
forum: Hardware
---

### Post by worldy on 2008-06-03
Which binary driver should i install for Geforce 7000M ?
nvidia-legacy, nvidia-glx or nvidia-glx-new

---

### Post by helino on 2008-06-03
I suggest using Envy NG (if you're using Hardy), which will automatically download and install the correct driver for you. You can find more info about Envy NG here:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by worldy on 2008-06-03
I am just not comfortable with third party scripts.

Installed nvidia-glx-new and graphics is working fine.
nvidia-glx is provided by nvidia-glx-new.

i had got my graphics working with nvidia-glx on gutsy before.

---

### Post by helino on 2008-06-04
Envy NG is supported by Ubuntu and it's avaiable in the repos, so all you have to do is:
```
sudo apt-get install envyng-gtk
```

You could also use Ubuntus Restricted drivers manager I guess, but if you want to do it totally on your own, you could download the drivers from Nvidia, and the follow this little guide: [http://ubuntuforums.org/showpost.php?p=5104158&postcount=3](http://ubuntuforums.org/showpost.php?p=5104158&postcount=3)

If you want to install the packages from Synaptic, my guess is that you should use the nvidia-glx-new, since 7000 M is quite modern.

---

