---
title: "aMsn"
date: 2008-08-06
forum: General Help
---

### Post by sdalgl72 on 2008-08-06
Hey

I am new to all this so sorry if this is posted in the wrong place but AMSN is not connecting and I have just clicked check for new version and there is.  I originally installed it through add and remove and was wondering how I install the update.

Thank you an advance for your help.

---

### Post by Ryadt on 2008-08-06
You will have to download it from their website.
[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)
Download the Tcl/tk 8.4 and follow the simple instruction.

---

### Post by sdalgl72 on 2008-08-06
> **Ryadt said:**
> You will have to download it from their website.
[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)
Download the Tcl/tk 8.4 and follow the simple instruction.


Thanks for your help I tried following instructions and still get this.  Could you give idiot proof instructions please :D I am really sorry.

---

### Post by danuk88 on 2008-08-06
download it from hear,

[http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb](http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb)

Then just click it to install (remove the old one first)

---

### Post by y-lee on 2008-08-06
If you installed aMSN thru add and remove and then did not uninstall it but downloaded the current version of aMSN from the link above and installed that you most likely now have 2 aMSN installed. If so the menu item or launcher you are clicking starts the old version not the new.

My advice would be to try to find the new version on your computer and change menu items and launchers to reflect the new location. I am not sure if it would be safe to uninstall the old version, I probably would try it. But it might and probably would mess up a few things like the menu item for aMSN might get removed.

The command **whereis amsn** might find both the old and the new version of the program.

BTW you said you installed the new version did you use the "generic installers" or did you compile from source code.

---

### Post by sdalgl72 on 2008-08-06
> **y-lee said:**
> If you installed aMSN thru add and remove and then did not uninstall it but downloaded the current version of aMSN from the link above and installed that you most likely now have 2 aMSN installed. If so the menu item or launcher you are clicking starts the old version not the new.

My advice would be to try to find the new version on your computer and change menu items and launchers to reflect the new location. I am not sure if it would be safe to uninstall the old version, I probably would try it. But it might and probably would mess up a few things like the menu item for aMSN might get removed.

The command **whereis amsn** might find both the old and the new version of the program.

BTW you said you installed the new version did you use the "generic installers" or did you compile from source code.

This is the results of what I got when putting that code in can you instruct me further it really does have to be a dummies guide.

---

### Post by y-lee on 2008-08-06
Judging from that you probably only have 1 aMSN. You can check it out by opening nautilus (the file manager) and navigating to /usr/share/amsn and then clicking the amsn file in that folder. When msn starts go to help about and see what version it is.

The file /usr/bin/amsn should be a link to the amsn above but if you wish to be sure navigate to /usr/bin/ in nautilus  and start msn there by clicking the amsn file found there, now check the version number. If both are the old version go ahead and remove amsn using add and remove programs or synaptic. 

You might wish to install amsn from the deb above after removing the old version, if you trust danuk88 that is. I am not sure who made that deb but I would hope it is legit. If you have doubts install from amsns web site.

---

### Post by sdalgl72 on 2008-08-06
> **y-lee said:**
> Judging from that you probably only have 1 aMSN. You can check it out by opening nautilus (the file manager) and navigating to /usr/share/amsn and then clicking the amsn file in that folder. When msn starts go to help about and see what version it is.

The file /usr/bin/amsn should be a link to the amsn above but if you wish to be sure navigate to /usr/bin/ in nautilus  and start msn there by clicking the amsn file found there, now check the version number. If both are the old version go ahead and remove amsn using add and remove programs or synaptic. 

You might wish to install amsn from the deb above after removing the old version, if you trust danuk88 that is. I am not sure who made that deb but I would hope it is legit. If you have doubts install from amsns web site.

Hey uninstalled amsn and run the process to install from amsn website.

got this error

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Package 'TCL Scripting Language' was found but was of the wrong version and the correct version could not be located.

[IV 8.4 for @tcl.sourceforge.net/tcl]

Error: Unable to prepare package AMSN MSN client.

---

### Post by davidw89 on 2008-08-06
Why don't you try Emesene?

---

### Post by y-lee on 2008-08-06
> Hey uninstalled amsn and run the process to install from amsn website.

got this error

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed

How did you try to install it? If using the Generic Installers they have two versions one for Tcl/Tk 8.4 and one for Tcl/Tk 8.5.

```
echo "puts [set ::tcl_patchLevel]; exit" | wish
```

Will tell you which version of Tcl you have if version 8.4 please try the Generic installer for that version. If you have no version of tcl post back, or try to install it.

```
sudo apt-get install tcl tk tcl-dev tk-dev
```

davidw89, I am assuming the OP wants aMsn there are several Im programs that can connect to MSN but I for example like and use aMSN.

---

### Post by davidw89 on 2008-08-06
You could try both...as for me aMSN doesn't even log on for me..just says "connecting" forever

---

### Post by sdalgl72 on 2008-08-06
> **y-lee said:**
> How did you try to install it? If using the Generic Installers they have two versions one for Tcl/Tk 8.4 and one for Tcl/Tk 8.5.

```
echo "puts [set ::tcl_patchLevel]; exit" | wish
```

Will tell you which version of Tcl you have if version 8.4 please try the Generic installer for that version. If you have no version of tcl post back, or try to install it.

```
sudo apt-get install tcl tk tcl-dev tk-dev
```

davidw89, I am assuming the OP wants aMsn there are several Im programs that can connect to MSN but I for example like and use aMSN.

stuart@stuart-laptop:~$ echo "puts [set ::tcl_patchLevel]; exit" | wish
The program 'wish' can be found in the following packages:
 * tk8.3
 * tk8.5
 * tk8.4
 * tk
Try: sudo apt-get install <selected package>
bash: wish: command not found

I tried it with both but both came up with the same thing.

---

### Post by sdalgl72 on 2008-08-06
> **davidw89 said:**
> Why don't you try Emesene?

I will have a look at it.

Does it support webcams?

---

### Post by y-lee on 2008-08-06
> **sdalgl72 said:**
> stuart@stuart-laptop:~$ echo "puts [set ::tcl_patchLevel]; exit" | wish
The program 'wish' can be found in the following packages:
 * tk8.3
 * tk8.5
 * tk8.4
 * tk
Try: sudo apt-get install <selected package>
bash: wish: command not found

I tried it with both but both came up with the same thing.

You need the tk package, try

```
sudo apt-get install tcl tk tcl-dev tk-dev
```

---

### Post by Adri2000 on 2008-08-06
There is a fixed package available in hardy-proposed and (very soon) gutsy-proposed. See [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

---

### Post by rfdeshon on 2008-08-06
Hey all, I posted this in another amsn thread yesterday (search the forums people, this question has already been answered).

1) Remove old amsn
```

sudo aptitude purge amsn

```
2) Install TCL/TK 8.5 and TLS

```

sudo aptitude install tcl8.5 tk8.5 tcltls

```
tcl-dev and tk-dev are NOT NEEDED.
3) Download the TCL/TK 8.5 package from the amsn website
4) Install amsn
```

cd /path/to/download
chmod +x amsn-0.97.2-1.tcl85.x86.package
sudo bash amsn-0.97.2-1.tcl85.x86.package

```
Note: if you already tried to install the package at some point, it will tell you to run package install. Just replace bash in the above command with package install.
5) Launch amsn, it will have to do some more configuration at this point, answer it's questions and be patient.

---

### Post by sdalgl72 on 2008-08-06
Hey guys thanks for all your help Adri2000 fixed the problem ok not the latest version but it fixed the not being able to log on problem :D

Thanks for all your help can't thank you enough.

---

### Post by badgaz1 on 2008-08-06
Where can I find the new version that will work with x64?

---

### Post by tuxxy on 2008-08-06
You dont  need to install from source, you should however all be using the supported package of the new aMSN version 0.97.2 which is available for 32/64bit download here [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)  

Once you downloaded to desktop right click on the file and select install.

---

### Post by Adri2000 on 2008-08-07
> **badgaz1 said:**
> Where can I find the new version that will work with x64?

See my post above.

> **tuxxy said:**
> You dont  need to install from source, you should however all be using the supported package of the new aMSN version 0.97.2 which is available for 32/64bit download here [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)  

Once you downloaded to desktop right click on the file and select install.

This package is *not* supported, as it's not from the official Ubuntu repositories.

---

### Post by stanz on 2008-10-04
[quote=Adri2000;
This package is *not* supported, as it's not from the official Ubuntu repositories.[/quote]

Geezz....Cannot connect with the repo version ~ I read the protocol change post.
and.....
Cannot install from amsn site, cause the auto installer stuff can't find the right version of Tcl/Tk 8.5 - which I just got.
????

I'm ready to sh*t can this program and stick with GyachE !!!

---

### Post by tuxxy on 2008-10-04
Update to the newer version, download the deb here

[http://www.getdeb.net/release.php?id=3001](http://www.getdeb.net/release.php?id=3001)

---

### Post by stanz on 2008-10-06
> **Adri2000 said:**
> See my post above.



This package is *not* supported, as it's not from the official Ubuntu repositories.

I agree with using the repos.

---

