---
title: "Several problems in Asus A52J notebook"
date: 2010-11-02
forum: Hardware
---

### Post by skamarla on 2010-11-02
I have several issues in my Asus A52J notebook; they are all probably related, but any help for either one will be appreciated:

1) The headphone jack doesn't mute the loudspeakers.
2) The webcam is upside down (and yes, I have tried all the libv4l tricks. It's still upside down).
3) The system hangs every time if I put down the lid.

I will probably have to write something for the incompatibility list, but maybe you can help me with this last shot.

Thanks in advance

---

### Post by kostas on 2010-11-15
Hi i have the same problems with my A52J.To correct the
camera in skype i found this solution.
Make a file called skype.sh in the home directory, putting on the terminal: 
sudo gedit skype.sh
Write in it the following line: 
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

start skype from terminal : sh skype.sh
or create a launcher to start skype from desktop or taskbar with command :sh skype.sh
I hope this will help.

---

### Post by skamarla on 2010-11-19
It did! Thanks a lot!

I had tried the v4l1compat.so trick, but it didn't work then. It works now, though. There was a v4l update not long ago. Perhaps that was it.

I also had to force the lib32 directory. I'm running 64-bit Ubuntu, so the default lib is lib64, but skype seems to be a 32-bit app.

So, all in all, the winning command was:

```
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

or alternatively

```
LIBV4LCONTROL_FLAGS=3 LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

The Control_flags=3 doesn't seem to be that critical, though.

Thanks again!

---

