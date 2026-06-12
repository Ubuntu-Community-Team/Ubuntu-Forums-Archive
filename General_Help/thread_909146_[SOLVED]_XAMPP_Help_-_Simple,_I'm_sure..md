---
title: "[SOLVED] XAMPP Help - Simple, I'm sure."
date: 2008-09-03
forum: General Help
---

### Post by immetoo on 2008-09-03
Hi, I have what I'm sure is a simple problem, but I can't get my head around it (I'm a VERY recent windows to Ubuntu convert - Still taking baby steps).

I installed XAMPP following the instructions in [this]("http://ubuntuforums.org/showthread.php?t=223410") tutorial. 

Everuthing's working fine. I can get to the XAMPP home page via [http://localhost/](http://localhost/), so the server is running. 

I created the public_html folder in my home folder and connected to the htdocs as per the example.

However, when I try to visit [http://localhost/MyUserName/](http://localhost/MyUserName/) is get a:
You don't have permission to access /MyUserName/ on this server.

I do have an index.php in the folder and presumed that I would be able to access it in that fashion, but apparently not. 

Again, I'm sure I'm just missing something stupid. Anyone any idea what that stupid thing is? 

**Ideally I'd like to be able to write directly to the htdocs folder in opt/lampp/htdocs through the GUI (not the terminal) but the owner is set as 'nobody' so I can't make permissions changes.**

Any help would be greatly appreciated. Thanks.

---

### Post by Ryadt on 2008-09-03
You can do```
gksudo nautilus
```and in there you can change the permission of the folder.

---

### Post by immetoo on 2008-09-03
aha! (no, not the band). Worked a charm. Thank you Ryadt.

---

