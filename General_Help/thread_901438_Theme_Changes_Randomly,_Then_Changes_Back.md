---
title: "Theme Changes Randomly, Then Changes Back"
date: 2008-08-26
forum: General Help
---

### Post by kieonsegg on 2008-08-26
Every once and a while my theme in ubuntu will change, from my Darker-Ice theme to like a windows 95'ish plain look and it will also change the icons for the volunme control,shutdown, etc... in the task bars. It changes like this for about 15 seconds then changes back to my theme. Why is this happening?

---

### Post by rax_m on 2008-08-27
Are you sure you're not getting the plain look only when you enter in your password to run an application as a privileged user? This normally happens when you install your themes only in your home directory (/home/username/.themes directory), and it's not available to all users.

---

### Post by kieonsegg on 2008-08-27
> **rax_m said:**
> Are you sure you're not getting the plain look only when you enter in your password to run an application as a privileged user? This normally happens when you install your themes only in your home directory (/home/username/.themes directory), and it's not available to all users.

Hmmm... you might be right there but im not sure. Does sound right though. My theme is loaded in my SD card i think. It might also be in that directory. What should i do to fix this???

---

### Post by rax_m on 2008-08-28
i think you have to copy your theme directory to the /usr/share/themes directory.

---

