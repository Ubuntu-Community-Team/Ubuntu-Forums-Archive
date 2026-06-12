---
title: "[SOLVED] Revert to Ubuntu Provided ATI Proprietary Driver"
date: 2008-09-15
forum: General Help
---

### Post by Shiskimalii on 2008-09-15
I installed the ATI 8.8 graphics driver directly from ATI and would like to know how I could downgrade back to the Ubuntu provided proprietary driver. The new one has sceen flickering during videos with compiz and cannot do any program from wine with graphics (cannot run starcraft with 8.8.) If anyone knows how to remove the current driver or perhaps when the new 8.9 driver will be released that would be very helpful.

---

### Post by whizbaby on 2008-09-15
How did you install it? That would give a great hint about how to remove it :)

---

### Post by northern lights on 2008-09-15
How did you install the driver? .deb binary or did you compile from source?

Can you point out exactly what you installed from?

---

### Post by Shiskimalii on 2008-09-15
I compiled from source following the manual method from [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by whizbaby on 2008-09-15
try a
```
dpkg -l|grep "fglrx"
```
with the packages showing up, do
```
dpkg -r replace-with-package-name
```

then install the driver from the repositories
```
sudo apt-get install xorg-driver-fglrx    
```  
worked?

---

### Post by Shiskimalii on 2008-09-15
method 2

---

### Post by whizbaby on 2008-09-15
> **Shiskimalii said:**
> method 2
Sorry, just after finishing my post I realized how i missed that point and started to edit...look above

---

### Post by northern lights on 2008-09-15
Are you on a 32bit install?

If so, do the following:

1. Remove what you installed:
```
sudo dpkg --purge xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle

```

2. Remove fglrx from the disabled modules
```
gksu gedit /etc/default/linux-restricted-modules-common

```find the line ' DISABLED_MODULES="blah blah fglrx blah" ' and manually remove 'fglrx'

(3.) If you added to '/etc/modprobe.d/blacklist-restricted' and '...-local' remove the lines also.

4. Install old driver```
sudo apt-get update && sudo apt-get install xorg-driver-fglrx
```

---

### Post by Shiskimalii on 2008-09-15
running dpkg -l|grep "fglrx" I got
```
ii  fglrx-amdcccle                             2:8.522-0ubuntu1                                     Catalyst Control Center for the ATI graphics
ii  fglrx-kernel-source                        2:8.522-0ubuntu1                                     Kernel module source for the ATI graphics ac
ii  xorg-driver-fglrx                          2:8.522-0ubuntu1                                     Video driver for the ATI graphics accelerato

```

so do you want me to remove all of them?

Edit: Im on a 64 bit install.

---

### Post by northern lights on 2008-09-15
Yes. All three (see step1 above).

---

### Post by Shiskimalii on 2008-09-15
```
sudo dpkg -r fglrx-kernel-source
dpkg: dependency problems prevent removal of fglrx-kernel-source:
 xorg-driver-fglrx depends on fglrx-kernel-source.
dpkg: error processing fglrx-kernel-source (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 fglrx-kernel-source

```

```
 sudo dpkg -r xorg-driver-fglrx
(Reading database ... 135280 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib32/libGL.so.1' with
  different file `/usr/lib32/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx

```

Any thoughts?

---

### Post by whizbaby on 2008-09-15
Please follow northern lights lead, I completely forgot that the module gets blacklisted in the howto.,.

---

### Post by Shiskimalii on 2008-09-15
Following nothern lights I recieved

```
sudo dpkg --purge xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle
(Reading database ... 135181 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib32/libGL.so.1' with
  different file `/usr/lib32/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--purge):
 subprocess post-removal script returned error exit status 2
Removing fglrx-kernel-source ...
Removing all DKMS Modules
Done.
dpkg - warning: ignoring request to remove fglrx-amdcccle which isn't installed.
Errors were encountered while processing:
 xorg-driver-fglrx

```

Is that because I'm on a 64 bit install?

Edit: Ignore the last error because I've already got fglrx-amdcccle removed.

I cannot get the xorg-driver-fglrx package to uninstall with exit status 2. (see error above in this post)

---

### Post by whizbaby on 2008-09-15
I see the problem.,.in the howto the package is installed using a '--force-overwrite' option. It will take me a while to dig out how to revert that.
You will have to use a '--force-something' option likewise, but those can *really* break your package system if you do something wrong.

---

### Post by northern lights on 2008-09-15
with 'fglrx-kernel-source' and 'fglrx-amdcccle' removed, ```
sudo dpkg --purge --force-all xorg-driver-fglrx
``` should take care of the last nasty bit.

---

### Post by Shiskimalii on 2008-09-15
> **northern lights said:**
> with 'fglrx-kernel-source' and 'fglrx-amdcccle' removed, ```
sudo dpkg --purge --force-all xorg-driver-fglrx
``` should take care of the last nasty bit.

No it came up with the same error.

---

### Post by northern lights on 2008-09-15
> **Shiskimalii said:**
> 
dpkg-divert: rename involves overwriting `/usr/lib32/libGL.so.1' with
  different file `/usr/lib32/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--purge):
 subprocess post-removal script returned error exit status 2[/CODE]
If it still returns the above, then we'll remove that library manually.

Run ```
ls /usr/lib/libGL* -la
```and post the output here.

_After_ you got the go-ahead from someone knowing all the files, run ```
sudo rm /usr/lib/libGL*
```to remove libGL.so.1 and its friends.

Then purge xorg-driver-fglrx again.

---

### Post by Shiskimalii on 2008-09-15
```
 ls /usr/lib/libGL* -la
lrwxrwxrwx 1 root root     16 2008-07-09 04:40 /usr/lib/libGLEW.so.1.5 -> libGLEW.so.1.5.0
-rw-r--r-- 1 root root 273488 2008-02-11 09:49 /usr/lib/libGLEW.so.1.5.0
-rw-r--r-- 1 root root 519408 2008-04-05 16:05 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2008-08-23 16:56 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070002
-rw-r--r-- 1 root root 540720 2008-04-05 16:05 /usr/lib/libGLU.so.1.3.070002

```

---

### Post by whizbaby on 2008-09-15
It seems you can use dpkg-divert to solve this problem, but I dont yet get how to do it.

---

### Post by Shiskimalii on 2008-09-15
Any idea of when the 8.9 drivers will be released because if its soon I'll just wait then upgrade to that.

Edit: Never mind I found these charts here. [http://www.vr-zone.com/articles/ATI_Catalyst_Driver_Roadmap/6045.html](http://www.vr-zone.com/articles/ATI_Catalyst_Driver_Roadmap/6045.html)

---

### Post by northern lights on 2008-09-15
> **Shiskimalii said:**
> ```
 ls /usr/lib/libGL* -la
lrwxrwxrwx 1 root root     16 2008-07-09 04:40 /usr/lib/libGLEW.so.1.5 -> libGLEW.so.1.5.0
-rw-r--r-- 1 root root 273488 2008-02-11 09:49 /usr/lib/libGLEW.so.1.5.0
-rw-r--r-- 1 root root 519408 2008-04-05 16:05 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2008-08-23 16:56 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070002
-rw-r--r-- 1 root root 540720 2008-04-05 16:05 /usr/lib/libGLU.so.1.3.070002

```

You can go ahead an run```
sudo rm /usr/lib/libGL*
```

Then purge xorg-driver-fglrx again.

---

### Post by Shiskimalii on 2008-09-15
That code didnt work to delete the files, but I did manage to delete both the files using nautilus. I'm now back to the old Ubuntu provided driver.

---

### Post by northern lights on 2008-09-15
Sorted, then.

You can mark a thread as solved in the "Thread Tools", upper right-hand corner.

---

