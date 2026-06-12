---
title: "Does anyone knows how to install this .sh file?!?!"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by discipulo44 on 2009-05-10
[SIZE=4]](*,)Can please someone tell me how can I install this file [SIZE=5]install-crossover-pro-7.1.0.sh[/SIZE] ? Because I really dont now how to install a .sh file in ubuntu... All your help is going to be very appreciated...   THANKS \\:D/
[/SIZE]

---

### Post by benj1 on 2009-05-10
just open up a terminal
cd to the directory the file is in and then type
```

./install-crossover-pro-7.1.0.sh
```

that should start the installer

---

### Post by discipulo44 on 2009-05-10
[SIZE=3]I open a Terminal and cd to directory that is the desktop and when I put this code 
[/SIZE][SIZE=3]./install-crossover-pro-7.1.0.sh[/SIZE] [SIZE=3]
it gave me this in the terminal:

bash: ./install-crossover-pro-7.1.0.sh: Permission denied


What can I do to have the permission to install it?

THANKS... \\:D/
[/SIZE]

---

### Post by SuperSonic4 on 2009-05-10
Try ```
chmod +x install-crossover-pro-7.1.0.sh
``` which will make it executable (idk if it's already executable)

If that doesn't work you may need to be root by doing ```
sudo sh install-crossover-pro-7.1.0.sh
```

---

### Post by benj1 on 2009-05-10
sudo ./install-crossover-pro-7.1.0.sh

then enter your password when prompted.

---

