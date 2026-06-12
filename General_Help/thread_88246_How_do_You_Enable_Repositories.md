---
title: "How do You Enable Repositories"
date: 2005-11-09
forum: General Help
---

### Post by Drifter on 2005-11-09
I am trying to learn how to compile a kernel.  I am using tseliot's guide for newbies, it says before u start be sure to have all rpositories enabled.  How do u do that and how do u know if u have then all enabled.  Thanks for any help on this.

---

### Post by aysiu on 2005-11-09
Why are you trying to compile a kernel? I've never done this before. I'm just curious as to why you think it's necessary.

If your repositories are enabled, you should be able to type ```
sudo apt-get update
``` in a terminal and get no errors.

---

### Post by Noah0504 on 2005-11-09
```
sudo gedit /etc/apt/sources.list
```
Now just uncomment all of the repositories for them to be enabled.

---

### Post by Drifter on 2005-11-09
I don't think it is necessary, I just want to learn how to do it.  I want to lean as much as I can about linux.  Before I could answer your post, I lost firefox again, it just goes off at random sometimes it lasts for an hour and sometimes it get goes when it wants to.

---

### Post by Noah0504 on 2005-11-09
[QUOTE=Drifter]I don't think it is necessary, I just want to learn how to do it.  I want to lean as much as I can about linux.[/QUOTE]
Well, now you know how.  :)

---

### Post by Drifter on 2005-11-09
O.K. how do I uncomment the repositories

---

### Post by Noah0504 on 2005-11-09
[QUOTE=Drifter]O.K. how do I uncomment the repositories[/QUOTE]
Just remove the # before the repository entry.

---

### Post by Drifter on 2005-11-09
Some of them have two ## of these do I remove both of them

---

### Post by Noah0504 on 2005-11-09
[QUOTE=Drifter]Some of them have two ## of these do I remove both of them[/QUOTE]
You don't have to uncomment those.  They just describe the under-lying repositories.

---

### Post by Drifter on 2005-11-09
Oh I see, now I am going to try the kernel again.  Thanks for the help, I will need more I'm sure.

---

### Post by Drifter on 2005-11-09
Well, I thank u very much for you help with the repositories.  I just finished following tseliot's how to compile a new kernel for newbies and I finally got it right.  Now that I have compiled a kernel, unforunatley for me I still don't know what I did, but it is a start.

---

