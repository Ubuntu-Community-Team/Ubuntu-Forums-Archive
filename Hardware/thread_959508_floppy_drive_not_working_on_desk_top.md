---
title: "floppy drive not working on desk top"
date: 2008-10-26
forum: Hardware
---

### Post by bigguy49 on 2008-10-26
Ok ..I know that some think that floppy drives are a thing of the past,but I still have photos and files I need to recover from them..and since I loaded Ubuntu 8.04 on the desk top I can't access My floppy drive ..is their something I need to do to mount this device..(New to Ubuntu and Linux so I am still learning)

---

### Post by cariboo on 2008-10-26
I haven't used hardy for a couple of months, but I know that the floppy modules does not get loaded automagically in Intrepid. Check to see if the floppy module is loaded by typing in a terminal:

```
lsmod | grep floppy
```

If the module is loaded you should see some out put with the word floppy in it. If you don't see any output insert the floppy module:

```
sudo modprobe floppy
```

You should now be able to use your floppy drive. Hurry up and get your info off of those disk as them seem to suffer from bit rot a lot quicker then they used to. :)

Jim

---

