---
title: "re install intel536ep dial up modem after kernel update"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by fairdoes on 2006-02-28
Yo! I've made the thread title as complete as possible in case anyone else ever needs to do this!

 I wish to download the security update that fixes the security issues in the kernel. This will mean my dial up modem is no longer installed (because the kernel is new), but i I feel sure i don't need to start from the beginning again.

 All the following code examples (in **bold**) refer to the dial up modem 'HowTo' - [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

The '3 missing packages' **gcc-3.4 etc.**, should still be in place (won't they?!).

The uncompressed Intel driver is still where it was on my desktop, the directory Intel-536 is still there and contains **Intel536.ko**

Does this mean i can reinstall from this point onwards, namely

 **sudo cp Intel536.ko /lib/modules/ etc**  ? or will the new kernel have changed something about compiling the driver?


 Don't laugh (much); I've ordered a book on Linux from the library, but it hasn't arrived yet!:D

 P.S. For fellow newbies to dial up ubuntu - the firewall (firestarter) does need starting manually, and ppp is the most reliable connection method I've used. The panel dialling applet looks good, but automatically dials when you turn on the computer - a nightmare for 'pay-as-you-go' connections.

---

### Post by towsonu2003 on 2006-03-02
If you used "make" to create the module (i.e. compile it), you'll need to do it all over again for the new kernel. new kernels need their own modules, compiled for / with their source. it's good practice ;)

---

### Post by fairdoes on 2006-03-02
Thanks! (Good practice, indeedy)

---

### Post by StefanoCole on 2006-03-03
Fairdoes, I think that before recompiling you also have to install the linux-headers of the new kernel.

Stefano

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=StefanoCole]Fairdoes, I think that before recompiling you also have to install the linux-headers of the new kernel.
[/QUOTE]
oh yes that's kinda whole point. I assumed the system update would also upgrade existing linux-headers to the new kernel's headers as well. well, while we are there, make sure /usr/src/linux is a link to the new kernle headers. Following is my system for illustration:
```

*uname -r*
**2.6.12-10-686**
*ls -l /usr/src*
(blablabla)
lrwxrwxrwx   1 root src      27 2006-02-05 22:08 **linux -> linux-headers-2.6.12-10-686**
drwxr-xr-x  18 root root   4096 2006-02-18 00:22 linux-headers-2.6.12-10
drwxr-xr-x   4 root root   4096 2006-02-18 00:22 linux-headers-2.6.12-10-386
drwxr-xr-x   4 root root   4096 2006-02-18 00:23 **linux-headers-2.6.12-10-686**
drwxr-xr-x  18 root root   4096 2005-10-17 16:37 linux-headers-2.6.12-9
drwxr-xr-x   4 root root   4096 2005-10-17 16:37 linux-headers-2.6.12-9-386
drwxr-xr-x   4 root root   4096 2005-10-26 19:27 linux-headers-2.6.12-9-686
(blablabla)

```
If it is not (although apt will update it during install, it may miss it in 0.009% of the time ;) ), then
```

sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
```

---

### Post by fairdoes on 2006-03-09
Good news!

I've installed the new kernel (security upgrade) and re-doing the dial up modem only required following the instructions from the point 

** Compiling the driver **, in the file [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) **Dail Up Modem How To**.

(bold text is to help fellow newbies!)

All the guff about build essential and the files missing from the CD can be missed out. I was pleased about this because the headers have already been 'security updated.'

I hope this makes some sense - i still haven't got the library book :)

---

