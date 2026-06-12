---
title: "[SOLVED] uninstalling and synaptic"
date: 2008-09-25
forum: General Help
---

### Post by Repus on 2008-09-25
Hopefully this is an easy question.

I installed an app via synaptic. The process installed about a dozen dependencies. Later I uninstalled the app and noticed it did not uninstall the dependencies. 

How do I 
...(A) Identify chronologically what I previously installed via synaptic so I can 
...(B) Uninstall the dependencies that don't need anymore.

Alternately Im open to suggestions that don't follow my nice (A)(B) thingy. Basically how to I get rid of the crud I dont need anymore?

Thanks in advance

---

### Post by ad_267 on 2008-09-25
I don't know if there's an option in Synaptic but you can go to applications - accessories - terminal and enter:
```
sudo apt-get autoremove
```
to automatically remove stuff you don't need anymore.

---

### Post by Bakon Jarser on 2008-09-25
Use his autoremove advice.  For (A) go to File > history.

---

### Post by ad_267 on 2008-09-25
Just found another option.

In Synaptic go to Settings - Filters and add a new filter and call it "Autoremovable" or something then Deselect All and tick "Automatic removable" then ok. Now if you click on Custom Filters you can choose Autoremovable to find the packages that can be automatically removed.

---

### Post by Repus on 2008-09-25
Thanks everyone.

---

