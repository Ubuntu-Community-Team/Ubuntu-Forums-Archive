---
title: "veetle? anyone?"
date: 2010-10-04
forum: Hardware
---

### Post by clipt on 2010-10-04
hey peeps. looking to see if anyone in the ubuntu world has gotten veetle to work and what the did to make it work. i tried what i knew and... negatory on working. 
i opened a terminal and typed   sh veetle-0.9.17-linux-install.sh


and i get       sh: Can't open veetle-0.9.17-linux-install.sh

---

### Post by nc_jed on 2010-10-04
> **clipt said:**
> hey peeps. looking to see if anyone in the ubuntu world has gotten veetle to work and what the did to make it work. i tried what i knew and... negatory on working. 
i opened a terminal and typed   sh veetle-0.9.17-linux-install.sh


and i get       sh: Can't open veetle-0.9.17-linux-install.sh

$ chmod 777 veetle-0.9.17-linux-install.sh
$ sh veetle-0.9.17-linux-install.sh

??

---

### Post by clipt on 2010-10-04
cannot access 'veetle-0.9.17-linux-install.sh' no such file or directory

---

### Post by nc_jed on 2010-10-05
> **clipt said:**
> cannot access 'veetle-0.9.17-linux-install.sh' no such file or directory

Appears the file isn't there?  are you in the directory you downloaded it to when you execute the commands from the terminal?  Alternately, you can find the file in the graphical File Manager (nautilus).  Right-click, choose 'Properties', 'Permissions' tab.  Check the 'Allow Executing file as program' box.  Then go back to the terminal, use 'cd' to get to the directory the file is located in and execute the sh veetle*.sh command again.

- Jed

---

### Post by clipt on 2010-10-06
i actually got it, i youtubed it and found how to install it. thanks for the help though.

---

