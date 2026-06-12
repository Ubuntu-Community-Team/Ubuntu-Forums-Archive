---
title: "CP command"
date: 2008-10-06
forum: General Help
---

### Post by marcon00 on 2008-10-06
Hello...

i know how to operate with cp, but i want to copy paste within subfolder of the folder im copying from without typing whole directory

example :

cp /home/user/pictures/weekend /home/user/pictures/weekend/resized

the reason behind this is that i want to create a simple bashrc alias that will :
1. create new subfolder
2. copy all images to the subfolder
3. resize it using mogrify -resize 640 *.jpg  :)

```

alias foto='mkdri resized && cp * && cd resized && mogrify -resize 640

```

problem is in cp part :p any suggestions ??

---

### Post by Iowan on 2008-10-06
Using your example, if you **cd /home/user/pictures/weekend** you *should* be able to **cp *.jpg ./resized**

---

### Post by jerome1232 on 2008-10-06
```
cd /home/user/pictures/weekend
cp *.jpg resized/
```

as long as you don't prepend the directory with a / it looks in the present working directory.

---

