---
title: "No usplash at shutdown"
date: 2008-11-07
forum: General Help
---

### Post by eeegigo on 2008-11-07
I'm using "out of the box" ubuntu eee 8.04.1 (Hardy heron based) on asus
eeepc 901

I found some problems with default usplash:
In details:
1) if you shutdown there is only blank screen, without usplash.
2)If you first suspend or hibernate and then come back to your session and then choose to shutdown the usplash works regularly.
3)If you choose hibernate or suspend you don't have usplash (but I don't know if there should be an usplash in these cases!)

I searched through all web for days trying to solve this problem and I read any kind of possible fixes about this, I tried all but none works.
Someone suggested this bug is linked with network-manager. I re-installed it but without results. However probably (cause I'm not an expert) this theory says something right cause when you hibernate or suspend your session the wireless internet connection turns off. On the other hand also this "theory" isn't totally true cause if I simply turn off my wireless and then shutdown the usplash doesn't appear.

I also installed ubuntu 8.10 intrepid hibex and this bug doesn't exist
anymore, anyway I prefer ubuntu 8.04.1 distro cause it's lighter, faster
and better patched for my asus eeepc so I hope you can help me fixing this bug

---

### Post by bapoumba on 2008-11-07
Moved to General Help and added the asus eee pc tag.

---

### Post by minisori on 2008-11-07
Are your ttys blank too? If so, the problem is probably the frame buffer.

---

### Post by eeegigo on 2008-11-07
What do you mean for "ttys"? Sorry but I'm not expert... And with the buffer what can I do?
Thanks for the help

---

### Post by minisori on 2008-11-07
The text terminals, you know ctrl+alt+f1..f2....

If that is the case then take a look to this thread [http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

---

### Post by eeegigo on 2008-11-07
No they work perfectly

---

