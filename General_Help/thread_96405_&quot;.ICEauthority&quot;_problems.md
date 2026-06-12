---
title: "&quot;.ICEauthority&quot; problems"
date: 2005-11-28
forum: General Help
---

### Post by kinghajj on 2005-11-28
Occaisionally, when I try to login, it gives me an error that "Your X session lasted less then 10 seconds...." Appearently this is caused by the sudden changing of the file "~/.ICEauthority"'s permissions to not allow me to read it. It was originally owned by root, but I changed that to myelf--hopefully that fixes it.

Anyone know what caused this?

---

### Post by rawman_k on 2005-11-28
I have the same problem. After /ect/gdm/XSession: Beginning session setup ... there are errors because the file /home/me/.ICEauthority is not found. I haven't deleted anything.

---

### Post by rawman_k on 2005-11-28
I've found something : [http://www.ubuntuforums.org/showthread.php?t=73961&highlight=ICE+authority](http://www.ubuntuforums.org/showthread.php?t=73961&highlight=ICE+authority)

---

### Post by rawman_k on 2005-11-28
It worked :smile: 

enter this:    sudo chown yourusername .ICEauthority

---

