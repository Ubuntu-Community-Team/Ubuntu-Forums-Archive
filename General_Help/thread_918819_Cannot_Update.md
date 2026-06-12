---
title: "Cannot Update"
date: 2008-09-13
forum: General Help
---

### Post by lunarcloud on 2008-09-13
```
sam@sam-desktop:~$ sudo apt-get update
E: Method gave invalid 200 URI Start message
```

```
sudo aptitude update
E: Method gave invalid 200 URI Start message
E: Method gave invalid 200 URI Start message
E: Method gave invalid 200 URI Start message

```

And Adept just crashes.

This has been happening a lot lately (since getting back to school). I am connected, but it wont stop erroring out.

---

### Post by javaJake on 2008-09-13
Can you post your /etc/apt/sources.list file? It could be that you have third-party repositories set up that are not working correctly.

---

