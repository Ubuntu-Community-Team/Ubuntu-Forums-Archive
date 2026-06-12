---
title: "How do I use framebuffer apps Ubuntu Desktop"
date: 2008-08-07
forum: General Help
---

### Post by blazercist on 2008-08-07
Ok so I log into my Ubuntu Hardy Desktop box through SSH and I want to use links2 -g which is framebuffer mode, but I get the error:

(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.

Someone told me I need to load a framebuffer module with modprobe?
Or I read somewhere that adding vga=    to the kernel line will solve it, but I dont know what vga is supposed to = ?

Anyone know why I get this error?

---

### Post by Vivaldi Gloria on 2008-08-07
> Anyone know why I get this error?

Sorry, I don't know. links2 -g works in my hardy without a problem and I have not modified anything, not even a vga= line.

> Or I read somewhere that adding vga=    to the kernel line will solve it, but I dont know what vga is supposed to = ?

See this thread:

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

You can only use modes available in the output of

```
sudo hwinfo --framebuffer
```

---

### Post by blazercist on 2008-08-07
thanks for that, perhaps its because of SSH?  I doubt it considering the error but hey, anything is possible.

the command you referenced above gives alot of output, many modes to choose from but, how am I supposed to choose one?  if I rememeber correctly the vga= thing is supposed to have a three digit number but none of these modes have a corresponding 3 digit number the format looks as follows:

 Mode 0x0365: 1440x900 (+5760), 24 bits
 Mode 0x0368: 1680x1050 (+1680), 8 bits
 Mode 0x0369: 1680x1050 (+6720), 24 bits

is it 369 from the 0x0369? vga=369 ?

---

### Post by Vivaldi Gloria on 2008-08-07
> the command you referenced above gives alot of output, many modes to choose from but, how am I supposed to choose one?  

Read the thread I wrote above. Especially read the first two posts there.

> thanks for that, perhaps its because of SSH?  I doubt it considering the error but hey, anything is possible.

Ahh. I just saw that you are talking about ssh. I doubt that you can get it working over ssh. ssh can forward X but I can't see how you can forward the framebuffer. But you can use ssh to setup a proxy. There are guides around for that.

---

