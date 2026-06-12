---
title: "Kernal Problem"
date: 2008-07-20
forum: General Help
---

### Post by Killaspike on 2008-07-20
I am following this guide here: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675) for installing x-fi drivers by recompiling my kernal but I get stuck near the end I get this error in my terminal:

ryan@ryan-desktop:/usr/src/linux$ cp /boot/config-`uname -r` ./.config
cp: cannot create regular file `./.config': Permission denied


Why is it not letting me do this?

---

### Post by iaculallad on 2008-07-20
> **Killaspike said:**
> I am following this guide here: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

for installing x-fi drivers by recompiling my kernal but I get stuck near the end I get this error in my terminal:

ryan@ryan-desktop:/usr/src/linux$ cp /boot/config-`uname -r` ./.config
cp: cannot create regular file `./.config': Permission denied


Why is it not letting me do this?

That should be:

```
sudo cp /boot/config-`uname -r` ./.config
```

---

### Post by Killaspike on 2008-07-20
> **iaculallad said:**
> That should be:

```
sudo cp /boot/config-`uname -r` ./.config
```


Wow I'm an idiot, thanks.

---

### Post by Killaspike on 2008-07-20
When I save the menu config setting I get this error:

Error during writing of the kernel configuration.
Your kernel configuration changes were NOT saved.

make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2


Why isn't it saving the menuconfig?

---

