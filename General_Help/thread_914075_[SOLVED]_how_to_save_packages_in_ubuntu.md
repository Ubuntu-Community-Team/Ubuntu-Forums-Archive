---
title: "[SOLVED] how to save packages in ubuntu"
date: 2008-09-08
forum: General Help
---

### Post by Louis de Broglie on 2008-09-08
Hi,

Every time i install ubuntu, i have to redownload and reinstall some packages. I would like to know if it is possible to save the packages i downloaded and then after reinstalling ubuntu I just install them from my backup packages ? :)

---

### Post by Oldsoldier2003 on 2008-09-09
Moved from the Tutorials and tips moderation queue to General Help. Please don't post support requests to T&T.

---

### Post by Oldsoldier2003 on 2008-09-09
> **Louis de Broglie said:**
> Hi,

Every time i install ubuntu, i have to redownload and reinstall some packages. I would like to know if it is possible to save the packages i downloaded and then after reinstalling ubuntu I just install them from my backup packages ? :)

You might consider [APTonCD]("http://sourceforge.net/projects/aptoncd") If downloading the packages again is a problem for you because of bandwidth. You could also create an image of a clean install using partimage. I hope these ideas are helpful in gettting you started down the right path.

---

### Post by loell on 2008-09-09
or you can also get those downloaded packages from

```
/var/cache/apt/archives
``` directory.

---

### Post by Louis de Broglie on 2008-09-09
Thanks to both of you for these information.:)

---

### Post by Louis de Broglie on 2008-09-11
So if I save the files somewhere in my hard drive. What do I have to do after reinstalling ubuntu to install them from hard drive ? :)

---

### Post by cmay on 2008-09-11
hi.
i have to ways i do myeself. one is to use apton cd. that way i have a cdrom that i can use as source. the other is i save my debian packages on a usb stick and just install them with gdebi package installer. i recommend apton cd .
hope it helps.

---

### Post by Irihapeti on 2008-09-11
You can also make a personal repository. This is just a directory on your hard drive with .deb packages in it. The full instructions are here:

[https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories](https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories)

---

### Post by Louis de Broglie on 2008-09-12
> **cmay said:**
> 
 one is to use apton cd. that way i have a cdrom that i can use as source. 
Can you explain what is apton cd ? :) Btw ,the idea of personal repository is cool.

---

### Post by Irihapeti on 2008-09-12
APTonCD is like a repository on a CD or DVD. If you want to install a package that is on the CD, you are asked to insert the CD, and all the dependencies are taken care of, too.

Because I'm on a dialup I keep all my .debs in a personal repository, and when it gets to about 650MB, I make an APTonCD disk. I can then delete all the files in the personal repository and start again.

The disk is also useful for doing a new install of Ubuntu on another machine.

---

### Post by Louis de Broglie on 2008-09-13
So how do I create such CD ? Just burn a CD with the packages then insert the CD and start the package manager and click add CD-ROM ?:) Or, I need to do something more to make it work ? :)
[B]
Edit : Ah, so stupid of me. You already mentioned what is :-p. Thanks, i installed it from synaptic :)[/B]

---

