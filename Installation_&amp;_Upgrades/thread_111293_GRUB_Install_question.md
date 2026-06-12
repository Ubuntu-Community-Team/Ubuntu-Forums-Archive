---
title: "GRUB Install question"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by beameup on 2006-01-02
I'm about to set up a dual boot Ubuntu/Kubuntu machine. Ubuntu is already installed. Is it best to just reload the GRUB installer when installing Kubuntu, or should I not install it and edit the Ubuntu GRUB menu to show Kubuntu?
Or is there another option I'm missing here?  Thanks

---

### Post by Herman on 2006-01-02
Whenever I am installing more than one Linux system I always just do the normal thing and install GRUB to MBR as usual. It means the operating system you installed first will be on the bottom of the list (Ubuntu), and the most recent (Kubuntu), will be above it in your new GRUB menu list. :D (Herman)

---

### Post by beameup on 2006-01-04
That's what I did. Funnyy thing is it lists Ubuntu as the name for both OS'es

---

### Post by kingsidy on 2006-01-04
it is not necessary to dual boot ubuntu/kubuntu. all you have to do is install kubuntu-desktop after you install ubuntu. at the login screen you can choose whether to use gnome or kde. i think that there is no point of dual booting because it is beasically the same os. you can choose to use either using the same install. if you want to use ubuntu you can just log off the kubuntu session and log into ubuntu. you can for example use the free space to install another linux distro.

---

### Post by beameup on 2006-01-06
And that's probably what I'll do. I like Ubuntu over Kubuntu, Maybe it's time to play with Mepis or Kanotix :) .

So if I wipe that partition clean, I'm guessing I'll have to edit the GRUB menu to remove the Kubuntu entries?

searching......

---

