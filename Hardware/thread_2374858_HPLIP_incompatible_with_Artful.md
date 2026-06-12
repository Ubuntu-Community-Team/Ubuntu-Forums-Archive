---
title: "HPLIP incompatible with Artful"
date: 2017-10-19
forum: Hardware
---

### Post by drfox on 2017-10-19
I have an HP OfficePro All in One printer. The print function works fine, but I cannot get SANE to recognize the scanner. I had previously used hplip to install the scanner in 17.04, but the hplip.run install utility reports that a dependency, libcrypto, is missing. I have installed libcrypto++6, but that doesn't solve the dependency issue. I am using hplip 3.17.10.
Can anyone suggest a workaround?

---

### Post by dino99 on 2017-10-20
3.17.7 works fine (default Artful)

---

### Post by jib2-form on 2017-10-20
How would you use v. 3.17.10 siince Artful is shipped with 3.17.7 ?  
Maybe there's a mismatch between hplip version and the plugin version?

---

### Post by cariboo on 2017-10-20
Moved as Artful has now been released.

---

### Post by drfox on 2017-10-20
> **cariboo said:**
> Moved as Artful has now been released.

I have been downloading the latest hplip(s) because since early beta, I have not been able to use my scanner. This is the output I get when I try to use the default Artful installed hp-setup

drfox@bigdog:~$ hp-setup
The program 'hp-setup' is currently not installed. You can install it by typing:
sudo apt install hplip
drfox@bigdog:~$ sudo apt install hplip
[sudo] password for drfox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version (3.17.7+repack0-3).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please tell me how it works for you.

---

### Post by pdc on 2017-10-20
> I have an HP OfficePro All in One printer. would you be willing to tell us which one you have please?

---

### Post by jib2-form on 2017-10-21
You might need the hplip plugin.
$ sudo hp-setup -i
then answer the questions and download the plugin.

---

### Post by drfox on 2017-10-21
So it seems I have a broken system. I have another laptop running Artful which has a working hplip.
On my problem machine I have tried purging hplip, rebooting and reinstalling hplip from the repos, but still get the error "The program 'hp-setup' is currently not installed. You can install it by typing:
sudo apt install hplip"
The model number is not relevant, but it's an OJP 8725
Any suggestions?

---

