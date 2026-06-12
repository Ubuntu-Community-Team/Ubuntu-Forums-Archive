---
title: "[SOLVED] how to rename your home directory without messing it up"
date: 2008-08-25
forum: General Help
---

### Post by bigdee973 on 2008-08-25
i just made the grave mistake of renaming my home directory by using sudo nautilus thinking nothing would go wrong with doing it..well lucky for me i was able to use fail safe terminal to rename the home directory... i was able to 'sudo nautilus' from fail-safe terminal and it worked..i was wondering how can i rename my home directory safely? i already changed my username by going to users and groups in system..the reason i need to change it its because its causing some confusion because we have a few pc's with the same home directory name and when we ssh into it we get a little confused. ALSO, by me using sudo nautilus in fail-safe mode to rename the file was kind of lucky for me... how do i rename the file without using a GUI such as nautilus? i tried sudo rename -f /home/frank /home/dummy but it failed to rename the home directory from frank to dummy it said it couldnt because of something i dont remember...well i hope i could get help with both of my questions..thanks.

---

### Post by sisco311 on 2008-08-25
```
sudo usermod -d /home/<**new-home-here**> -m **<user-name-here>**
```

---

### Post by bigdee973 on 2008-08-25
> **sisco311 said:**
> ```
sudo usermod -d /home/<**new-home-here**> -m **<user-name-here>**
```

thank u that did the trick

---

### Post by sisco311 on 2008-08-25
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

