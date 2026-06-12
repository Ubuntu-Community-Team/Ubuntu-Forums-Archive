---
title: "Eebuntu: how do you install and run using synaptic package manager"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by Littlemoo on 2009-02-15
I am new to linux and have installed eeebuntu on my eeepc to get round the wireless network problems.
i am trying hard to like linux but it is hard after being familiar with windows. 
I am struggling to work out how to install and run programs. 
i tried to install xmms, based on a reccomendation.
After using seach, i found a package called xmms2 and right clicked " ark to install"it then to me to install that, and all realated packeages.
i think it has installed, but i don't know where it has installed to, or how to run the program after it has been installed. 
so, e
Is there an add/remove programs for eeebuntu like there is in standard ubuntu, as this appeared to be easier to use. 
If not, how do i find out where my programs have installed to, and how do i run them after installation with SPM.

Thanks loads,
Jo

---

### Post by cariboo on 2009-02-15
Xmms2 is a command line program you need to install a front end to use it. Xmms is no longer in the repositories, you can get it [here]("http://www.pvv.ntnu.no/~knuta/xmms/")

Add the repositories to your /etc/apt/sources.list. To do this press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

type your password when asked. Simply copy and paste the sources for your version to the bottom of the file, then save and exit. Next go to System-->Administration-->Synaptic Packages Manager and click the reload  button. Once the repositories have reloaded search for xmms, once it shows up right-click and select install. Xmms will not show up in the menu, so you will have to add it yourself.

To make sure it installed correctly, Press Alt-F2 and type xmms.

Jim

---

