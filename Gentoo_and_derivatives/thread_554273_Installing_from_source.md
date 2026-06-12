---
title: "Installing from source"
date: 2007-09-18
forum: Gentoo and derivatives
---

### Post by happysmileman on 2007-09-18
I've been using Gentoo for a few days and it's noticably (read: incredibly) faster than Kubuntu, as expected, so I want to know, as well as making it faster, what else does building a package from source do?

I'm mainly interested in how much it affects the following (if any):

Speed (obviously),
Size,
Amount of errors while running,
RAM usage,
Anything else interesting and good.

I'm already well aware of the speed since I can now have my KDE desktop loaded literally within 5 seconds of logging in (including typing startx)

---

### Post by K.Mandla on 2007-09-18
It was my understanding that specially compiled packages will run faster and take up less space than general catch-all compilations. The others I can't speak to.

(Moving to Gentoo discussion forum. ;) )

---

### Post by stmiller on 2007-09-18
Yeah that's about everything I think. A Gentoo install will use less disk space than a package-type distro also by nature.

Ubuntu and others come with a lot of stuff set up and running by default. RAID (removed as default in Feisty thank goodness), and other processes are set to run at boot whether you need them or not! The Ubuntu folks have to make a very generic universal sort of install disc so it will work so good on any machine, as Ubuntu does.

If you know what you are doing you can of course turn things off or on that are running in the background of Ubuntu to speed things up. But with Gentoo you are starting from the ground up, configuring a kernel for your machine, a make.conf and other things very specific. So there's no crap going on taking up any resources, and every package is built exactly for your machine.

---

### Post by Bachstelze on 2007-09-19
Besides the obvious performance gain of having the packages compiled specifically for your hardware, the biggest gain is smaller packages. Because you can compile only the features of a package you need, and not compile the ones you don't need, which will result in smaller RAM and disk usage (the package itself will be smaller but you will also avoid installing unneeded dependencies).

---

### Post by zaratustra on 2007-09-19
You can even make your gentoo run slower then Ubuntu if you don't profile it right:-) Compiling by itself doesn't make anything faster, ubuntu packages are also compiled once. You have to do some effort to configure and profile your system to your needs. As more you are familiar with your hardware and your needs, you can better profile you gentoo and make it use less resources. Gentoo is not just a distro, it is also way of living and using only stuff you really  need... Maybe you could get annoyed with long time compiling but it is the price we pay for ultimate customization.

---

### Post by Anonii on 2007-09-19
Ehm, compiling from source uses more HD space than binary packages. From what I remember my OpenOffice installation was 3GB in Gentoo.

---

### Post by Bachstelze on 2007-09-20
> **Anonii said:**
> Ehm, compiling from source uses more HD space than binary packages. From what I remember my OpenOffice installation was 3GB in Gentoo.

Those are the temporary files created during the compilation, they are normally deleted when it's done.

---

