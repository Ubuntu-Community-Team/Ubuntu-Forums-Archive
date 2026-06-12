---
title: "Menu Config Not Saving"
date: 2008-07-20
forum: General Help
---

### Post by Killaspike on 2008-07-20
When I save the menuconfig setting I get this error:

Error during writing of the kernel configuration.
Your kernel configuration changes were NOT saved.

make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2


Why isn't it saving the menuconfig?

---

### Post by iaculallad on 2008-07-20
For the changes to save on configuration files, you should have the privilege to do it. As in:

```
gksudo gedit /location/of/menuconfig
```

or

```
sudo nano /location/of/menuconfig
```

---

### Post by Killaspike on 2008-07-20
> **iaculallad said:**
> For the changes to save on configuration files, you should have the privilege to do it. As in:

```
gksudo gedit /location/of/menuconfig
```

or

```
sudo nano /location/of/menuconfig
```

I dont understand how that helps me save the file? What do I do once I put those commands in?

I am totally new to Linux, this is my first time really getting into it.

---

### Post by iaculallad on 2008-07-20
> **Killaspike said:**
> I dont understand how that helps me save the file? What do I do once I put those commands in?

I am totally new to Linux, this is my first time really getting into it.

For every system configuration files that needs to be edited in Ubuntu, it requires you to edit it as a privilege user so you could save any changes made on that file.
Issuing the commands above will open your menuconfig file for editing, with a write/save access since you issued the gksudo Or sudo. Be sure to input the correct authentication before you can start saving the file.

---

### Post by Killaspike on 2008-07-20
It is still giving me the same error

This is the exactly what terminal shows:

ryan@ryan-desktop:/usr/src/linux$ make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig


Error during writing of the kernel configuration.
Your kernel configuration changes were NOT saved.

make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2
ryan@ryan-desktop:/usr/src/linux$

---

### Post by Killaspike on 2008-07-20
I am trying to follow this guide: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675) but im having some trouble with the menuconfig part.

---

### Post by iaculallad on 2008-07-20
> **Killaspike said:**
> It is still giving me the same error

This is the exactly what terminal shows:

ryan@ryan-desktop:/usr/src/linux$ make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig


Error during writing of the kernel configuration.
Your kernel configuration changes were NOT saved.

make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2
ryan@ryan-desktop:/usr/src/linux$

Aha, we've been discussing a different topic a while back. From this point, we could at least wait for other forum member's idea/solution with this problem.

---

### Post by Killaspike on 2008-07-20
> **iaculallad said:**
> Aha, we've been discussing a different topic a while back. From this point, we could at least wait for other forum member's idea/solution with this problem.

I just have no clue what im doing, I consider myself a pretty advanced windows user but linux is just going over my head.

---

### Post by Killaspike on 2008-07-20
This is the exactly what terminal shows:

ryan@ryan-desktop:/usr/src/linux$ make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig


Error during writing of the kernel configuration.
Your kernel configuration changes were NOT saved.

make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2
ryan@ryan-desktop:/usr/src/linux$

I am trying to follow this guide: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675) but im having some trouble with the menuconfig part.

---

### Post by tuxxy on 2008-07-20
Your link is void and couldnt you use the menu editor?

---

### Post by bodhi.zazen on 2008-07-20
Threads merged. Please do not start multiple threads on the same topic it causes confusion and duplication of effort.

---

### Post by Killaspike on 2008-07-21
> **tuxxy said:**
> Your link is void and couldnt you use the menu editor?

What is the menu editor?

I know nothing about linux

---

### Post by Killaspike on 2008-07-21
I am having such a hard time just trying to get my X-FI sound card to work, I really wanted to use Linux but if I cant even have sound whats the point?

---

### Post by bodhi.zazen on 2008-07-21
> **Killaspike said:**
> I am having such a hard time just trying to get my X-FI sound card to work, I really wanted to use Linux but if I cant even have sound whats the point?

I understand your frustration, hardware problems are frustrating ...

There is more to Linux then X-FI cards and you can get a replacement card (soundblaster) for less then $25.

---

