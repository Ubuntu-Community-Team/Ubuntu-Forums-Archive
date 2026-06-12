---
title: "So.., what the heck happened to my floppy drive....???"
date: 2008-10-31
forum: General Help
---

### Post by jason.b.c on 2008-10-31
i upgraded to Intrepid Ibex last night , but now when i browse to ```
computer:///
``` in the menu i have no floppy drive at all , my other drives are there and mountable but no fd0... , what gives...?


how do i get it back...?


thanks....

---

### Post by snowpine on 2008-10-31
According to this thread, you need to use 'sudo modprobe floppy'

[http://ubuntuforums.org/showthread.php?p=5933304](http://ubuntuforums.org/showthread.php?p=5933304)

---

### Post by ju2wheels on 2008-10-31
Wow, people still use that thing. Kudos to you if you still have functioning floppies.

Thats like bringing back an 8 track lmao.

---

### Post by jason.b.c on 2008-11-01
> **ju2wheels said:**
> Wow, people still use that thing. Kudos to you if you still have functioning floppies.

Thats like bringing back an 8 track lmao.

well , i still use it....


and the floppy really isn't that old anyway...

---

### Post by jason.b.c on 2008-11-09
still no floppy drive....!

---

### Post by jason.b.c on 2008-11-09
bump once again , if the drive is in my computer it HAS to work...

---

### Post by ad_267 on 2008-11-09
First link on google.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651)

Just add floppy to /etc/modules and reboot.
Might have to do "sudo mkdir /media/floppy0" first.

---

### Post by jason.b.c on 2008-11-10
bump

---

### Post by ad_267 on 2008-11-10
> **jason.b.c said:**
> bump

Don't just bump your thread without replying to my post. Did that not work?

---

### Post by lelmo85 on 2008-11-10
1.)Have you tried(code);
sudo cd /media
sudo mkdir floppy0
sudo mount -t ext2 /dev/fd0 /media/floppy0
2.)Check your cables.
Pardon my stupidity but what is "bump" aand why did it cause irritation? LMO

---

### Post by ad_267 on 2008-11-10
> **lelmo85 said:**
> 1.)Have you tried(code);
sudo cd /media
sudo mkdir floppy0
sudo mount -t ext2 /dev/fd0 /media/floppy0
2.)Check your cables.
Pardon my stupidity but what is "bump" aand why did it cause irritation? LMO

"bump" is a post to put your thread near the top of the forum if you haven't had a reply in a long time. It caused irritation because I replied, and jason.b.c completely ignored my post. If my post didn't help then he could have explained why not, and we could make some progress.

---

### Post by jason.b.c on 2008-11-10
> **ad_267 said:**
> "bump" is a post to put your thread near the top of the forum if you haven't had a reply in a long time. It caused irritation because I replied, and jason.b.c completely ignored my post. If my post didn't help then he could have explained why not, and we could make some progress.

what...?

i didn't see your post...

---

### Post by jason.b.c on 2008-11-10
> **ad_267 said:**
> Don't just bump your thread without replying to my post. Did that not work?

no it didn't..!

and that is why i bumped...

---

### Post by jdong on 2008-12-05
Does the **/dev/fd0** device exist on your system?

---

### Post by jason.b.c on 2008-12-05
> **jdong said:**
> Does the **/dev/fd0** device exist on your system?

you mean "physicaly" inside my machine -or- in ubuntu "places"...?

---

### Post by jason.b.c on 2008-12-06
so how do i get my drive working again...?

---

### Post by jason.b.c on 2008-12-06
> **lelmo85 said:**
> 1.)Have you tried(code);
sudo cd /media
sudo mkdir floppy0
sudo mount -t ext2 /dev/fd0 /media/floppy0
2.)Check your cables.
Pardon my stupidity but what is "bump" aand why did it cause irritation? LMO

```
jason@HP-Vectra-VL:~$ sudo cd /media
[sudo] password for jason: 
sudo: cd: command not found
jason@HP-Vectra-VL:~$ sudo mkdir floppy0
jason@HP-Vectra-VL:~$ sudo mount -t ext2 /dev/fd0 /media/floppy0
mount: special device /dev/fd0 does not exist
jason@HP-Vectra-VL:~$ 

```

---

### Post by Shazaam on 2008-12-06
If you follow the link that ad_267 gave you on the first page you can fix your floppy problem. Read it all of then way through before trying anything.

---

### Post by jason.b.c on 2008-12-12
well i guess i'm gonna have to just give up on this then - seeing as though i can't seem to get anymore help <slash> fix my problem here on my own...


i've tried every single suggestion made by the members here but to no avail....:confused:

---

