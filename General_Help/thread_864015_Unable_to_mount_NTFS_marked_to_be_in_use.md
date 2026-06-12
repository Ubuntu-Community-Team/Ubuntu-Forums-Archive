---
title: "Unable to mount: NTFS marked to be in use"
date: 2008-07-19
forum: General Help
---

### Post by GabrielWolff on 2008-07-19
I didn't unmount an external HDD before pulling the plug, and now I got the following:

When inserting the USB cable, I get a long message (screenshot attached) that says: Sorry, man, the HDD can't be mounted, because your "NTFS is marked to be in use".

I managed to see the HDD's content by using mountpy. But then it's read-only, and I'd really like to use the drive properly.

Now, I think I understand the issue more or less, only thing is: how do I fix it?

Thanks :)

---

### Post by Tim Sharitt on 2008-07-19
I believe all you can really do is take one of the options given. If you remount the drive in windows and then unmount it cleanly, there should be no further problems. I believe the case is the same with the force option in linux, once cleanly unmounted it should mount fine the next time (though I'm not entirely sure on this one). In my experience the windows method does work permanently (unless the drive isn't cleanly unmounted again). I'm sure someone will correct me if I'm wrong.:)

---

### Post by GabrielWolff on 2008-07-19
> **Tim Sharitt said:**
> I believe all you can really do is take one of the options given. If you remount the drive in windows and then unmount it cleanly, there should be no further problems. I believe the case is the same with the force option in linux, once cleanly unmounted it should mount fine the next time (though I'm not entirely sure on this one). In my experience the windows method does work permanently (unless the drive isn't cleanly unmounted again). I'm sure someone will correct me if I'm wrong.:)

In that case: what is "the relevant line"? Where do I add the stuff? I attach a screenshot of my fstab file

:)

---

### Post by Tim Sharitt on 2008-07-19
To force the drive to mount open a terminal and enter
```
mount -t ntfs-3g /dev/sdc1 /"location to mount the filesystem" -o force
```
As long as the drive is cleanly unmounted next time it should mount fine the next time.

---

### Post by GabrielWolff on 2008-07-19
I remembered I had a WIN partition on my machine, booted it, unmounted the HDD and now it's fine. On the way I deleted and uninstalled 80% of what was there. I obviously don't need it if I forgot about it :)

Thanks eveyone!! :)

---

