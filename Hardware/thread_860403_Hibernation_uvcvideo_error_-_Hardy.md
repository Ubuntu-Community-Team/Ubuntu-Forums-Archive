---
title: "Hibernation uvcvideo error - Hardy"
date: 2008-07-15
forum: Hardware
---

### Post by skiwithpete on 2008-07-15
Hi,

When I try to hibernate I get an error for uvcvideo

a) is there a way I can output the error to see exactly what the problem is?
b) what is uvcvideo?  What can I do to stop this error?  (though I probably won't get an answer to b until I get an answer to a)

I'm running an HP DV6934ca.  

Thanks in advance for your help.

P

---

### Post by atlas95 on 2008-07-15
I have the same problem on XPS m1330, this is not very important but i would like to remove it too !

---

### Post by sdennie on 2008-07-15
I've seen that error too (before I just removed the uvcvideo driver).  It doesn't seem to cause any problems but, you might be able to remove it by having uvcvideo automatically removed on suspend/hibernate and reloaded when the machine comes back up.  To do that, edit /usr/lib/pm-utils/defaults and make SUSPEND_MODULES look like this:

```

SUSPEND_MODULES="uvcvideo"

```

---

### Post by skiwithpete on 2008-07-15
ok, that got rid of the uvc error.  

Now, something flashes up really quickly a second before it goes down... and I only barely read it, it said something like:


> 
84.821515 suspend_device usb suspend ... usbcore return -32
could not suspend device 7-4.


anyone know what this is?

or if I can output the error so I can see it clearly?

How can I determine device 7-4?

I basically rebooted after that moment... 
//edit: actually it seems to boot, then load the hibernated file system for a successful hibernation...

Thanks for the help, feels like progress...

---

### Post by beercz on 2008-08-25
I have exactly the same problem with the error message being displayed very briefly immediately before my new lenovo 3000 n200 laptop hibernates, except my values are different at the end of "could not suspend device" (3-4 I think).

I am pretty sure it has something to do with my integrated SD Card reader, as when I resume from hibernation, I am unable to mount the card reader.

Has anyone found a solution to this, or is able tell me where the error message is logged, so I can investigate further.

Any help would be appreciated.

Thanks in advance.

---

### Post by skiwithpete on 2008-09-23
that's good info about the card reader, hope someone can help.

---

### Post by googatrix on 2008-10-23
I was going down this same route & getting both the errors mentioned above. I managed to remove the USB error by adding "usbcore" to SUSPEND_MODULES in /usr/lib/pm-utils/defaults. The full line looks like this:

```
SUSPEND_MODULES="uvcvideo usbcore"
```

Although this got rid of all the errors, it did give me a working hibernate. My laptop (HP Pavilion) was then simply shutting down rather than hibernating. Digging around led me to explore another option, s2disk. More details [can be found here]("http://backports.ubuntuforums.com/showthread.php?t=919106"). That way I finally got it to work without too much hassle.

---

