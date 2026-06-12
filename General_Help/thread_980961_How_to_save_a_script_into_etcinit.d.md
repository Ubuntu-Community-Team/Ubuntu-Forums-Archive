---
title: "How to save a script into /etc/init.d"
date: 2008-11-13
forum: General Help
---

### Post by Warner White on 2008-11-13
I want to add a script to my startup. I know what the text should be. The instructions I am following say to put it in the /etc/init.d/ directory. But I don't know how to do that. How do I "put" something into that directory? Direct typing? I suspect not. The ls command reveals what appear to be files. I tried saving it from the text editor but was refused permission.

---

### Post by Amarsingh0793 on 2008-11-14
You need to save the text file as root:

1) Press ALT + F2
2) Type in 
```
gksu nautilus
```
3) When the nautilus window comes up, go to your desired destination (in your case /etc/init.d/)
4) You may now right click and click create document (and open it with text editor)
5) Enjoy

---

### Post by hictio on 2008-11-14
Don't forget to make the script, once you have created it on place like Amarsingh0793 suggested, open a terminal (Applications -> Accessories -> Terminal) and type:

```

chmod +x /etc/init.d/yuor.script (ENTER)

```

---

