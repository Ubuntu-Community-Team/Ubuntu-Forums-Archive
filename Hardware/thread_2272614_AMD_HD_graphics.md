---
title: "AMD HD graphics"
date: 2015-04-08
forum: Hardware
---

### Post by Spae on 2015-04-08
I have the open source installed and it works with games to some extent but things just don't display properly and the FPS isn't the best.

I went here [http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64](http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64) to get the hopefully better driver but I don't know what to do. I downloaded all the files for ubuntu 14.04 and then I went here [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx#Install](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx#Install) but it doesn't work.
> 

[LIST=1]
[*]Launch the Terminal Application/Window and navigate to the AMD Catalyst proprietary driver download. 
[*]Enter the command              *sudo **sh ./amd-driver-installer-x86.x86_64.run* to launch the AMD Catalyst proprietary driver installer and display the AMD Catalyst proprietary driver setup dialog box. 
[/LIST]


It just returns 
> sh: 0: Can't open ./amd-driver-installer-x86.x86_64.run


Of course it shouldn't work due to this 
> **NOTE:** The document uses "**amd-driver-installer-x86.x86_64.run**" as a generic reference to the AMD install file. But I don't know where any .run files are. They only had .deb files.

It's an AMD HD7950

and double clicking the .deb files doesn't work due to dependency errors.

---

### Post by QIII on 2015-04-08
Hello!

Did you know you can install the fglrx driver (the proprietary AMD driver) from the Ubuntu repos?

But first:  Which version of Ubuntu are you using, including the point release (i.e.: 12.04.5, 14.04.2 ...)

---

### Post by mastablasta on 2015-04-08
also read this: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

it's actually easy to install drivers. 2 clicks with a mouse.

---

### Post by QIII on 2015-04-08
None of that will work with the Hardware Enablement Stack that just came out for 12.04 and 14.04, though.

---

### Post by Spae on 2015-04-08
I reinstalled Ubuntu yesterday so 14.04.

Going into the software sources and clicking the AMD driver in additional drivers does not work. It reselects the open source bubble as soon as I click apply for the proprietary driver.

> 
Did you know you can install the fglrx driver (the proprietary AMD driver) from the Ubuntu repos? How?

I can see fglrx in software centre should I do that?

Well, I tried in software centre and it didn't work.

> The following packages have unmet dependencies:

fglrx: Depends: libqtcore4 (>= 4:4.8.4) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
       Depends: xorg-video-abi-15 but it is a virtual package



---

### Post by mastablasta on 2015-04-08
post output command of ```
uname -a
```

make sure you have all necessary repositories enabled.

---

### Post by QIII on 2015-04-08
Although you did not respond to my question about the specific version of Ubuntu you are using, your last post indicates what I suspected:  you are running either 12.04.5 or 14.04.2 -- each of which uses the recent Hardware Enablement Stack.

Unfortunately, there is a bug I reported about 6 weeks ago:  the fglrx driver will not install properly with the HWE stack.

My first recommendation would be to just wait and use the open source driver for the moment.

If you absolutely must have the proprietary driver and want to stay in the LTS cycle, then back up and install either 12.04.4 or 14.04.1.

14.10 does not exhibit this bug, nor does 15.04.  The latter has not yet been released.  Using either of them takes you out of the LTS cycle, however.

Because you are affected by this bug, would you please visit the report and click "Affects me" to raise the heat index?
[https://bugs.launchpad.net/ubuntu/trusty/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/trusty/+source/fglrx-installer/+bug/1424491)

---

### Post by Spae on 2015-04-08
```
uname -a
Linux bob-System-Product-Name 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Yeah, I do have 14.04.2, I just had to search how to find that. I'll just wait it out. I've clicked it also affects me on that page.

Thanks for your help. Now I won't have to go crazy trying to do the impossible.

---

### Post by QIII on 2015-04-08
Welcome.  And thanks for turning up the heat.  This is a bit embarrassing since it happened just a few days after I blogged about how well the R9 290X works on Ubuntu after several days of testing.

Alas.

---

