---
title: "Please help me install this"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Vibin Lakshman on 2009-11-08
When I try to install Google gears , I found this info

## What does Gears require to be compatible with my Linux system?           
If you'd like to run the Gears for Firefox on a Linux (32-bit) platform, please make sure your system has glibc 2.3.5 or higher and libstdc++6 (Gears 0.3) or libstdc++5 (Gears pre-0.3). 


Can anyone help me to install those , coz i'm not able to do so

---

### Post by Lateralis on 2009-11-08
They are just a couple of packages/libraries that are needed by Google Gears to run properly.  To install them you can either use the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) or you can use the command line.  I'll describe how to install them using the command line as it is easier for me. =P  

Fire up a terminal: Applications -> Accessories -> Terminal.  Then type:

```

sudo apt-get install libstdc++6  glibc-2.10-1

```

---

