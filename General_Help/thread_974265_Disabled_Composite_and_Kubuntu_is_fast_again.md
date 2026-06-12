---
title: "Disabled Composite and Kubuntu is fast again"
date: 2008-11-07
forum: General Help
---

### Post by ashrack on 2008-11-07
have been using Intrepid since RC version and it was so sluggish. After nobody on the forums gave me any help I was in the process of installing Sidux which is said to be faster than Ubuntu. 
But today I remembered that Kubuntu nowadays ships with Composite enabled in XORG. So I added this to xorg.conf
```
Section "Extensions"  
Option "Composite" "Disable"  
EndSection
```
and KDE 4.1 is not sluggish anymore even thou I never had desktop effects enabled.

Was the reason for my slow 2d rendering because I have such a slow GPU, and if it is so why isn't composite disabled for GPU that are this slow?

---

