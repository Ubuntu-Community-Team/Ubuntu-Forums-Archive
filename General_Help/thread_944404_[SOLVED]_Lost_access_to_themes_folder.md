---
title: "[SOLVED] Lost access to themes folder"
date: 2008-10-11
forum: General Help
---

### Post by Bfhaines on 2008-10-11
Hello.
I've lost access to my themes folder. Big X on it. Tried chmod with sudo. No luck. When i check properties/permissions on the folder,it says owner and group have read/write access but i dont. Seems like root has claimed this folder.Themes are not showing in appearance prefs either.Only the one i'm using.Sure would like some help with this.
Thanks.
Bert.
Ps:I'm using Ubuntu 8.04.1

---

### Post by dhazin on 2008-10-11
If you know how to use console, you can simply do ```
sudo chown -R /path/to/your/folder <your_username>:<your_usergroup>
```
Typically your user's group will be the same as user's name.

---

### Post by dhazin on 2008-10-11
If you know how to use console, you can simply do ```
sudo chown -R /path/to/your/folder <your_username>:<your_usergroup>
```
Typically your user's group will be the same as user's name.

---

### Post by Bfhaines on 2008-10-11
Hi.Thanks for the reply. I tried what you said and it said invalid user. Maybe i'm not doing it right. My user name is bert and the path is /usr/share/themes

---

### Post by dhazin on 2008-10-11
oh, sorry.. the correct syntax for chown will be
```
sudo chown -R <your_username>:<your_usergroup> /path/to/your/folder
```

---

### Post by Bfhaines on 2008-10-11
That  did it. Thank you very much. This was the first time i've posted and got an answer and a fix within a half hour. Pretty good. Now if i can figure out how to close this thread. Have a nice day.
Bert.

---

