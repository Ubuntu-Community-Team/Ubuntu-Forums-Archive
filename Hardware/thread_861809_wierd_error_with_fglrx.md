---
title: "wierd error with fglrx"
date: 2008-07-16
forum: Hardware
---

### Post by rolandixor on 2008-07-16
when I run amdcccle, openoffice 3.0 or fglrx info, I get:

```
fglrxinfo: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted

```

I can't find any fix but a downgrade, but I've had it with the old drivers and reinstalling all the time.

catalyst 8.4 works, but 8.6 gives this error.

---

### Post by zgornel on 2008-07-17
Well, at this point you should wait a few more days until 8.7 comes out ... Are you sure you installed the driver correctly and have acceleration ?

---

### Post by rolandixor on 2008-07-17
Is there no REAL solution?
I installed it correctly, and yes I have 3D accelaration, Blender 3D works fine, etc...
does anyone have a real answer?

---

### Post by rolandixor on 2008-07-17
> **zgornel said:**
> Well, at this point you should wait a few more days until 8.7 comes out ... Are you sure you installed the driver correctly and have acceleration ?

How long is a few days? I have until Saturday.

---

### Post by zgornel on 2008-07-17
> **rolandixor said:**
> How long is a few days? I have until Saturday.

If you have until saturday use 8.4 . You are not the only one who has the problem ( [http://www.phoronix.com/forums/showthread.php?t=10922](http://www.phoronix.com/forums/showthread.php?t=10922) ) and the solution is probably not trivial. Try removing the driver, the dkms modules from /var/lib/dkms and reinstall.

---

### Post by SpinDizzyMR on 2008-07-17
lol I've got this problem now too.

---

### Post by fitmik on 2008-08-17
Well, I have the very same problem and it happened when i updated from catalyst 8.6 to 8.7 so its not version related but update related. 
Probably a bad uninstall that conflicts with the new driver.

---

### Post by fitmik on 2008-08-17
> **fitmik said:**
> Well, I have the very same problem and it happened when i updated from catalyst 8.6 to 8.7 so its not version related but update related. 
Probably a bad uninstall that conflicts with the new driver.

Solved!

(Deleted all related ATI folders manually.) not sure if this did the trick.

Then installing using method 2 : [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29")

This gaves me the segmentation fault when using 
$ sudo aticonfig --initial -f

So after that i "simply" ran the driver the normal way: .(i think this did the trick)
sudo sh ati-driver-installer-8-7-x86.x86_64.run 
      
and it worked; fglrxinfo gives:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7769 Release

Im using a radeon 4850 and ubuntu hardy 32 bits.

Way too simple...

---

### Post by TimD123 on 2008-10-14
After running through Method 2 from the link above I was getting this.

To fix it I just re-ran 
sudo sh ati-driver-installer-8-7-x86.x86_64.run 
and let it reinstall/overwrite.

Hope this helps anybody else experiencing this issue.

---

### Post by manolomanolo on 2008-11-25
Same error on Ubuntu 8.10

manolo@manolo-laptop:~$ amdcccle
amdcccle: ../../src/xcb_io.c:352: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted


not sure I understant how to solve it but most of all not sure that possibile workaround is still good for Ubuntu 8.10

Thanks.

---

### Post by fitmik on 2009-02-18
You dont to follow any complex method now since the Catalyst drivers are now supporting Ubuntu. Just follow the ATI recommendations and you will be good.
Tested with catalyst 9.1 and ubuntu 8.10.

---

