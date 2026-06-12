---
title: "Kubuntu &amp; Ubuntu playing nice"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by joplass on 2009-10-28
I am trying to be proactive here ladies and gents.  I am currently running Jaunty (Gnome) of course I will update to Koala tomorrow.  I am wondering if I could run Kubuntu and Ubuntu on the same hard drive but separate partitions without causing too much trouble to grub.  Both partitions will have Koala with the difference that one side will be Ubuntu and the other Kubuntu. 

See I am hearing good stuff about KDE 4.3 and I want to try it without bugging Gnome.  I prefer the later for my own reasons that I don't need to get into.

---

### Post by portentum on 2009-10-28
You shouldn't have any issues with doing this. I've personally run Ubuntu, Debian and Gentoo on the same system all sharing a home partition and had no issues. It doesn't sound like you're planning to have them share a home partition, so I can't think of any reason they should conflict at all.

Good luck with it, I've played around with the latest KDE some myself and just can't seem to leave Fluxbox for long.

---

### Post by presence1960 on 2009-10-28
> **joplass said:**
> I am trying to be proactive here ladies and gents.  I am currently running Jaunty (Gnome) of course I will update to Koala tomorrow.  I am wondering if I could run Kubuntu and Ubuntu on the same hard drive but separate partitions without causing too much trouble to grub.  Both partitions will have Koala with the difference that one side will be Ubuntu and the other Kubuntu. 

See I am hearing good stuff about KDE 4.3 and I want to try it without bugging Gnome.  I prefer the later for my own reasons that I don't need to get into.

whether you use Gnome or KDE has no effect on GRUB at all. When you select an OS from the GRUB menu to boot it points to the files necessary to boot that OS. Once that is accomplished the OS then boots.

---

### Post by joplass on 2009-10-28
> **presence1960 said:**
> whether you use Gnome or KDE has no effect on GRUB at all. When you select an OS from the GRUB menu to boot it points to the files necessary to boot that OS. Once that is accomplished the OS then boots.

I was just afraid of the fact that Kubuntu and Ubuntu in Koala will have the same kernel and how will grub manage that?

---

### Post by nickrout on 2009-10-28
> **joplass said:**
> I am trying to be proactive here ladies and gents.  I am currently running Jaunty (Gnome) of course I will update to Koala tomorrow.  I am wondering if I could run Kubuntu and Ubuntu on the same hard drive but separate partitions without causing too much trouble to grub.  Both partitions will have Koala with the difference that one side will be Ubuntu and the other Kubuntu. 

See I am hearing good stuff about KDE 4.3 and I want to try it without bugging Gnome.  I prefer the later for my own reasons that I don't need to get into.

You can run them both on the same install. Just choose to log into KDE or Gnome when you log in.

---

### Post by nickrout on 2009-10-28
> **joplass said:**
> I was just afraid of the fact that Kubuntu and Ubuntu in Koala will have the same kernel and how will grub manage that?

The kernel will be the same, but the root filesystem will br different.

---

### Post by phillw on 2009-10-28
> **joplass said:**
> I was just afraid of the fact that Kubuntu and Ubuntu in Koala will have the same kernel and how will grub manage that?

GRUB is a boot loader, once you tell it what u want, that OS takes control - hence you can use grub to boot windows etc... It just tells the computer to go to the boot record for what ever system you select.

There's a great resource on grub here ....

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Regards,

Phill.

---

### Post by presence1960 on 2009-10-28
> **joplass said:**
> I was just afraid of the fact that Kubuntu and Ubuntu in Koala will have the same kernel and how will grub manage that?

it still has no effect because you can only boot one OS at a time. GRUB will point to the boot files for that OS you select and that OS will boot with the kernel selected. Even if Kubuntu and Ubuntu have the same kernel only the one installed on the OS you select to boot will be used.

---

### Post by joplass on 2009-10-28
Thanks fellas.

---

### Post by SunnyRabbiera on 2009-10-28
well why install them separately, you know you can install Kubuntu-dekstop and it will allow you to run both KDE and Gnome on the same drive without a dual boot.
KDE and Gnome do not interfere with oneanother.

---

### Post by joplass on 2009-10-29
> **SunnyRabbiera said:**
> well why install them separately, you know you can install Kubuntu-dekstop and it will allow you to run both KDE and Gnome on the same drive without a dual boot.
KDE and Gnome do not interfere with oneanother.
I don't know about now but in the past, before Ubuntu, every distro I used with both KDE and Gnome, KDE apps/programs were showing up on Gnome and vice-versa.  That I don't want.  If there is chance of that happening I wouldn't want Konqueror in Gnome.
Will this happen? Anybody?

---

### Post by nickrout on 2009-10-29
The gnome programs will be in the kde menu and vice versa.

Always the best tool for the job IMHO. GTK programs run under kde and vice cersa, but so what?

---

### Post by joplass on 2009-10-30
> **nickrout said:**
> The gnome programs will be in the kde menu and vice versa.

Always the best tool for the job IMHO. GTK programs run under kde and vice cersa, but so what?

So what?  What is this gestapo type of deal?  If you don't like what someone wrote just move on pal.  
I am talking about MY computer not yours.

---

### Post by nickrout on 2009-10-30
> **joplass said:**
> So what?  What is this gestapo type of deal?  If you don't like what someone wrote just move on pal.  
I am talking about MY computer not yours.

No No sorry just making sure you know you don't need two separate installs to have the alternatives of gnome and kde. Seems like a waste to me (waste of disk space, waste of time to reboot (as opposed to logging out and back in).But as you say its your computer, go for it, it will present no real problem. Good luck, and any problems do post back.

---

