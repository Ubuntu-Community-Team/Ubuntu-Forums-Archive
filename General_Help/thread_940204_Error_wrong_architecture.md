---
title: "Error wrong architecture?"
date: 2008-10-06
forum: General Help
---

### Post by jimi_hendrix on 2008-10-06
im trying to install the Awsome Desktop Enviroment and got to the point where i need to install libconfuse

i downloaded the .deb package but it seems that its for 32 bit ubuntu and i have 64 bit

i had this problem before and tried to search for the post but i cannot find it

i have an intel processor

any help would be great

thanks in advance

---

### Post by jerome1232 on 2008-10-06
If you want to force it's install; I have in one instance had this break things so yeah you've been warned.
```
sudo dpkg -i --force-architecture path-to-deb/file
```

---

