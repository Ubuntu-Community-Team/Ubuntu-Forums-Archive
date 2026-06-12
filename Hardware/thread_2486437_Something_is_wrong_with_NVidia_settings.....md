---
title: "Something is wrong with NVidia settings...."
date: 2023-04-30
forum: Hardware
---

### Post by tomdixon on 2023-04-30
Hi to all,

Something is wrong with my NVIDIA settings. The list of usable tuning functions is too small. Some features are missing. 

 Re-installation causes this. Before that I had all the features. 

Is it really normal, that kernel update destroys Nvidia drivers functionality entirely? Do I really  have to uninstall Nvidia drivers before kernel update?

If it is normal I do not wonder that Linux Torvalds shows his middle finger to Nvidia stuff.  

Otherwise the Nvidia works very well. The speed is good and tested. 

Ubuntu 22.04 and Palit Geforce 3090 RTX. Nvidia 525 series drivers (it does not matter what driver, they all behave like this)

Best,

"Tomdixon"

---

### Post by oldfred on 2023-04-30
How are you installing the nVidia drivers? From Ubuntu repository or direct download from nVidia.

The Ubuntu repository versions are configured to be included in every kernel update.

3The nVidia versions are not. So if directly downloading you have to reinstall with every kernel update. Really its incorporating into kernel that has to be done.

---

### Post by tomdixon on 2023-04-30
I am installing sometimes using Ubuntu GUI from Ubuntu repository. I may also install by using command prompt from Ubuntu repository. I never use direct download from Nvidia. 


sudo apt install nvidia-driver-525 and so on. Or by pressing one single button from GUI. It depends day and the mood.

---

