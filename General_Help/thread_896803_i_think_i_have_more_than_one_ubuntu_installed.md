---
title: "i think i have more than one ubuntu installed"
date: 2008-08-21
forum: General Help
---

### Post by Smithben1983 on 2008-08-21
i think i have mopre than one ubuntu installed and i want to get the ones i dont want out of there. I found this link [http://ubuntuforums.org/showthread.php?t=245959]("http://ubuntuforums.org/showthread.php?t=245959") and i was trying to take care of it on my own but i dont know what one i dont want. i have an image of my boot screen below. i only use windows and the very top ubuntu. thanks for taking the time to read this.
[IMG]http://i300.photobucket.com/albums/nn2/smithben1983/IMG00303.jpg[/IMG]

---

### Post by lordadi on 2008-08-21
That's a differnet kernel for Ubuntu to use and is not a problem. If you want to get rid of it get StartUp Manager from the repos and limit the number of kernels to keep to 1.

---

### Post by Uchiha_madara on 2008-08-21
Don't worry ....
you have one Ubuntu Dude...

---

### Post by Nepherte on 2008-08-21
What you see here, are several kernels (read: the core of your operating system). It still is one ubuntu install though. When you update, you get new kernel updates, but you still keep the old kernel in case the new one breaks your system. If the latest one works for you, you can safely remove the old one. You can also make your boot loader to not show the different kernels, but only the last one or a specified amount as mentioned in above posts.

---

### Post by sameerds on 2008-08-21
> **Smithben1983 said:**
> i think i have mopre than one ubuntu installed and i want to get the ones i dont want out of there. I found this link [http://ubuntuforums.org/showthread.php?t=245959]("http://ubuntuforums.org/showthread.php?t=245959") and i was trying to take care of it on my own but i dont know what one i dont want. i have an image of my boot screen below. i only use windows and the very top ubuntu. thanks for taking the time to read this.

Actually what you are seeing on the screen are not versions of Ubuntu, but versions of the Linux kernel that Ubuntu uses. You probably performed some form of upgrade recently, that installed a new version of the Linux kernel (the first in the list). The other one is the older version that was running on your system until that upgrade.

You can safely ignore this screen and just hit enter to select the default. When you upgrade the next time, the older copy may go away.

But if you are interested, I think this should be filed as a bug in Ubuntu. The system has done something that confused the user. There could be a better way for the system to handle an upgrade to the Linux kernel version, without confusing the user.

---

### Post by colobix on 2008-08-21
I don't thing that screen is confusing the user.
I guess they'll understand everything when they see (Recovery Mode) and when they see a new kernel after an update.

---

### Post by sameerds on 2008-08-21
> **colobix said:**
> I don't thing that screen is confusing the user.
I guess they'll understand everything when they see (Recovery Mode) and when they see a new kernel after an update.

Here's what I think when I look at the photo posted in this thread: it looks like there are two "Ubuntu 8.04.1" on the system, with some geeky looking numbers following them, and each one has one extra entry for "Recovery Mode". The screen does not explain that in fact, its just one Ubuntu system with the option of booting into two different kernels.

I think the menu.lst should be changed, so that it shows a title line that says "Ubuntu 8.04.1" followed by the two lines each for the two kernels. The kernel lines should not say "Ubuntu" again.

I know this is not a very critical problem, and trying to do what I mention might be tricky, and not worth developer time, and all that ... but I still believe that this is confusing to the user.

---

### Post by sameerds on 2008-08-21
> **sameerds said:**
> I think the menu.lst should be changed, so that it shows a title line that says "Ubuntu 8.04.1" followed by the two lines each for the two kernels. The kernel lines should not say "Ubuntu" again.

There's another problem visible in that screenshot ... the name "Linux kernel" is not mentioned. That is wrong for two reasons ... Linux is not given credit where its due, and the geeky looking string of numbers seems to apply to "Ubuntu" in some way.

---

### Post by Seventh Reign on 2008-08-21
> **sameerds said:**
> I think the menu.lst should be changed, so that it shows a title line that says "Ubuntu 8.04.1" followed by the two lines each for the two kernels. The kernel lines should not say "Ubuntu" again.

+1 for that.  Great Idea.

---

