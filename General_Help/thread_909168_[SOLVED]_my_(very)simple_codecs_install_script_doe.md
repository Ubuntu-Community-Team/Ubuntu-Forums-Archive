---
title: "[SOLVED] my (very)simple codecs install script doers not work"
date: 2008-09-03
forum: General Help
---

### Post by cmay on 2008-09-03
hi . can anyone help me whit this little script to install the things i need to have my dvd working under ubuntu on a amd64 machine. i followed some instructions from somewhere but i cant find again. its a simple script but it should work.
[PHP]
#!/bin/bash
# should install all the codecs stuff but ?
sudo apt-get update &&
sudo apt-get install medibuntu-keyring &&
sudo apt-get update &&
sudo apt-get install w64codecs libdvdcss2 
sudo apt-get upgrade[/PHP]

anyone knows what to do so it works. ? 
thanks for the time.

---

### Post by justleen on 2008-09-03
```

#!/bin/bash
# should install all the codecs stuff but ?
sudo apt-get update 
sudo apt-get install medibuntu-keyring w64codecs libdvdcss2 
sudo apt-get upgrade  

```

no need to update in between, or use the && (bash already executes the following line..)

---

### Post by cmay on 2008-09-03
hi . thanks for the reply.
i copied a script from somewhere. i found it via these forums. i dont know bash but when i find out how to make it work i will try create a perl script that installs all the codecs in a easy way. of course this very simple bash script should at least work before i try whit perl.
i will try to rewrite this one then. i never had any trouble whit installing codecs on my i368 ubuntu versions. i dont use this medibuntu-keyring in these scripts i already made for that . 
i will mark my tread as solved when i get this working.
thanks for the time.

---

### Post by cmay on 2008-09-03
[PHP]#!/bin/bash
# should install all the codecs stuff but ?
sudo apt-get upgrade
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update 
sudo apt-get install medibuntu-keyring 
sudo apt-get update 
sudo apt-get install w64codecs libdvdcss2 
sudo apt-get upgrade[/PHP]
this worked :)

---

