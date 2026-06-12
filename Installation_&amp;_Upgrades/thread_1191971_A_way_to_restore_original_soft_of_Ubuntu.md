---
title: "A way to restore original soft of Ubuntu"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by Yuugari on 2009-06-19
Hello!
This is my first post so I would like to greet everyone. :) 
I wonder if there is any way of restoring Ubuntu to a point when there were installed only programs and packages that came with a system? After I have installed my new system I downloaded many, many useless (at least for me :P) packages and small programs. Now I would like to undo all those installations. Some of them I have uninstalled via "add/remove" but some of them could be uninstalled only via Synaptic (and to be honest I really don't remember which programs I have downloaded).
And one important thing - of course I could reinstall all system but after few years of using Microsoft I got used to fight until the end (I have never reinstalled Windows (sic!)). So that option is out of the question. :)
I would appreciate all advices. :)
Best regards!

---

### Post by Mark Phelps on 2009-06-19
You could generate a list of all the packages you installed but removing them is not that simple.  You see, if a package had a dependency, and you installed through synaptic, it downloaded and installed the dependency package(s) as well.

So, to do a thorough job, you would have to remove all the dependencies, too,

But that's a much worse problem because, if the dependency was already present on your system, it didn't reinstall it.

I tried the general cleanup once, and it removed over 200 packages!! Left the system in an unbootable state.

So, unless you want to spend the next few weeks checking out each and every dependency before you remove it, it's probably a lot less work, and certainly safer, to just save off your settings and do a clean install.

---

### Post by Yuugari on 2009-06-27
Eh, that's a pity. :?
It's sad that there's no other option to restore a system... I think many beginning users would appreciate it if it could be possible to restore a system without reinstalling it.

---

### Post by kixome on 2009-06-27
there is, but you have to use software such as clonezilla, immediately after you have installed and updated it, to make a clone image of your system. then if you want to revert, you just pop in the cd created with clonezilla and you start over.

---

### Post by Yuugari on 2009-07-04
So, if someone hasn't used that kind of program from the beginning - there's no other way?

---

### Post by Sef on 2009-07-04
> So, if someone hasn't used that kind of program from the beginning - there's no other way?


Not any that I know of, except as stated in previous posts.

---

### Post by earthpigg on 2009-07-04
packages you isntalled _**not**_ from the repositories will be listed in synaptic under status -> local or obsolete.

---

