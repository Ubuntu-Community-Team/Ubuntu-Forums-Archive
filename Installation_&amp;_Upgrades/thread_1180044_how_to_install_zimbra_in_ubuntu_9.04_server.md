---
title: "how to install zimbra in ubuntu 9.04 server?"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by AlexenderReez on 2009-06-06
i know...it is risky..but i hope i don't need to spend time to format and downgrade my server to 8.04 LTS...because the only version available is that version...so here is goes> root@ubuntu:/home/radzi/zcs-6.0.0_BETA1_1397.UBUNTU8.20090415162243# ./install.sh
WARNING: ZCS is currently only supported on Ubuntu Server 6.06 and 8.04 LTS.
You are attempting to install on Ubuntu 9.04 which may not work.
Support will not be provided if you choose to continue.


Do you wish to continue? [N] y

Operations logged to /tmp/install.log.23759
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-cluster...NOT FOUND
    zimbra-core...NOT FOUND


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
  [http://www.zimbra.com/license/zimbra_public_eula_2.1.html](http://www.zimbra.com/license/zimbra_public_eula_2.1.html)


Press Return to continue

Checking for prerequisites...
     FOUND: NPTL
     FOUND: sudo-1.6.9p17-1ubuntu3
     FOUND: libidn11-1.10-3
     MISSING: libgmp3
     FOUND: libstdc++6-4.3.3-5ubuntu4
Checking for suggested prerequisites...

###ERROR###

One or more prerequisite packages are missing.
Please install them before running this installer.

Installation cancelled.

[email]root@ubuntu:/home/radzi/zcs-6.0.0_BETA1_1397.UBUNTU[/email]8.20090415162243# ./install.sh
WARNING: ZCS is currently only supported on Ubuntu Server 6.06 and 8.04 LTS.
You are attempting to install on Ubuntu 9.04 which may not work.
Support will not be provided if you choose to continue.


Do you wish to continue? [N] y

Operations logged to /tmp/install.log.24252
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-memcached...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-cluster...NOT FOUND
    zimbra-core...NOT FOUND


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
  [http://www.zimbra.com/license/zimbra_public_eula_2.1.html](http://www.zimbra.com/license/zimbra_public_eula_2.1.html)


Press Return to continue

Checking for prerequisites...
     FOUND: NPTL
     FOUND: sudo-1.6.9p17-1ubuntu3
     FOUND: libidn11-1.10-3
     MISSING: libgmp3
     FOUND: libstdc++6-4.3.3-5ubuntu4
Checking for suggested prerequisites...

###ERROR###

One or more prerequisite packages are missing.
Please install them before running this installer.

Installation cancelled.

[email]root@ubuntu:/home/radzi/zcs-6.0.0_BETA1_1397.UBUNTU[/email]8.20090415162243# apt-get libgmp 
E: Invalid operation libgmp
[email]root@ubuntu:/home/radzi/zcs-6.0.0_BETA1_1397.UBUNTU[/email]8.20090415162243# apt-get install libgmp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgmp


any help please...atlease how to make install succeed ...  T_T

---

### Post by alsrmurad on 2009-06-08
i am also facing the same problem.still i did not get any help or solution on this matter

---

### Post by Pioden on 2009-06-08
>> MISSING: libgmp3

Try installing this library and try again.

---

### Post by Blinkiz on 2009-06-25
libgmp3 does not exist under 9.04, but libgmp3cs2 exist.
You need to edit util/utilfunc.sh
```
nano +1868 util/utilfunc.sh
```and change that one into
```
PREREQ_PACKAGES="sudo libidn11 fetchmail libgmp3c2 libxml2 libstdc++6 openssl libltdl7"
```You still have errors after this do..

---

### Post by SylentBobNJ on 2009-07-15
> **Blinkiz said:**
> libgmp3 does not exist under 9.04, but libgmp3cs2 exist.
You need to edit util/utilfunc.sh
```
nano +1868 util/utilfunc.sh
```and change that one into
```
PREREQ_PACKAGES="sudo libidn11 fetchmail libgmp3c2 libxml2 libstdc++6 openssl libltdl7"
```You still have errors after this do..

Can anyone verify this works?  I need to install on 9.04 server as well.

Thanks!

---

### Post by Blinkiz on 2009-07-15
> **SylentBobNJ said:**
> Can anyone verify this works?  I need to install on 9.04 server as well.
Thanks!
The fix works. But you will have new problems after you solved this one.
If you gonna use Zimbra, use the recommended 8.04 LTS version instead.

---

### Post by pmla on 2009-07-15
yap perl problems I think

---

### Post by redchuck on 2009-07-27
I made it up to:

```
Press Return to continue

Checking for prerequisites...
     FOUND: NPTL
     FOUND: sudo-1.6.9p17-1ubuntu3
     FOUND: libidn11-1.10-3
     FOUND: fetchmail-6.3.9~rc2-4ubuntu1
     FOUND: libgmp3c2-2:4.2.4+dfsg-2ubuntu1
     FOUND: libxml2-2.6.32.dfsg-5ubuntu4
     FOUND: libstdc++6-4.3.3-5ubuntu4
     FOUND: openssl-0.9.8g-15ubuntu3.2
     FOUND: libltdl3-1.5.26-1ubuntu1
Checking for suggested prerequisites...
Prerequisite check complete.

Checking for installable packages

Found zimbra-core
Error: attempting to install i386 packages on a unknown OS.
Exiting...

```

But I'm not sure how to continue from here.  I'd really like to try Zimbra on 9.04 because my users are deeply unhappy with how bad Exchange support is on Evolution.  Does anyone have this working?

---

### Post by Blinkiz on 2009-07-28
> **redchuck said:**
> I'd really like to try Zimbra on 9.04 because my users are deeply unhappy with how bad Exchange support is on Evolution.  Does anyone have this working?
You really should be using 8.04 LTS. When you encounter errors, no one are gonna help you if ubuntu 9.04 is the installation base.

---

### Post by Eil on 2009-07-31
Someone made a Jaunty package for the 6.0 RC1 release, you could try that: [http://www.zimbra.com/forums/developers/30621-zcs-6-rc1-ubuntu-server-9-04-a.html](http://www.zimbra.com/forums/developers/30621-zcs-6-rc1-ubuntu-server-9-04-a.html)

---

### Post by pmla on 2009-07-31
It's a french original and no english is to be found in the original website.

I have done the english translation that refers to the author, link to original webpage and link to original downloads.

[TRANSLATION]("http://www.pmabox.com/index.php?option=com_content&view=article&id=22:how-to-install-zimbra-in-ubuntu-server-904-jaunty&catid=10:iceland-blog&Itemid=16")

Have FUN

---

### Post by piju on 2009-08-09
maybe this can help

[http://blog.celogeek.fr/linux/linux-tutoriels/comment-installer-zimbra-server-6-sur-ubuntu-server-9-04-jaunty/](http://blog.celogeek.fr/linux/linux-tutoriels/comment-installer-zimbra-server-6-sur-ubuntu-server-9-04-jaunty/)

---

