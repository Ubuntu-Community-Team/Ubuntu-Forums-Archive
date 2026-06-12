---
title: "CPU Won't shutdown"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by reizencroft on 2008-03-19
I had a gutsy gibbon installed on my. It's working quite fine. But i'm a bit irritated that when i shut it down, my rig wont turn off. The monitors off, but the cpu wont turn off. It's an atx, it shutdowns fine on windows. My mobo is Asus a7s333, Athlon xp 1800+.

It's bit irritating, since i still have to wait for the shutdown process before i manually push the power button.

Thanks for any help given.

---

### Post by reizencroft on 2008-03-20
Can anyone help me?

---

### Post by davidgypsy on 2008-03-20
I have the same problem on an HP compaq nx9030, so I simply reinstalled 7.04 and it works great. Hopefully 8.04 will have sorted this out.

---

### Post by panda84 on 2008-03-22
> **reizencroft said:**
> I had a gutsy gibbon installed on my. It's working quite fine. But i'm a bit irritated that when i shut it down, my rig wont turn off. The monitors off, but the cpu wont turn off. It's an atx, it shutdowns fine on windows. My mobo is Asus a7s333, Athlon xp 1800+.

It's bit irritating, since i still have to wait for the shutdown process before i manually push the power button.

Thanks for any help given.

I have the same problem here and I just figured it out how to fix it. It seems this motherboard have a broken ACPI implentation (or something bad like that) so the only possibility is to disable it.

These are the step to make it turn off properly (it found them just because Debian defaults to 486 kernel):

1) edit "menu.lst" to make sure all future kernels will have ACPI disabled (you can use the editor you prefer, this is just the simpler way):
- press Alt+F2;
- enter the following command:
```
gksu gedit /boot/grub/menu.lst
``` if you use Ubuntu or
```
kdesu kwrite /boot/grub/menu.lst
``` if you use Kubuntu;
- edit the line
```
# kopt=
``` by just adding at the end this option:
```
acpi=off
``` And **do not uncomment the line, be sure to keep the "#" at the beginning!**;
- save and exit.

2) install the following packages:
[http://packages.ubuntu.com/gutsy/powersaved](http://packages.ubuntu.com/gutsy/powersaved)
[http://packages.ubuntu.com/gutsy/linux-image-386](http://packages.ubuntu.com/gutsy/linux-image-386)
As always you have several ways to do that.
The easier one: System -> Administration -> Synaptic Package Manager; search for "powersaved" and for "linux-image-386"; select them for installation and then apply.
The faster way is:
```
sudo apt-get install powersaved linux-image-386
```
Please be sure to install "386" version, as "generic" version does not work.

Reboot and pray! :)

If it seems that the option "acpi=off" is not enabled or that the 386 kernel is not the default kernel be sure to run:
```
sudo update-grub
```

Good luck!

Bye,
Diego

---

### Post by bcummings on 2008-03-23
I have to admit that following the instructions above did solve my shutdown issue.  I created so many others though, that I'm about to pull my hair out.  I had to reinstall the restricted drivers manager,  I can't get my installation of parallels to run any longer.  AAAHHHHH!  Be careful with this!  [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by panda84 on 2008-03-24
> **bcummings said:**
> I have to admit that following the instructions above did solve my shutdown issue.  I created so many others though, that I'm about to pull my hair out.  I had to reinstall the restricted drivers manager,  I can't get my installation of parallels to run any longer.  AAAHHHHH!  Be careful with this!  [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

I think that's because of the newly installed "386" kernel. Restricted drivers are external of the kernel and so are parallells modules. That's why open source driver / software is good! :)

However, if you choose the "generic" kernel at boot time you should be able to start them properly.

---

