---
title: "Ubuntu equiv to bat"
date: 2008-08-14
forum: General Help
---

### Post by timboellis on 2008-08-14
What is the equiveland to a Bat file in Ubuntu.

Say I wished to start firefox in windows I would create a text file with firefox and save as a bat how can i do this in Ubuntu

---

### Post by Mgiacchetti on 2008-08-14
create a file, enter the commands you wish, save the file wherever you wish,

after saving and closing, navigate to that directory right click properties.
go to permissions, and check the executable option.

---

### Post by sayakb on 2008-08-14
Create a script. A sample script (open **gedit filename** from a terminal):
```

#!/bin/bash
ls
echo OK

```
Save it and type:
```
chmod +x filename
```
And execute it by typing:
```
./filename
```

---

