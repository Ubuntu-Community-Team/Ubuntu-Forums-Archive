---
title: "How to right click folder open with terminal"
date: 2008-10-14
forum: General Help
---

### Post by Cool Surfer on 2008-10-14
Like in windows we browse to folfers and right click and theres a tweak setting which gives an option on right click - command prompt here

How do we open folder with terminal on right click ?

---

### Post by justleen on 2008-10-14
create a new script in the nautilus script dir with the following content:```
#!/bin/bash
gnome-terminal  --working-directory $1

```

make the script executable after saving..

---

### Post by bollix47 on 2008-10-14
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by Cool Surfer on 2008-10-14
Thank you.

---

