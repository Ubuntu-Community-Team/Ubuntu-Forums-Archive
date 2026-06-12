---
title: "[SOLVED] I cannot delete these folders!"
date: 2008-11-19
forum: General Help
---

### Post by jumboshrimp11 on 2008-11-19
So, I recently had a bit of trouble with my Windows installation, where it just wont boot anymore. But, that's now in the past, and I want to delete all the windows files off of the Windows hard drive so I can use the rest of the space. The only problem, though, is that a few of them refuse to delete! I've tried doing it normally, tried using the command
```
sudo rm -rf /media/S3A6022D501/ProgramData
```
which just gives me an error about "cannot remove directory, operation not supported". 

I would really prefer not to format the whole partition, because I do have some large collections of files on there I'd like to keep... does anybody have any advice?

---

### Post by SuperSonic4 on 2008-11-19
It is probably because it's an essential folder. 

Your best bet would probably be to back up the files and repartitions. What happens if you go into dolphin as root. Launch by typing ```
su -c 'dolphin'
``` in a konsole

---

### Post by jumboshrimp11 on 2008-11-19
If I use ```
su -c 'dolphin'
```
It just says ```
su: Authentication error

```
If I use ```
sudo su -c 'dolphin'
```
It says:```
 <unknown program name>(21449)/: KUniqueApplication: Cannot find the D-Bus session server

<unknown program name>(21439)/: KUniqueApplication: Pipe closed unexpectedly.

```

But you said that it might be an essential folder? I bet that's the problem. I'm guessing there's no way to turn it into a non-essential folder?

---

### Post by SuperSonic4 on 2008-11-19
Yeah, I forgot you're not in mandriva there, that's my bad :(
does kdesu dolphin do anything? I doubt it though =/

If it can be/how it can be changed goes beyond my expertise

---

### Post by jumboshrimp11 on 2008-11-19
No, that doesn't do anything either. Thanks for your help though!
Does anybody else know how I might go about deleting these folders?

---

### Post by jumboshrimp11 on 2008-11-19
Please?

---

### Post by Billybob97060 on 2008-11-19
you might try a built in program named "shred" it is meant to remove a file so that it cannot be accessed again by file retrieval programs in the future. for example you would type "shred -u -z -n 5 yourfilehere" see if that does anything if not, let me know :)

---

### Post by Billybob97060 on 2008-11-19
if that does no good you might also try secure-delete "apt-get install secure-delete" after installing it you will run something like "srm yourfilehere"

---

### Post by jumboshrimp11 on 2008-11-20
Wow, I just realized that all the folders are empty! I thought they were hogging all my space, but I guess I just have a lot of stuff...
My apologies, and thanks to everyone for your assistance!

---

