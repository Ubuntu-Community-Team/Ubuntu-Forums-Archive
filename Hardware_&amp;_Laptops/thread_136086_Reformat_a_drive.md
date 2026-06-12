---
title: "Reformat a drive"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by peppermint on 2006-02-25
I'm sure theres a tool that can do this but its doing a good job at hiding from me :P
My computer has three drives with one partition on each. The first drive is formated as ntfs and holds Windows XP. The second drive is also ntfs and acts as a data store. The third drive is ext3 for Ubuntu.

I need to reformat the second drive to vfat so both operating systems can read it. So whats the command to do the reformat? The drive is /dev/sdb5 and is 150Gb.

---

### Post by shams2 on 2006-02-25
there is parted installed, for help read: man parted, or easy way install gparted with:
aptitude install gparted
it is a nice  graphical interface.

---

### Post by cilynx on 2006-02-25
There are lots of ugly command line tools to do what you want, but for a nice all-in-one graphical solution, check out gParted

---

### Post by navilon on 2006-02-25
I suggest installing and using Gparted
```
sudo apt-get install gparted
```

---

### Post by peppermint on 2006-02-25
Thanks for the advice peeps. It worked much faster than I thought it would :D

---

### Post by peppermint on 2006-02-25
I have a couple of more problems now.
first, i can't make the drive mount at start up. However I can manually do it.

This is the command I'm using to mount the drive manually
```

sudo mount -t vfat /dev/sdb5 /mnt/data

```

and this is the instruction I've added to /etc/fstab
```

/dev/sdb5       /mnt/data       vfat    defaults,errors=remount-ro 0       1

```

Secondly, only root can write to the drive. I've tried
```

sudo chmod 777 /mnt/data -R

```

but the permissions don't go higher than 755. I can make the values lower though.

---

### Post by peppermint on 2006-02-25
Ive fixed the automount problem by changing this
```

/dev/sdb5 /mnt/data vfat defaults,errors=remount-ro 0 1

```
to this
```

/dev/sdb5 /mnt/data vfat defaults 0 0

```
In the /etc/fstab file.

However the permissions problem still persists.

---

### Post by taurus on 2006-02-25
Try

```

/dev/sdb5 /mnt/data vfat defaults,umask=0000 0 0

```

---

### Post by peppermint on 2006-02-25
Ah. Works now, thanks :)

Edit: No it didnt, i though it worked because i can now make files on the drive. However I still cant change ownerships or permissions. I keep getting "Operation not permtted" errors :rolleyes:

---

### Post by taurus on 2006-02-25
Use

```

sudo chmod 744 <filename>
sudo chown <userID> <filename>

```

---

### Post by peppermint on 2006-02-25
I have been using those commands. chmod works, chown and chgrp don't.

---

### Post by taurus on 2006-02-25
[QUOTE=peppermint]I have been using those commands. chmod works, chown and chgrp don't.[/QUOTE]
Even with sudo!!!  :confused:

---

### Post by peppermint on 2006-02-25
Yes!
*Spooky music plays in the background*
Oh my god! Root died!

---

### Post by taurus on 2006-02-25
[QUOTE=peppermint]Yes!
*Spooky music plays in the background*
Oh my god! Root died![/QUOTE]
Root died!!!  You are now in some serious hot water, my friend!!!  
What exactly do you mean root died?

---

### Post by peppermint on 2006-02-25
[QUOTE=taurus]What exactly do you mean root died?[/QUOTE]
I'm sorry if I scared you, I was joking :mrgreen:

---

### Post by taurus on 2006-02-25
[QUOTE=peppermint]I'm sorry if I scared you, I was joking :P[/QUOTE]
Don't worry.  I have a new pair of underwear on so I am good...  ;)

---

### Post by localzuk on 2006-02-26
They may be ugly but they are fully functional and useable IMO :)

---

### Post by cilynx on 2006-02-26
man fstab

search for "user"

The "user" option allows normal users to mount the device and not just root.

---

### Post by peppermint on 2006-02-26
Puting user in as an option returns the same results.

Edit: current fstab entry
```

/dev/sdb5 /mnt/data vfat auto,user,exec,rw,async,umask=0000 0 0

```

---

