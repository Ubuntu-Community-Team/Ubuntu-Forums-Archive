---
title: "Where do I install GRUB?"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by jbennett on 2006-02-16
I would like to configure my laptop to dual boot Windows XP and Ubuntu so I've been browsing various websites to get an idea of what this entails, and how best to go about doing it.  I think I'm going to partition the hard drive in my laptop and install Ubuntu on a new partition, but the question I have is, where do I install GRUB?  I've read differing opinions, some sources say that it should NOT be installed in the MBR (thus overwriting Windows bootloader) and others say that it should be installed in the MBR.

I'm very new to Linux and to configuring my hard drive, so I want to make sure I have a real good idea of what needs to be done before I even attempt anything.

Any help would be greatly appreciated.

Thanks.

---

### Post by psusi on 2006-02-16
Just pop in the ubuntu install cd and it will walk you through it.  It will offer to shrink the windows partition and install ubuntu to the free space.  It will automatically install grub to the MBR, which is what you want.

---

### Post by jbennett on 2006-02-16
[QUOTE=psusi]Just pop in the ubuntu install cd and it will walk you through it.  It will offer to shrink the windows partition and install ubuntu to the free space.  It will automatically install grub to the MBR, which is what you want.[/QUOTE]

Thanks, that reassures me a little bit. :)

---

### Post by aysiu on 2006-02-16
See the fifth link of my signature. You won't regret it. It's the ultimate Ubuntu and Windows dual boot guide.

You can install Grub to the MBR or not do it. I'd advise doing it, as Ubuntu's Grub will automatically add Windows to the boot menu. You have to do all sorts of virtual somersaults to get Windows to recognize Ubuntu in it's boot.ini file.

---

### Post by jbennett on 2006-02-16
[QUOTE=aysiu]See the fifth link of my signature. You won't regret it. It's the ultimate Ubuntu and Windows dual boot guide.

You can install Grub to the MBR or not do it. I'd advise doing it, as Ubuntu's Grub will automatically add Windows to the boot menu. You have to do all sorts of virtual somersaults to get Windows to recognize Ubuntu in it's boot.ini file.[/QUOTE]

I just visited that link and that webpage does an amazing job of detailing the process for installing and dual booting with Ubuntu and Windows XP.

Thanks.

---

### Post by Coelocanth on 2006-02-16
[QUOTE=jbennett]I just visited that link and that webpage does an amazing job of detailing the process for installing and dual booting with Ubuntu and Windows XP.

Thanks.[/QUOTE]

I installed Ubuntu only a couple days ago and used Herman's guide to walk me through repartitioning my hard drive so I could dual-boot. I let GRUB install to the MBR - it's the simplest solution.

Everything went really well with the repartitioning and install. The only troubles I had were with my monitor, but thanks to the help of forum members such as aysiu, Herman, Estariel, and a couple others, I got that sorted out quite quickly. Funny thing is, I've not booted into Windows hardly at all! :D 

Anyhow, I think you'll enjoy Ubuntu, just be prepared to ask questions and do some research. If you're like me and coming from years of only using Windows, it's quite shockingly different - but it's a hell of a lot of fun.

Good luck to you!

---

### Post by jbennett on 2006-02-16
[QUOTE=Coelocanth]Anyhow, I think you'll enjoy Ubuntu, just be prepared to ask questions and do some research. If you're like me and coming from years of only using Windows, it's quite shockingly different - but it's a hell of a lot of fun.

Good luck to you![/QUOTE]

Thanks for the encouragement, I look forward to learning.  I'm sure you'll see more of me in the forums!

---

