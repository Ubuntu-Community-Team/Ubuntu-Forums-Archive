---
title: "Repair ubuntu installed inside windows"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by kaloer on 2009-04-14
Hi,

My ubuntu installation does not work well anymore. Everytime i boots the system, i get this error:
```
Kernel panic - not syning: vfs: unable to mount root fs on unknown-block(0,0)
```

Can I repair this error using the disc? If not, can I then access my files from Windows? I have tried the DiskInternals Linux Reader, but my linux installation is not listed.

I really do not want to lose my files on the system.

//Kaloer

---

### Post by kkkkdddd on 2009-04-14
Do you know what caused this error?
Was Ubuntu working before it?

For disc related problems, I recommend program called Test Disk, which is available for both Linux and Windows.
It is in Ubuntu repository. You can run Ubuntu form Live CD, connect to the Internet and try:
```
sudo apt-get install testdisk
sudo testdisk
```

You can also try Windows version. I haven't tried it, so I don't know whether it is good. 
 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by kaloer on 2009-04-15
I don't know what caused the error. I simply opened Eclipse when it suddently shutdown.. I also had a Android emulator and Firefox open..
Ubuntu was working great before the error..

I'll try the program now,
thank you very much for your answer

---

### Post by kaloer on 2009-04-15
Great! Now it works.. Thank you very much for your help!

---

