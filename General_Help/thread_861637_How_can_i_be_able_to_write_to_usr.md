---
title: "How can i be able to write to /usr?"
date: 2008-07-16
forum: General Help
---

### Post by YouSmeg118 on 2008-07-16
I need to put some files in the folder 

/usr/share/amsn/skins

but it says you dont have permission... this is pissing me off a lot.

How can i bypass this? Is there an admin mode or anything?

Thanks in advance...

---

### Post by tgrimley on 2008-07-16
if you're trying to do mv file /usr/share/amsn/skins/ then you just prepend with sudo like:

```
sudo mv file /usr/share/amsn/skins/
```

if you want to do it with nautilus, do ALT+F2 and type

```
gksu nautilus
```

and then just drag and drop

---

### Post by rraj.be on 2008-07-16
Try with sudo.

For example if you want to edit a text file named sno.txt you can do it by
```

sudo gedit /usr/share/amsn/skins/sno.txt
```

---

### Post by gila_monster on 2008-07-16
You need to write as root. Instead of typing

cp onefile twofile

try

sudo cp onefile twofile

sudo is the command used to perform an action effectively as root. It will ask for your password. Just type it in, and everything should copy over.

Most distributions have an actual root account. In Ubuntu, this is disabled in favor of using sudo. This is to help prevent accidental deletions of important files and that sort of thing.

---

### Post by rraj.be on 2008-07-16
> **tgrimley said:**
> ```
gksu nautilus
```

and then just drag and drop


Its not advisable to use gksu nautilus because it will give you root privilege to entire nautilus.With this you can make any change to your system files and it may lead to problem with your stability,if you have modified any important files mistakenly..

You can take control of only wanted files with sudo or gksu.

---

### Post by tgrimley on 2008-07-16
> **rraj.be said:**
> Its not advisable to use gksu nautilus because it will give you root privilege to entire nautilus.With this you can make any change to your system files and it may lead to problem with your stability,if you have modified any important files mistakenly..

You can take control of only wanted files with sudo or gksu.

Yes, but same applies for doing sudo... you have to be careful either way.  It's easier to drag and drop, select multiple files, etc with nautilus.  It's not inherently more dangerous and in fact I'd say it's harder to make big time mistakes like deleting your whole installation (though probably easier to make smaller ones like deleting files accidentally).

---

### Post by jonian_g on 2008-07-16
When I was new to Ubuntu and linux (two years ago), I was trying to copy and delete files that needed root perm. When I discovered gksudo nautilus, I was very happy. I never destroyed my system. Being new to linux doesn't make you stupid.
Ubuntu, as the slogan says is "Linux for human beings", so the best is to show to new users the easy way.

---

