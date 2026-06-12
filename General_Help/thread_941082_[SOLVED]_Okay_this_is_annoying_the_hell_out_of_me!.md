---
title: "[SOLVED] Okay this is annoying the hell out of me!"
date: 2008-10-07
forum: General Help
---

### Post by Lord Xeb on 2008-10-07
I have 2 files stuck in the trash and none of the things that I have tried didn't work. Deleting the trash cache doesn't work and I cannot even access the trash with root nautilus e_e. I will get the following: 

```
The contents of this folder cannot be displayed.

Sorry, couldn't display all the contents of "trash": Operation not supported
```

What the hell is going on here? I can access the trash just fine when I do it normally. If i try and delete them, it says that permission is denied. What should I do? Let me know if I need to give any further information on this subject.

---

### Post by christianvaldes on 2008-10-07
have you tried?

sudo nautilus

then File --> Empty Trash

---

### Post by nick09 on 2008-10-07
Well restore the files and you need to change the permissions. Then you can get rid of them.

---

### Post by Lord Xeb on 2008-10-07
can't already gone e_e

It say that they do not exist, but when I go an look at the trash itself normally, I can see the two files sitting there.

---

### Post by RiceMonster on 2008-10-07
I had this problem back when I was using gnome once. You can manually delete them from the command line (use sudo rm -f). I honestly forget where the folder is right now, but I think its somewhere in ~/.gnome2 or ~/.gconf or something along those lines. The folder name is Trash, I know that. I'd find it for you, but I don't use nautilus.

---

### Post by christianvaldes on 2008-10-07
so the files are gone....
the problem is resolved?

---

### Post by billgoldberg on 2008-10-07
> **christianvaldes said:**
> have you tried?

sudo nautilus

then File --> Empty Trash

You mean

```
gksudo nautilus
```

--

Sounds like a bug, do as the user with the girly manga avatar ( :p ) suggested. Might work.

---

### Post by christianvaldes on 2008-10-07
> **billgoldberg said:**
> You mean

```
gksudo nautilus
```

--

Sounds like a bug, do as the user with the girly manga avatar ( :p ) suggested. Might work.

Does it make a difference?
I just tried both commands and they do the same thing...
thou if you know the difference I would appreciate the reason...
in mean time I will look for the reason.
Thanks

---

### Post by billgoldberg on 2008-10-07
> **christianvaldes said:**
> Does it make a difference?
I just tried both commands and they do the same thing...
thou if you know the difference I would appreciate the reason...
in mean time I will look for the reason.
Thanks

For graphical applications launched as root it is advised to use "gksudo" instead of "sudo".

You use "sudo" only in the terminal.

Most of the time it doesn't matter. Like launching gedit with sudo is pretty safe, I do it myself all the time.

But everything else I use gksudo for.

If you want to know why it's advised to use gksudo instead of sudo to launch GUI apps, this might be a good read:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by LaRoza on 2008-10-07
Moved to General Help.

Trash is in:
```

~/.local/share/Trash

```

Delete with:

```

sudo rm -r .local/share/Trash/*

```

---

### Post by christianvaldes on 2008-10-07
> **billgoldberg said:**
> For graphical applications launched as root it is advised to use "gksudo" instead of "sudo".

You use "sudo" only in the terminal.

Most of the time it doesn't matter. Like launching gedit with sudo is pretty safe, I do it myself all the time.

But everything else I use gksudo for.

If you want to know why it's advised to use gksudo instead of sudo to launch GUI apps, this might be a good read:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks so much.

---

### Post by Lord Xeb on 2008-10-07
Okay solved Thanks so much LaRoza

---

### Post by hman469 on 2008-10-07
> **LaRoza said:**
> Moved to General Help.

Trash is in:
```

~/.local/share/Trash

```

Delete with:

```

sudo rm -r .local/share/Trash/*

```


Thanks LaRoza I was having the same problem.

---

