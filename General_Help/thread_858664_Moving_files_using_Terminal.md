---
title: "Moving files using Terminal"
date: 2008-07-13
forum: General Help
---

### Post by kystorms on 2008-07-13
I would like to know how one moves a file ( a theme file for Black Box) from one location to the proper location via terminal?

I tried simply moving the files using the file manager, but the error came that I was not allowed to create a file there.

I am trying to move the theme file from its present folder in my docs, to the proper location of:

/usr/share/blackbox/styles/

thank you
:KS

---

### Post by Rocket2DMn on 2008-07-13
the "mv" command is what you want.  If you don't have permissions, you may need to use sudo with it, though you shouldn't really be writing to directories that don't allow you to unless you are following some directions somewhere.
```
mv /path/to/original/file /path/to/new/location
```

---

### Post by kystorms on 2008-07-13
awesome thank you very much!

I know this is an okay folder as it just holds themes.


thank you so much again!

:popcorn:

---

### Post by sisco311 on 2008-07-13
The easiest way is to open the filebrowser as root:
```
gksu nautilus
```




In the terminal you can use the mv(move) command:
```
sudo mv source dest
```

read this for more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kystorms on 2008-07-13
> **sisco311 said:**
> The easiest way is to open the filebrowser as root:
```
gksu nautilus
```




In the terminal you can use the mv(move) command:
```
sudo mv source dest
```

read this for more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


okay, please forgive my ignorance here, but how do I open the filebrowswer as root? Do i type gksu in terminal?

*** edit -------- I found it, alt - f2 then type the directions you provided! that was as easy as pie thank you SO MUCH!!!
it worked like a charme.

---

