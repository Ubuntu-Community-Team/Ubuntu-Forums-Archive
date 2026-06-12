---
title: "text missing"
date: 2008-11-24
forum: General Help
---

### Post by Russty of Oz on 2008-11-24
I am using Kubuntu and Compiz with the Nvidia 96.43.09 drivers (MX440 video card) and on some programs such as K3b there is no text in the boxes or from the drop down menus in File, Edit etc.  (see screenshot)  as I move the mouse over the blank area there is a very quick flash of text but not enough time to read it.  

Does anyone know what is the cause of this? 

Russty.

---

### Post by blazemore on 2008-11-24
Why do you have to use the old drivers? Do you use legacy hardware?

Also, if this is purely a Compiz issue (mod suggest moving to relevant forum), try updating Compiz to the latest version

Add the following line to /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```
and so apt-get update and apt-get upgrade -y

---

### Post by SocratesTNR on 2008-11-24
Rusty, do a search of this forum for Nvidia and or 96.43.09...


There's dozens of us having the same problems...

Bugs have been reported here, on the NVIDIA forum and on Launchpad (here's just one):

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836)

Some patches have been suggested and work for some people but fundamentally, there's a problem with the 96 driver.

If you switch off the fancy screen effects then you should be ok.

You'll just have to wait for an updated driver to get yer wobbly windows back.

---

### Post by Russty of Oz on 2008-11-24
Thanks guys, I will try turning off the extra effects and see what happens.  

The old drivers are the only ones that work with my old graphics card with Intrepid at the moment so I will just have to wait for newer drivers to be released.

Russty

---

### Post by henrik9 on 2008-12-02
I had this problem and for me it disappeared when I turned compiz off. So I uninstalled compiz and deleted all compiz configuration files manually (do a search and search for *compiz*). After compiz reinstallation everything worked fine. Can be worth a try.

---

