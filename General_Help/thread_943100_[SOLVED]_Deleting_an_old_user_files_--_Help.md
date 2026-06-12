---
title: "[SOLVED] Deleting an old user files -- Help"
date: 2008-10-09
forum: General Help
---

### Post by Spades_Neil on 2008-10-09
Anyways, I went to delete an old underused profile to free up memory on my computer. However, ever since deleting the profile, all of the folders and files are stuck and locked there! D:

I'm supposed to be the admin, but I'm being denied permission to delete the files. Is there any way to get around this?

The profile I'm trying to remove is /home/julie

My mother's profile is no longer used, and never really was, so I want to delete everything. The log in is gone, but the profile contents isn't. :\

Mind explaining to me how to get around this? If you gotta use tech talk, give me step-by-step instructions because I'm not good at tech talk.

._.

---

### Post by doas777 on 2008-10-09
> **Spades_Neil said:**
> Anyways, I went to delete an old underused profile to free up memory on my computer. However, ever since deleting the profile, all of the folders and files are stuck and locked there! D:

I'm supposed to be the admin, but I'm being denied permission to delete the files. Is there any way to get around this?

The profile I'm trying to remove is /home/julie

My mother's profile is no longer used, and never really was, so I want to delete everything. The log in is gone, but the profile contents isn't. :\

Mind explaining to me how to get around this? If you gotta use tech talk, give me step-by-step instructions because I'm not good at tech talk.

._.

well the easy way is to use Alt + F2 and in the dialog that pops up, enter:
```

gksu nautilus

```

this will prompt you for your password. it will then launch a folder window. this window will be running as administrator and should be able to delete the folder and it's contents. 

let me know if that does not do it, and I'll walk you through the command line way.

---

### Post by kerry_s on 2008-10-09
did you try a root nautilus?

press alt+f2, type> gksudo nautils /home

then just delete it.

---

### Post by Spades_Neil on 2008-10-09
> **doas777 said:**
> well the easy way is to use Alt + F2 and in the dialog that pops up, enter:
```

gksu nautilus

```

this will prompt you for your password. it will then launch a folder window. this window will be running as administrator and should be able to delete the folder and it's contents. 

let me know if that does not do it, and I'll walk you through the command line way.

...Interesting. It's THAT easy? *clicks*

*messes with the files until I find the one I want and delete* o.o It's gone? Wow, that easy?

*checks hidden files*

The file didn't move anywhere else, did it? It poofed pretty quick for a simple delete of a folder that big.

---

### Post by WWSmith36 on 2008-10-09
> The profile I'm trying to remove is /home/julie

My mother's profile is no longer used, and never really was, so I want to delete everything. The log in is gone, but the profile contents isn't. :\

Root nautilus is one way to go.  I´m been waiting a while for a valid case to give out this command, and this is it

```
sudo rm -rf /home/julie
```

I´m sure everyone was thinking this, but didn´t want to say it.....

---

### Post by Iowan on 2008-10-09
> **Spades_Neil said:**
> It poofed pretty quick for a simple delete of a folder that big. Accidental deletes happen instantly - intentional ones usually take longer ;) 

@WWSmith36
Yes, I was thinking that - I just don't type as fast... especially the warning.

---

### Post by doas777 on 2008-10-09
> **WWSmith36 said:**
> 
I´m sure everyone was thinking this, but didn´t want to say it.....

you read my mind. I try not to let beginners even know rm exists, except that it's bad. not that it really is if your careful.
[COLOR="Red"]
to OP: BE VERY CAREFUL USING 'rm -rf'. it can destroy all your data permenently if misused.[/COLOR]

---

### Post by doas777 on 2008-10-09
> **Spades_Neil said:**
> ...Interesting. It's THAT easy? *clicks*

*messes with the files until I find the one I want and delete* o.o It's gone? Wow, that easy?

*checks hidden files*

The file didn't move anywhere else, did it? It poofed pretty quick for a simple delete of a folder that big.

i've usually found deletes to be almost instantaneous in ubuntu, but I do use 'wipe' on occasion and it can take hours.

---

### Post by Spades_Neil on 2008-10-09
> **doas777 said:**
> you read my mind. I try not to let beginners even know rm exists, except that it's bad. not that it really is if your careful.
[COLOR="Red"]
to OP: BE VERY CAREFUL USING 'rm -rf'. it can destroy all your data permenently if misused.[/COLOR]

Pssh, I could tell already that it's not something I want to be screwing with. >_>

I'll save it for when I **want** to break my computer. :P

---

### Post by Spades_Neil on 2008-10-09
> **doas777 said:**
> i've usually found deletes to be almost instantaneous in ubuntu, but I do use 'wipe' on occasion and it can take hours.

Wipe, I'm not familiar with...

...But all that matters, is the file is gone, yes?

---

### Post by doas777 on 2008-10-09
> **Spades_Neil said:**
> Pssh, I could tell already that it's not something I want to be screwing with. >_>

I'll save it for when I **want** to break my computer. :P

lol. you'll do just fine in linuxland.

cheers,
Franklin

---

