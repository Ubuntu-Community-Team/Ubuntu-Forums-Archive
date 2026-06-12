---
title: "Script"
date: 2008-08-04
forum: General Help
---

### Post by njb on 2008-08-04
I have a file with extention *.sh
How can I execute this script under hardy Heron ?

:lolflag:

NjB

---

### Post by tamoneya on 2008-08-04
this is assuming it is on the desktop and is called myfile.sh.
```
cd ~/Desktop
chmod +x myfile.sh
./myfile.sh
```

If this is an installer of some type the last command may need sudo like this:```
sudo ./myfile.sh
```

---

