---
title: "kinit: No resume image, doing normal boot"
date: 2008-12-17
forum: Hardware
---

### Post by nairboon on 2008-12-17
Hi all
I've some trubble with Ubuntu 8.10
Some days ago, something crashed and i got grub error 17. I couldn't find a solution, so I reinstalled ubuntu.
Now some days later I can't 'boot' anymore, I got that:

```
kinit: No resume image, doing normal boot
mount: mounting /dev/disk/by-uuid/{some numbers} on /root failes invalid: argument
...
...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```

after that message there comes Busybox, with a smal shell (no fdisk, sudo)
What can I do??
I tried to repaire with supergrub, got error 15, failed.
I tried boot with Knoppix liveCD, "can't use filesystem" and I got a really small shell.
I tried boot in protected mode.

---

### Post by larsomi on 2009-01-31
i have the same problem as above

and i have it since my pc crashed with no reason during login

since then always the same message

please help

thanks

---

### Post by coachmad on 2009-01-31
[FONT="Century Gothic"]ditto same problem...
rebooted got the same message have no freaking idea where to proceed. so linux god please help
BUMP
[/FONT]

---

### Post by nairboon on 2009-02-01
boot from ubuntu DVD / CD, go to the terminal and type sudo fdisk -y /dev/[your boot hd]
it'll repair all broken stuff on the hd, that helped me.

---

### Post by Si Deacon on 2009-02-11
> **nairboon said:**
> boot from ubuntu DVD / CD, go to the terminal and type sudo fdisk -y /dev/[your boot hd]
it'll repair all broken stuff on the hd, that helped me.

Hi, I've had same problem on my son's pc after updating. I'm going to try the above to repair it but can you enlighten me as to what to enter in place of '[your boot hd]'? (Bit thick you see!).

---

### Post by martinbaselier on 2009-02-11
fdisk -l will list all the available drives.
edit: since I'd never seen the fdisk -y option before, I just did a man fdisk to read the manual and it's not in there.
I think you need to do a  e2fck [boot hd] without the -y option. If you use -y, it will assume yes is the answer to all questions.
You probably want to read the question before you answer.

---

### Post by nova47 on 2009-02-26
I'm getting the same problem and I also don't understand what is meant by the -y in the fdisk option, or for that matter what typing fdisk /dev/sdx is going to do since that just opens the partitioner. Now for the newbery what does e2fck [boot hd] mean?

---

### Post by nairboon on 2009-03-02
sry, fdsik -l lists all your partions  and fsck /dev/sdx will fix it, i recommend the -y option otherwise you have to type [enter] several times

---

### Post by gonkyouka on 2009-04-10
it says there isnt a -y option..

---

### Post by Ratsock on 2009-05-26
"e2fsck -y /dev/sda1" worked for me

---

### Post by peacechicken on 2009-06-23
> **nairboon said:**
> boot from ubuntu DVD / CD, go to the terminal and type sudo fdisk -y /dev/[your boot hd]
it'll repair all broken stuff on the hd, that helped me.

What option do you select after booting from CD? "Try Ubuntu without any change to your computer" or what? I don't know how to get to Terminal to even try the other suggestions.

---

### Post by peacechicken on 2009-06-23
> **Ratsock said:**
> "e2fsck -y /dev/sda1" worked for me

Please disregard my previous response to this thread.

I was able to fix this by booting from LiveCD, going to Terminal, and running "sudo fsck /dev/sda1" which cleaned up a couple problems (don't remember what all it said) then I restarted like normal and it was able to boot up again.

My whole problem started when I had to do a hard shut down after it completely froze. I hope this doesn't happen every time I have to shut down...!

*::crossing fingers::*

---

### Post by peacechicken on 2009-06-25
> **peacechicken said:**
> I was able to fix this by booting from LiveCD, going to Terminal, and running "sudo fsck /dev/sda1" which cleaned up a couple problems (don't remember what all it said) then I restarted like normal and it was able to boot up again.

My whole problem started when I had to do a hard shut down after it completely froze. I hope this doesn't happen every time I have to shut down...!

*::crossing fingers::*

Spoke too soon, it's doing it again. This time, "fdisk -l" doesn't list *anything*, sudo fsck /dev/sda1 doesn't work, and e2fsck /dev/sda1 doesn't do anything either: 

```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: No such file or directory while trying to open /dev/sda1
```

Any ideas?

---

