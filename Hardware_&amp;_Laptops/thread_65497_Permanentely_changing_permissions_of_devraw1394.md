---
title: "Permanentely changing permissions of /dev/raw1394"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by RikoW on 2005-09-14
Hi,

I have a mini DV camera connected to my Laptop via firewire and using Kino to extract the movies and edit them. To do so, I (being in the video group) need to have read access to the firewire device /dev/raw1394

```
> ls -l /dev/raw1394
crw-------  1 root video 171, 0 2005-09-14 10:26 /dev/raw1394

``` 

Of course, I can easily change that using sudo chmod. However, using a Laptop, the permissions are set back to the above once after shutdown - restart.

How can I add read permissions to that device permanentely at boot time, so that I don't have to do that by hand everytime I would to read from the firewire port?

Thanks,
                Riko

---

### Post by RikoW on 2005-09-15
Ok, I found it out myself. So just in case someone else needs to permanently  change the permissions of any /dev/*, I post the solution here.

The key word to know about is "udev"

```
> cd /etc/udev/permissions.d/
> sudo cp udev.permissions udev.permissions.save
>sudo emacs  udev.permissions   # or gedit ...

```

Find the entry "raw1394" in the permissions file and set it to what you need:

```

#raw1394:root:video:0600
raw1394:root:video:0640

```

After reboot, the video group has from now on read permissions to the /dev/raw1394.

Cheers,

              Riko

---

