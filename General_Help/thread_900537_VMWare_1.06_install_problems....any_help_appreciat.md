---
title: "VMWare 1.06 install problems....any help appreciated"
date: 2008-08-25
forum: General Help
---

### Post by kbfromvt on 2008-08-25
Hello.  I'm fairly new to Linux, but would consider myself extremely computer literate and can do about anything you'd ever want/need to do in Windows OS.  I'm trying to learn Linux by trial-and-error. 

I'm trying to install VMWare Server on my Kubuntu 8.0.4 system as I need to run Windows for some graphic design tools I use and I use VMWare on my Windows systems and like it.  

I've gone through the install, read some tutorials, gotten to the point where I thought it would work, and am now getting these errors:

[COLOR="Red"]/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)[/COLOR]

Any help is GREATLY appreciated.  Sorry if this post is in the wrong forum.

-KYLE

---

### Post by Ryadt on 2008-08-25
Try these 
```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
``````
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

---

### Post by kbfromvt on 2008-08-25
i'm pretty sure i did those already, they were posted by someone who had a tutorial on this site for this exact install.  i'll type them in just to be sure.

---

### Post by kbfromvt on 2008-08-25
> **Ryadt said:**
> Try these 
```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
``````
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

Ok, so I did that, now I get this:

root@Asus64:/usr/bin# vmware
No protocol specified
No protocol specified
root@Asus64:/usr/bin#

---

### Post by kbfromvt on 2008-08-25
All set, thanks for all your help.  Exited from ROOT prompt and ran like a charm.  Thanks.

---

