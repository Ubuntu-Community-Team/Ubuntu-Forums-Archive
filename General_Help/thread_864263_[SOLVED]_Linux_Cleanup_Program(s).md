---
title: "[SOLVED] Linux Cleanup Program(s)"
date: 2008-07-19
forum: General Help
---

### Post by gali98 on 2008-07-19
Hey Guys,
   So I know that I have seen and even used some kind of program to clean out various unneeded files, i.e. tmp and icon cache and the like, but for the life of me I cannot find anything by searching google. It does not have to be fancy, a simple command line will work, I just need somthing that will work.
Any Suggestions? Thanks,
Kory

---

### Post by sports fan Matt on 2008-07-19
Have you seen this post: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by gali98 on 2008-07-19
Thanks that is a start, but I also want to clear out various caches....:)
Kory

Thanks for quick reply!

---

### Post by gali98 on 2008-07-19
I tried kdirstat, but it wasn't what I was really looking for....
Kory

---

### Post by hyper_ch on 2008-07-19
what various caches?

---

### Post by gali98 on 2008-07-19
icon cache of like nautilus gnome. Stuff like that. I'm not really sure what I did before, it was like a year ago... I think it was just some command I ran.

---

### Post by kpkeerthi on 2008-07-19
To clean nautilus cache:
```
find ~/.thumbnails -name "*.png" -atime +7 -exec rm '{}' ';'
```
**Note:** This will delete thumbnails that were not accessed in the last 7 days. In other words, it keeps the mostly accessed thumbails.

---

### Post by gali98 on 2008-07-20
Thanks so much... SOLVED
Kory

---

