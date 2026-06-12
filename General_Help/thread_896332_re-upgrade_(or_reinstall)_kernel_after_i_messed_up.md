---
title: "re-upgrade (or reinstall) kernel after i messed up"
date: 2008-08-21
forum: General Help
---

### Post by nlz on 2008-08-21
I had kernel 2.6.24-19-generic, but then I installed some driver from Arakhne for my motion eye webcam and my computer wouldn't boot anymore on that kernel. It stuck on 'loading hardware drivers'. So then I just started up in 2.6.24-18-generic which i still had on my HD, and I deleted the kernel and the related files form /boot and menu.lst. 

But now I cannot upgrade anymore to 2.6.24-19! I also cannot choose to reinstall it in synaptic. In synaptic it is still mentioned as installed. Should I uninstall and then reinstall?

Thanks

---

### Post by Archmage on 2008-08-21
> **nlz said:**
> Should I uninstall and then reinstall?

I think that is the best way to resolve the situation.

Please never delete a program directly on the harddrive. Always use Synantec.

---

### Post by nlz on 2008-08-21
but if i select this in synaptic, it also wants to uninstall linux-generic, linux-image-generic, and linux restricted-modules-generic. Will my other kernels still work then?

---

### Post by nlz on 2008-08-26
* bumptiedum *

---

### Post by jedi-penguin on 2008-08-26
You can try install another kernel, and boot into it. Then trouble shoot the problem one.

---

### Post by nlz on 2008-08-26
The problem is not that i cannot boot, i can perfectly boot into 2.6.24-18-generic, but i want 2.6.24-19-generic back. I cannot just add it in synaptic because i removed it manually.

So: is it a problem that linux-generic, linux-image-generic, and linux restricted-modules-generic packages get uninstalled when I uninstall 2.6.24-19-generic in Synaptic in order to reinstall it?

---

### Post by jedi-penguin on 2008-08-26
linux-generic, linux-image-generic depends on the most current linux-image-$version-generic. I don't think there is any harm uninstalling them. I saw someone did the same thing in this thread: 
[https://answers.launchpad.net/ubuntu/+question/36539](https://answers.launchpad.net/ubuntu/+question/36539)

---

### Post by nlz on 2008-08-27
thanks! it worked!

---

### Post by Malac on 2008-08-27
Package->Force Version in Synaptic can sometimes be used on those packages to step them back to the previous versions.

---

### Post by mssever on 2008-08-27
> **nlz said:**
> So: is it a problem that linux-generic, linux-image-generic, and linux restricted-modules-generic packages get uninstalled when I uninstall 2.6.24-19-generic in Synaptic in order to reinstall it?
Once you've got your problems sorted out, go ahead and reinstall those packages. They aren't necessary for a running system, but without them you won't get any kernel updates.

---

