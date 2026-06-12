---
title: "Nuc8i5BEK not supported!"
date: 2018-10-05
forum: Hardware
---

### Post by gpsfreak on 2018-10-05
I was very excited to get the latest Intel Nuc8i5BEK. Then I found out Ubuntu is not installable on it. WTF??? Does anyone know if it's a driver issue or what exactly the problem is or if the issue is being worked to get it resolved?

---

### Post by Dennis N on 2018-10-05
I've seen reports that Ubuntu 18.10 beta will work on it as 18.10 has the 4.18 kernel.

---

### Post by gpsfreak on 2018-10-05
[COLOR=#3D3D3D][FONT=intel-clear]I checked with SimplyNuc. They said the reason they are not offering Ubuntu installation for the Nuc8i5BEK is some kind of driver conflict. They do offer Ubuntu OS with the previous Nuc version, Nuc7i5BNK, however, but I would rather get Intel's latest model.[/FONT][/COLOR]

---

### Post by oldfred on 2018-10-05
Another user posted this:
 How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)

---

### Post by gpsfreak on 2018-10-06
Thank you, oldfred. The first link about installing on Hades Canyon looks helpful, but I wonder if there is a broader effort to correct the problem so it's not necessary to install mesa from a ppa which is admittedly risky.

---

### Post by oldfred on 2018-10-06
When you have very new hardware it takes a while before updates are included in any distribution. 
First kernel and or drivers have to be updated, then they have to be included in a distribution. Depending on timing that can be up to a year.
And the more popular or standard the system the more like the changes will be incorporated sooner that later or even never if some very odd system. 

The 4.18 kernel in now in 18.10, but if you need 4.19 then you have to wait till probably 19.04 next year.

---

### Post by gpsfreak on 2018-10-08
Ok, thank you very much oldfred! I appreciate it.

---

