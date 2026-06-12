---
title: "setting permissions"
date: 2008-10-03
forum: General Help
---

### Post by Tucatts on 2008-10-03
Ok, I used to know how to do this but have forgot how. Just ran rkhunter and I wanted to check the rkhunter log in the file system. The rkhunter log file is closed to me as it says I don't have permission to open the file. How do I change the permissions so I can open the file? Can't believe I can't remember, lol. Have tried to find this in the forums but no luck so far.
Thanks!

---

### Post by vishzilla on 2008-10-03
i guess the file needs root permission. use sudo to access it

---

### Post by bodhi.zazen on 2008-10-03
```
gksu gedit /path/to/rk.log_file
```

---

### Post by tonyh6243 on 2008-10-03
This helped me out...

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Tucatts on 2008-10-03
OH yeah, Thanks to all three of you.It worked and I will save the "how to" this time. Have started a log book with this kind of help items so my poor old brain can have some help remembering now and again! LOL
Thanks again

---

