---
title: "uvcvideo module &amp; webcam light constantly on"
date: 2009-03-10
forum: Hardware
---

### Post by IraGainesUK on 2009-03-10
Hello all, (hope this is the right place).

I recently reformatted my hard drive (Dell XPS M1530) and installed Vista and Ubuntu back onto the machine.  Before the wipe, I also had Ubuntu installed and the Webcam worked fine, yet after the reinstall (of the same flavour of Ubuntu, 8.10) the webcam light refuses to turn off after a cold boot.

When trying to restart the uvcvideo module (the module that controls the webcam in linux) using 'sudo modprobe -r uvcvideo' I get 'FATAL: Module uvcvideo is in use.'.

Trying to use something like Cheese when the webcam light is on just brings up the test bars and static corner test screen (ie, no video).

To stop the module loading at startup, I tried adding it to the blacklist, so I added 'blacklist uvcvideo' to the bottom of my '/etc/modprobe.d/blacklist' file and did a reboot.  After reboot, trying Cheese straight off doesnt work (obviously), but I am now able to manually start uvcvideo using 'sudo modprobe uvcvideo', and it all works as expected after that.

Is there any way to get around this and not have to manually load the module after every startup?

After spending a few days searching forums for more information on this, I think my mind has gone a bit funny (oh yeah, so sorry about the long winded description, its just I hate it when youre reading another post and the steps arent described fully - Im a linux n00b really! :))

Any help or thoughts would be greatly appreciated, 

Thanks, 
   Ira

---

### Post by IraGainesUK on 2009-03-12
Bump  ...  :(

---

### Post by drWeeel on 2009-04-16
I was having this problem and it was driving me crazy, i eventually narrowed down to a program called 'motion' that was being launched on startup. Uninstalling that solved it for me.

You can check to see if you have the same problem by running the following in the terminal.

```
ps -A | grep motion
```

If there is any output, you've got the same problem as me, to fix it run:

```
sudo apt-get remove motion
```

---

### Post by IraGainesUK on 2009-04-16
Ah ha!  Patience really is a virtue!  That was it, thanks so much drWeeel - problem solved.  So motion was the problem - dont even know why I had it in the first place to be honest.

Now I can use my webcam normally again - cheers. :D

---

### Post by efes50cl on 2009-07-01
my problem still continues I have Lenovo 3000 v200 . My web cam light is on and in cheese my image is dark and black and white. I don't have a "function  + short cut" to shut down the cam...

---

### Post by chmac on 2012-07-17
I had the same error message, turned out skype was using the web cam. I found that by running ```
lsof | grep video0
```, then restarted skype. Check that your web cam is /dev/video0 first, and if not, change the grep piece appropriately.

---

### Post by matt_symes on 2012-07-17
Old Thread. Closed

---

