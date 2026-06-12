---
title: "ccsm not working"
date: 2008-10-04
forum: General Help
---

### Post by patrickaupperle on 2008-10-04
When I click ccsm under System>Preferences, nothing happens. After that, I decided to run it in the terminal. This is what came out:
```
patrick@patrick-laptop:~$ ccsm
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Please help.
What  should I do???

---

### Post by UbuntuNerd on 2008-10-04
looks like a bug check it out
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207")

run this command in a terminal
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```

---

### Post by patrickaupperle on 2008-10-04
> **UbuntuNerd said:**
> looks like a bug check it out
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207")

run this command in a terminal
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```

Thank you. Unfortunately, ccsm still wont come up. Now the terminal just sits there. Blank. No message. Maybe I should restart my computer?

---

### Post by patrickaupperle on 2008-10-05
Bump Please help.

---

### Post by Kevbert on 2008-10-05
> **patrickaupperle said:**
> Bump Please help.

What's the display card make, model? Intel, ATI and Nvidia cards work in most cases.  If it's not one of these, the card is not supported.  You could also try running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") and post back your results.

---

### Post by patrickaupperle on 2008-10-05
> **Kevbert said:**
> What's the display card make, model? Intel, ATI and Nvidia cards work in most cases.  If it's not one of these, the card is not supported.  You could also try running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") and post back your results.

I have integrated intel graphics. The thing is, Compiz works perfectly. I have the cube rotating and everything. CCSM is what is not working.
Here is compiz check:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by f1r31c3r on 2008-10-05
have you tried reinstalling it with the synaptic package manager maybe remove it then reinstall it etc then reboot your machine see if it works just a thought

also try run 
> 
apt-get update

> 
apt-get upgrade

you could check see if the package is broken so check for broken packages
> 
sudo dpkg --configure -a

think you can check for broken packages by using the filter buttons in the synaptic packet manager as well but i not sure.

---

### Post by patrickaupperle on 2008-10-05
> **f1r31c3r said:**
> have you tried reinstalling it with the synaptic package manager maybe remove it then reinstall it etc then reboot your machine see if it works just a thought

also try run 


you could check see if the package is broken so check for broken packages

think you can check for broken packages by using the filter buttons in the synaptic packet manager as well but i not sure.

Thank you for the suggestions. I have tried reinstalling it. I have not yet restarted since, when I finish what I am doing I will. I did notice one odd thing, don't ask why I did this, when I type in to the terminal ```
compiz
``` all the ccsms that I had tried to open show up. I can even change the settings. The problem is, I have to kill x after I do that. While this does work, I hope there is a different solution.

No broken packages.

---

### Post by patrickaupperle on 2008-10-05
I upgraded to 8.10 beta and ccsm now works fine. Thank you anyone who wanted to help or tried to help. I am not sure whether or not to mark this closed. The problem was not really solved. This would be almost no help to some one searching.

---

