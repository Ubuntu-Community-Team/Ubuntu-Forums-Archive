---
title: "Locate comand"
date: 2008-09-18
forum: General Help
---

### Post by van_Zeller on 2008-09-18
Hello all,

I'm still taking baby steps on the console and I'm having some difficulty. I want to enter a command that will locate all files that have the .jpg extension and the word "small" in a certain folder. I also want to eliminate these files. I somehow managed to come to this:

```
find /media/documents/documents/Musica/ -iname '*.jpg' | grep Small | xargs rm

```

Now the problem is that most of the paths of these images have spaces in them. So when when we have an album that is called "Freaked Out And Small", the rm command tries returns this:

```
rm: cannot remove `Freaked': No such file or directory
rm: cannot remove `Out': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `Small/AlbumArt_{29C87FF2-A39F-44CE-B4EE-E3A76FBC8696}_Large.jpg': No such file or directory

```

Any ideas? Thanks

---

### Post by anotherdisciple on 2008-09-18
Why not do this?

```
rm -i /media/documents/documents/Musica/*Small*.jpg
```

It has -i, so it will ask you before removing each file.

---

### Post by ghostdog74 on 2008-09-18
> **van_Zeller said:**
> 

```
find /media/documents/documents/Musica/ -iname '*.jpg' | grep Small | xargs rm

```

Now the problem is that most of the paths of these images have spaces in them. So when when we have an album that is called "Freaked Out And Small", the rm command tries returns this:

```

find /path -iname "*Small*.jpg" -exec rm -f "{}" \;

```

---

### Post by van_Zeller on 2008-09-22
Thanks for the replies, I'm going to try again now, and if I have any doubts I'll be back.

vZ

---

