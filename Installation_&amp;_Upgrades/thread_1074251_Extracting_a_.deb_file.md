---
title: "Extracting a .deb file"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by shmax44 on 2009-02-19
Hey all,

I've been trying to install openoffice 3.0 on Ubuntu 8.10 and having some trouble. I was following the instructions in [http://ubuntuforums.org/showthread.php?p=6639054#post6639054](http://ubuntuforums.org/showthread.php?p=6639054#post6639054) but one of the steps was: 

"extract the .deb file, OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz then you'll see a file called OOO300_m15_native_packed-1_en-US.9379"

well I have the tar.gz file saved on my desktop, but what is the command to extract it? Any help would be great or if anyone knows of an easier sure way to install it would be great. I tried a number of different methods and I removed openoffice 2.4 trying to follow another thread's instructions so now I have no openoffice functioning and still need to do some homework tonight! Please help!

---

### Post by mikewu on 2009-02-19
Open up a terminal and navigate to your Desktop

cd ~/Desktop

To extract a tarball, use the tar command
tar -xzf OOo_3.0.1_LinuxIntel_install_da_deb.tar.gz

That will uncompress the .tar.gz

You should be able to follow the guide from here.

---

### Post by konqueror7 on 2009-02-19
right click and 'Extract Here' or
```
tar -xzvf OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
```

---

### Post by shmax44 on 2009-02-19
> **konqueror7 said:**
> right click and 'Extract Here' or
```
tar -xzvf OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
```

Thanks a TON, guys. I tried both methods and neither was working on its own, but when I changed directories to the desktop, and used konquerors command in the terminal, it worked. It's installed now. I appreciate the help!

---

