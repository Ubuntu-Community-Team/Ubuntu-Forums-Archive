---
title: "Weird problem, am I disconnected?"
date: 2008-09-16
forum: General Help
---

### Post by olhat on 2008-09-16
I tried to install Kuduntu-desktop on my Ubuntu.  I googled around and found out that I can install Kubuntu online through Synaptic Package Manager ->search ->Kubuntu-desktop but there seems to be no package called so.  Is my Synaptic somehow disconnected from some of the needed depositories and could I do sth to correct the situation?  The connectivity is normal through Firefox and other applications.



TERMINAL

I have tried following commands in Terminal:
“sudo apt-get install kubuntu-desktop”
“sudo aptitude install kubuntu-desktop”



$ sudo apt-get install kubuntu-desktop

[sudo] password for olhat: 

Sorry, try again.

[sudo] password for olhat: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package kubuntu-desktop



~$ sudo aptitude install kubuntu-desktop

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done      

Couldn't find any package whose name or description matched "kubuntu-desktop"

Couldn't find any package whose name or description matched "kubuntu-desktop"

No packages will be installed, upgraded, or removed.

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done 



SYNAPTIC
“Synaptic Package Manager” shows:

“Generate package download script” says
“Nothing to install/upgrade”

The bar furthest down shows:
“1114 packages listed, 1114 installed, 0 broken. 0 to install/upgrade, 0 to remove”

---

### Post by NoReflex on 2008-09-16
I think you can try :
```
sudo apt-get install kde
```

Best wishes,
NoReflex

---

### Post by jken146 on 2008-09-16
> **NoReflex said:**
> I think you can try :
```
sudo apt-get install kde
```

Best wishes,
NoReflex

Nope, the package you want is **kubuntu-desktop** for sure.


Go to System -> Administration -> Software Sources and make sure that Main, Universe and Multiverse are enabled.  That can't hurt.  Then try ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

---

### Post by olhat on 2008-09-16
All sources were disabled by default.  

Kubuntu-desktop found now, not installed yet.  Silly me, nothing new. Thanks all!

---

