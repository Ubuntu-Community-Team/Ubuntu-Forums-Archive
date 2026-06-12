---
title: "DVD problem on Natty"
date: 2011-01-16
forum: Hardware
---

### Post by BothEyesShut on 2011-01-16
Hi Linux community,

Sorry if this is already a thread, but I didn't find one.

My girl has a Dell Inspiron 1501 lappy running Natty, and she was very disappointed when she couldn't get her DVD of "Deliverance" to play.  She's better off, I know, but I can't get it to work through the driver updates in synaptic package mgr nor software center.

The error we get is: "could not read from resource."

Any ideas or terminal cut-n-paste magic?

Love you guys,

-Both

---

### Post by garvinrick4 on 2011-01-16
Did you install:
libdvdcss2
```
sudo apt-get install libdvdcss2
```
rick@rick-HP-G71:~$ aptitude show libdvdcss2
Package: libdvdcss2                      
New: yes
State: installed
Automatically installed: no
Version: 1.2.10-0.3medibuntu1
Priority: optional
Section: free/libs
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Uncompressed Size: 111 k
Depends: libc6 (>= 2.7)
Replaces: libdvdcss-dev (<= 0.0.3-3), libdvdcss0 (<= 1.0.0-0.0), libdvdcss2-dev
          (<= 1.2.10-0.0)
Provides: libdvdcss
Description: Simple foundation for reading DVDs - runtime libraries
 To allow applications to access some of the more advanced features of the DVD
 format.
Homepage: [http://download.videolan.org/](http://download.videolan.org/)

Make sure you have your medibuntu repository installed:

---

### Post by garvinrick4 on 2011-01-16
Running natty and just ran a DVD and no problems.
#Use maverick for medibuntu repostories.
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

---

### Post by BothEyesShut on 2011-01-16
Awesome, this worked.  Thanks for your help, Mr. Garvin.

My gf will be pleased to find her DVD player in proper working order.  Ubuntu community saves the day again!

-Both

---

### Post by garvinrick4 on 2011-01-16
No problem, my only question would be if your girl friend did not know how to run a DVD how and why is she running a version of Ubuntu that is in development and in Alpha1 stage such as Natty, you will be back here aqain shortly. Have her install 10.04 lucid or 10.10 maverick version of Ubuntu and it will run without a hitch. She is running 11.04 now with 11 the year and 4 the month it will be released.

---

