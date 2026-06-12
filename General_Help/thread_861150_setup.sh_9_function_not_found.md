---
title: "setup.sh: 9: function: not found"
date: 2008-07-16
forum: General Help
---

### Post by xaocan on 2008-07-16
I tried to install something, it's and .iso file so I've mounted it, browsed the directory and did "sh setup.sh". And that's what I've got:

> xxx@xxx-desktop:/media/cdrom0$ sh setup.sh
setup.sh: 9: function: not found
x86


What does that mean and what should I do to fix it?

---

### Post by prshah on 2008-07-16
> **xaocan said:**
> 
What does that mean and what should I do to fix it?

probably a syntax error in the script. Can you post the script here or is it something ultra secret?

---

### Post by dracayr on 2008-07-16
try bash instead of sh (simply replace sh with bash in your command)

dracayr

---

### Post by xaocan on 2008-07-16
thx alot - the bash thing helped ;P

---

### Post by thatsmyboy on 2009-09-18
I guess ```
sh
``` is just the installed shell but if it's not installed (default in ubuntu) then you have to use ```
bash
``` ??

---

### Post by stderr on 2009-09-18
This is a rather old thread thatsmyboy :)

sh and bash are different shells: bash is newer nad has lots more features and syntax. In this case, the more basic sh was missing an inbuilt function that bash has.

Both sh and bash are installed by default in ubuntu. There are many other shells too, such as csh and zsh. You can write a simple shell script by putting the shell you want to use on the first line. Both these will work, although they're using sh and bash respectively:

```

#!/bin/sh
echo "Hello World"

```
```

#!/bin/bash
echo "Hello World"

```

---

### Post by killernat on 2009-11-05
thanks why wasnt ```
sh
``` included in ubuntu 9 couldnt it just be used as a pointer for bash so people dont have this problome

---

