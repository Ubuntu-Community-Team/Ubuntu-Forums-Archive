---
title: "Installing packeges from source on 7.10"
date: 2008-11-09
forum: General Help
---

### Post by Bryantos on 2008-11-09
We're learning Ubuntu in a college class, but we're running it under VMware and I have no internet access, so I can't just apt-get everything I need. What I'm doing is downloading packages from the internet under windows onto my flash drive and then trying to compile them from source in Ubuntu.

Well, I want to throw Compiz Fusion on here, but so far I havn't made any progress. Tried to ./configure it, and got an error saying 
```
configure: error: C compiler cannot create executables

```

I googled it, and saw on forums that I should try installing the build essential packages first. Tried that, but got an error saying I need the dpkg-dev package installed first. I went to install dpkg-dev and received the same error I did when I tried to install compiz straight away, so essentially I went into a large circle.

Does anyone know what packages I need, or if this is even a problem with me not having packages?

Keep in mind, I'm running 7.10 under VMware. If you need any other details please ask. :)

Thanks for any help. :D

---

### Post by oldos2er on 2008-11-09
I think 7.10 was the first version of Ubuntu to come with compiz-fusion already installed, but to make it at all useful you still need the package compizconfig-settings-manager. 

 If it's at all possible to get an internet connection with your machine, do so. Otherwise it's dependency hell.

---

### Post by Bryantos on 2008-11-10
I was able to finally get a connection after a few restarts of the machine in VMware.

Still couldn't get compiz to work, but it probably has something to do with trying to install the packages out of order, some settings in compiz I was over looking, or the video cards in the boxes. (I got a whitelisted error, but was able to get through it.)

---

### Post by oldos2er on 2008-11-10
Install the package compizconfig-settings-manager. For some reason, even tho' compiz-fusion is installed by default, the ability to configure it isn't.

---

### Post by igknighted on 2008-11-10
vmware doesn't support 3d accelerated graphics, so I don't think you can use compiz.

---

