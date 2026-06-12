---
title: "help with &quot;dpkg&quot; interruption during updgrade"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by SabbyH on 2009-10-21
HELP! went to do first update manger for my system and it gave me a message that says 

E: dpkg was interrupted. you must manually run "dpkg -- configure-a" to correct the problem. 

E:_Cache-> open() failed, please report. 

Can someone tell me what's wrong and what I should do?

---

### Post by disophisis on 2009-10-21
Have you tried running the command it specifies in a terminal?

---

### Post by SabbyH on 2009-10-21
LOL - since I don't even know what a terminal really refers to, then no. No idea how to do that. Might not have been the best idea to get ubuntu since I don't know any computer stuff, but I've loved how it ran until now.

---

### Post by disophisis on 2009-10-21
Try going to Applications, then Accessories, then select Terminal.  In the terminal, type:

sudo dpkg --configure -a

hit enter, and see if that clears it up.

---

### Post by SabbyH on 2009-10-21
thank you - I'll try that.

---

### Post by disophisis on 2009-10-21
saweet, and let us know if it works of course.

---

### Post by johninsf on 2009-10-28
Please help! I was upgrading to Kubuntu 9.10 tonight and got this this error after the install froze at ~90%. I tried running the sudo command mentioned in the terminal. 

It does not work and I get the following error:

"unable to accessdpkg status area: Read-only file system."

What can I do to make my file system readable again? Is it a running process that is locking me out? Any direction would be appreciated.

Thanks.

John

> **SabbyH said:**
> HELP! went to do first update manger for my system and it gave me a message that says 

E: dpkg was interrupted. you must manually run "dpkg -- configure-a" to correct the problem. 

E:_Cache-> open() failed, please report. 

Can someone tell me what's wrong and what I should do?

---

### Post by SabbyH on 2009-11-03
I did the instructions in a terminal and it seemed that everything worked. It seemed it was runnign the updates. When it was done though, the error message I got is below and now my netbook won't even recognize wifi. So I have no way to download ubuntu to re-install since I have no CD drive and it won't connect to the internet! 
 
Here's the error message: 
 
 
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'[/SIZE][/FONT]

---

