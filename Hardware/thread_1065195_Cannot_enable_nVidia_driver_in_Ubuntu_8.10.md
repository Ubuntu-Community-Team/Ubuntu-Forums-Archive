---
title: "Cannot enable nVidia driver in Ubuntu 8.10"
date: 2009-02-09
forum: Hardware
---

### Post by Rocks and Water on 2009-02-09
I'm new to Ubuntu (just installed 8.10 last night) and I'm having issues with my nVidia GeForce 7900 GT/GTO driver. When I go to system / administration / hardware drivers it recommends installing version 177. When I click activate, however, it hangs during installation.

After browsing the forums, it appears that this problem is not uncommon, but I've been unable to resolve the issue by myself. Would someone please walk me through the process, keeping in mind that my Ubuntu knowledge is minimal?

Thanks

---

### Post by francocerisola on 2009-02-09
Hi, try to do this:
go to System > Administration > Synaptic Package Manager

install: "envyng-core" and "envyng-gtk"

close the package manager, and then go to Applications > System Tools > envyng

Now follow the instructions.

I hope it works!

---

### Post by Rocks and Water on 2009-02-09
I installed "envyng-core" and "envyng-gtk", but then I got stuck. I cannot find "System Tools" under "Applications". I tried to add it by going to System > Preferences > Main Menu, but whenever I try to check the box to add "System Tools" it automatically unchecks itself. Very strange...

Any thoughts?

---

### Post by zero244 on 2009-02-09
I agree usually Envyng will install your drivers ok.
If you dont install the envy gtk you wont have a front end to use Envyng.
The gtk package is right underneath the Envyng core package.
Like mentioned above install both.

---

### Post by Rocks and Water on 2009-02-09
How do I access system tools? I can't seem to add it to my Main Menu.

---

### Post by francocerisola on 2009-02-09
Don't know why it is not on the menu, but you can also open programs by typing    Alt + F2   then write envyng-gtk

---

### Post by Rocks and Water on 2009-02-09
> **francocerisola said:**
> Don't know why it is not on the menu, but you can also open programs by typing    Alt + F2   then write envyng-gtk

I tried doing that and got the following error message:

"Error stating file '/home/martin/envyng-gtk': No such file or directory"

---

### Post by Rocks and Water on 2009-02-10
Ah, I finally got it to work! Not being able to access envyng through system tools, I entered the following into the console: **sudo envyng -t**. My driver is now installed and appears to be running fine.

Thanks for the help.

---

