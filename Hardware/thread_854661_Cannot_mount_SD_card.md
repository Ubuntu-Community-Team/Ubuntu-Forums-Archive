---
title: "Cannot mount SD card"
date: 2008-07-09
forum: Hardware
---

### Post by Formica45 on 2008-07-09
While tring to make my SD card writable I put some jibberish into the mount options dialog. Well, now everytime i try to mount it I get "Invalid mount option when attempting to mount the volume 'NEW VOLUME" dialog. So how do i change mount options if  i cant do it through the gui any more?

---

### Post by Formica45 on 2008-07-15
bump

---

### Post by stlouisubntu on 2008-10-19
Bump.  Same problem.  Anyone?  Anyone?

---

### Post by eldragon on 2008-10-19
without the gibberish.... well, you get the point...

paste what 
```

$ cat /etc/fstab

```
outputs.

---

### Post by stlouisubntu on 2008-10-22
Solution:

Open a terminal and enter:

gconf-editor

You will then see some folders.  Open the system folder.

Open the storage sub-folder.

Open the volumes sub-folder.

Open the _org_freedesktop . . . (long name)  sub-folder

Then you will see a mount options (registry key) and you will see
the bad option you entered before which you then need to clear out.

save and close (or apply or whatever.)

Your SD card should now mount properly (mine did.)

Hope this helps.

---

### Post by pirattrev on 2008-10-22
[Bump] yeah, I've been having the same problem. I'll try what the above guy said and see if that helps. thanks

---

### Post by Dj TweeX on 2009-01-29
So i opened the gconf-editor & in the storage folder there is only one sub folder & its default_options...
Any thoughts...
I am having the same problems btw

---

### Post by stchman on 2009-01-29
> **Formica45 said:**
> While tring to make my SD card writable I put some jibberish into the mount options dialog. Well, now everytime i try to mount it I get "Invalid mount option when attempting to mount the volume 'NEW VOLUME" dialog. So how do i change mount options if  i cant do it through the gui any more?

What kind of laptop do you have?  More information necessary.

---

### Post by Dj TweeX on 2009-01-30
i found a solution.
all you have to do is put this in terminal

```
sudo mkdir /media/<name of volume>
sudo mount /dev/sdb1 /media/<name of volume>
```

& to eject it,

```
sudo eject /media/<name of volume>
```

happy hunting.
~~Gabe~~

---

### Post by Dj TweeX on 2009-02-12
If this has solved your problem, Please mark the thread as solved.
Thank you,
~~Gabe~~

---

