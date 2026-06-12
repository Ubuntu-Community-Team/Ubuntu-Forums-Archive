---
title: "Acer Aspire 4250 freeze"
date: 2011-11-10
forum: Hardware
---

### Post by krisztian_andre on 2011-11-10
I managed to install ubuntu 11.10 desktop 64bit from the minimal iso adding ubuntu-desktop later, but it allways freezes after a few minutes. I cant find anything unusual in the logs. This is a fairly new laptop/chipset (amd fusion apu). I guess I have to tweak the system so I'm looking for other people with this laptop and their solutions/experiences.

---

### Post by seyavash on 2011-11-19
Hi i also face same problem with latest version of Ubuntu on Aspire 4250. After Installation and first 3rd reboot, LightDM display manager will freezing, i just found a small solution that im using dual boot ( Win 7), before directly booting to ubuntu, if i first boot into win 7 and then restart to Ubuntu, it will not freez! this problem is happening same in Mint Linux 12 rc (Lisa) 64bit, which is completely same as ubuntu 11.10. I also tried to replace gdm and kdm with LightDM, but there was same problem of freezing. The worst part about Aspire 4250 is that, there is no good hardware support for "AMD Radeon HD 6320" and its wireless adaptor "Acer Nplify 802.11", and i believe that freezing problem is because of lack of compatible drive for ATI 6320. if you be able to install suggested ATI suggested driver after installing Ubuntu, u will see there will be no graphical acceleration in both GNOME 3 and KDE plasma , specially very slow with visual effects, and it ATI Catalyst will show "Unsupported Hardware" in the corner of your screen.
lately ATI had released a new Catalyst Driver for linux platform : AMD Catalyst&#8482; 11.11 Proprietary Linux x86 Display Driver, and i tried to install it over Mint 12 and Ubuntu 11.10 , but after first or second reboot, the system was failure to boot, and graphical pop up menus and visual effects were collapsing!
i had tried different distributions: 
- Mandriva 2011 64 bit, just installing, no freezing but very slow in visual effects and wifi support.
-Fedora 15, no successful installation, it will freez during boot splash of live install CD. (Fedora 16 released lately and i haven't tried yet.)
-Open Suse 12.1 , is working properly with this laptop, very smooth and fast with GNOME 3 Shell, but wifi support is still weak!
- Mint 11 (Katya) is installed properly but no ATI graphic support, and same story with Mint 12 (Lisa)

finally i can say if they don't fix these bugs and do not release another ubuntu before 12.04 LTS, only Opensuse is the best choice, but it based on .rpm packages.

---

### Post by krisztian_andre on 2011-12-06
UPDATE:
I managed to install it with the minimal install cd and used the ethernet port to install the ubuntu-desktop meta package.
To make the wireless stop locking the machine you have to set the bios to boot from the network first.
Suspend works with the open drivers, havent tried catalyst. What does not work is hibernate and if the network cable is not plugged in it waits a few minutes for it before continuing.

---

### Post by seyavash on 2012-01-23
after changing bios setting, its my first boot, seem to be solved, also no problem with disconnecting wifi yet, btw for graphic driver im using "Gallium 0.4 on AMD PALM" which is perfectly working, and no problem with suspending, sleep or hibernate options. 
:popcorn:

---

### Post by seyavash on 2012-01-23
it really works, but please let me know how did u find the reason is because of wireless adapter and why this happened in this Acer laptop, any link or reference ....

---

### Post by krisztian_andre on 2012-03-02
Reason for what? What is this gallium driver you write about?

---

### Post by seyavash on 2012-04-02
Gallium 0.4 on palm is a name of an open driver, working good with this AMD Radeon, without any problem while standby ,.... 
by the way i still have problem with connecting wifi, its very weak in linux, any solution?

---

### Post by shantanu18 on 2012-04-16
Solution of this is different, but i really don't know why it works(only for acer).

```
 
1. Go to BIOS (Press F2 during boot)
2. Enable network boot
3. Select network boot as first boot

```

Above these steps will solve freeze problem during login. And use Open source gallium driver instead of amd catalyst driver. you can find a post [here]("http://shantanucse.blogspot.com") for enable gallium driver titled "best AMD Radeon driver for ubuntu"

---

### Post by seyavash on 2012-04-19
hey i know what u mean about network boot, its only to stop freezing, but the problem is that after all , wireless adapter (Nplify) doesnt work properly, very weak to get the signal, must sit in front of my wireless hub ( less than 5 meters ) to be able to get at least 90% of signal :D  (btw, i also tried to install using windows drivers, but not effected), any help?!?

---

### Post by krisztian_andre on 2012-12-22
> **seyavash said:**
> hey i know what u mean about network boot, its only to stop freezing, but the problem is that after all , wireless adapter (Nplify) doesnt work properly, very weak to get the signal, must sit in front of my wireless hub ( less than 5 meters ) to be able to get at least 90% of signal :D  (btw, i also tried to install using windows drivers, but not effected), any help?!?

No help, wifi range is crap. I`m looking into a replacement wifi card.

---

