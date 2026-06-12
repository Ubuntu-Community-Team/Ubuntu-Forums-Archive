---
title: "1394 question - Kino"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by Staesys on 2005-05-11
I cannot use Kino to pull video from my miniDV cam unless I first go to the /dev/ directory and run this command:

```
chmod a+r+w+x raw1394
``` 

How can I add myself to a group that has permissions to use the raw1394 device, without running this command after every reboot?

-Paul

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=Staesys]I cannot use Kino to pull video from my miniDV cam unless I first go to the /dev/ directory and run this command:

```
chmod a+r+w+x raw1394
``` 

How can I add myself to a group that has permissions to use the raw1394 device, without running this command after every reboot?

-Paul[/QUOTE]


start Kino with gksudo?

gksudo kino


in run dialog

---

### Post by Staesys on 2005-05-12
Yeah, that works. When I run it as root, it doesn't have any problems. I'd like to be able to run it as a normal user though.

---

### Post by pau on 2005-05-12
```
mknod /dev/raw1394
chmod 666 /dev/raw1394
```

or

```
mknod -m 666 /dev/raw1394 c 171 34
```

or

```
mknod -m 666 /dev/raw1394 c 171 0
```

But this is a bug of old versions. You shouldn't have any problem if you are running kino 0.7.4 or so...

---

### Post by Staesys on 2005-05-12
I have 0.7.5 and when I try to capture DV when I run Kino as a normal user it tells me that /dev/raw1394 is not loaded or it couldn't read/write it. (paraphrasing)

When I run it from a root terminal, it doesn't give me the error and works just fine; likewise when I chmod the properties for /dev/raw1394 so that a normal user can access it.

How do I make it so that I can use Kino without having to mess with the permissions of the /dev/raw1394 file first?

Other than that, it works great. In fact, I've already made a DVD with it already.

-Paul

---

### Post by Napalmski on 2005-06-04
The correct way to fix the permission problem is to fix UDEV.

1) go to /etc/udev/permissions.d
2) open udev.permissions with your favourite text editor (as root)
3) search for the line

             raw1394:root:video:0600

    and change it to

              raw1394:root:video:0660

4) add yourself to the video group
5) reboot and /dev/raw1394 will have the correct permissions

Nap

---

