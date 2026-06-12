---
title: "Issues with Gnome possibly any suggestions?"
date: 2008-10-03
forum: General Help
---

### Post by ster1988 on 2008-10-03
I just installed Ubuntu 8.04 on my gate way laptop today, and i am noticing some weird issues.

1. the Panel (toolbar) at the top of my screen is cut off short and does not extend all the way across the screen.

2. When i go into screen setting it shows two displays when i only have one.

3. When minimizing a window it leaves what could be described as a ghost patch on my screen until i bring focus to that area. 

4. Here are the stats of my lap top. 4 gbs of RAM, core 2 duo 2.0 processor
Intel® Graphics Media Accelerator X3100,

Any suggestions would be greatly appreciated.

---

### Post by Ryadt on 2008-10-03
Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Sycron on 2008-10-03
The > 2. When i go into screen setting it shows two displays when i only have one. is normal. You have a laptop no ? One monitor is the default screen and the other one is the VGA/ANALOG port.

---

### Post by Bucky Ball on 2008-10-03
Have you downloaded all updates? Have you installed ubuntu-restricted-extras?

Try System->Preferences->Advanced Desktop Effects Settings.

---

### Post by ster1988 on 2008-10-03
> **Bucky Ball said:**
> Have you downloaded all updates? Have you installed ubuntu-restricted-extras?

Try System->Preferences->Advanced Desktop Effects Settings.

i downloaded all of the updates, i haven't installed the advanced desktop  effects yet, should i install those ?

---

### Post by ster1988 on 2008-10-03
> **Bucky Ball said:**
> Have you downloaded all updates? Have you installed ubuntu-restricted-extras?

Try System->Preferences->Advanced Desktop Effects Settings.

how do i install ubuntu restricted extras ?

---

### Post by Bucky Ball on 2008-10-04
Go to System->Administration->Synatics Package Manager and do a search for:

**ubuntu-restricted-extras**

... Tick it and then apply changes. :)

After that it may give your an option to install restricted drivers for you card (ie not open source, third party drivers which the Linux community can give you no offical support on). No mind, install 'em anyhow! That should get things going.

---

### Post by ster1988 on 2008-10-06
> **Bucky Ball said:**
> Go to System->Administration->Synatics Package Manager and do a search for:

**ubuntu-restricted-extras**

... Tick it and then apply changes. :)

After that it may give your an option to install restricted drivers for you card (ie not open source, third party drivers which the Linux community can give you no offical support on). No mind, install 'em anyhow! That should get things going.

This is going to sound really dumb, but i was clicking around with my mouse and i actually just clicked and dragged the panel all the way to the right so now it actually fits my screen. The other night when i installed i tried doing this but it would only work on the bottom, Thanks for all of the help.

---

### Post by Bucky Ball on 2008-10-07
Good move. Load the restricted-extras anyhow. ;)

---

