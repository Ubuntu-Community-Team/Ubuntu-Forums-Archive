---
title: "[SOLVED] Why are there so many .debs in my system?"
date: 2008-09-21
forum: General Help
---

### Post by PhaeZee5 on 2008-09-21
There 2,393 .deb files that take up 1.8 GB(!) of my hard drive, what's the deal? If this is normal, is there any way around it?

---

### Post by cszikszoy on 2008-09-21
try this:

```
sudo apt-get autoclean
```

this will remove all of the debs from your local apt cache.

---

### Post by stoneage on 2008-09-21
Please supply more information; everyone on Ubuntu has some .debs on their hard drive. Are these files installed on your system, or simply saved there ?
What files are they ?
Where are they ?

---

### Post by PhaeZee5 on 2008-09-21
[HTML]this will remove all of the debs from your local apt cache. [/HTML]

won't they just be reloaded...or not?

[HTML]Please supply more information; everyone on Ubuntu has some .debs on their hard drive. Are these files installed on your system, or simply saved there ?
What files are they ?
Where are they ?[/HTML]

They are not installed (they wouldn't be debs then)
And they (the .deb files) are located in /var/cache/apt/archives

---

### Post by louieb on 2008-09-21
Just noticed your sig says your running the alpha 6 version if 8.10. 
How did you get that - through a dist upgrade from Hardy? A fresh install? Question probably belong in the Intrepid Ibex development forum?  [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Maybe a :confused:problem or it may be a :KSfeature of the next Ubuntu release.

---

### Post by stoneage on 2008-09-21
Do you have backup-manager ?
[http://ubuntuforums.org/showthread.php?t=895769&highlight=hard+drive+full%26quot%3B%26quot%3B](http://ubuntuforums.org/showthread.php?t=895769&highlight=hard+drive+full%26quot%3B%26quot%3B)

---

### Post by cszikszoy on 2008-09-22
> **tsudrummer24 said:**
> [html]this will remove all of the debs from your local apt cache. [/html]won't they just be reloaded...or not?

[html]Please supply more information; everyone on Ubuntu has some .debs on their hard drive. Are these files installed on your system, or simply saved there ?
What files are they ?
Where are they ?[/html]They are not installed (they wouldn't be debs then)
And they (the .deb files) are located in /var/cache/apt/archives

Just run the command I posted earlier.  The reason why you have so many .debs is because you most likely did a dist-upgrade with aptitude from hardy.  Notice how all of the .debs are in /var/CACHE...  That's all it is, its a cache.  When apt downloads debs, it stores them in a local cache, then installs them.  Unfortunately, apt does not delete them by default, so over time (or when you do a dist-upgrade) you will notice that you have lots of debs in the cache.

You can safely remove them as they are no longer needed.  They won't be reloaded because the files inside the .deb are already installed.

---

### Post by mb_webguy on 2008-09-22
+1

"sudo apt-get autoclean" is your answer.

---

### Post by PhaeZee5 on 2008-09-23
I used the autoclean command, and all I see is the .debs i'm currently using, all of the responses make sense: thank you!

---

### Post by PhaeZee5 on 2008-09-23
For the record, I used a dist-upgrade from hardy.

[HTML]Do you have backup-manager ?[/HTML]

I don't.

---

