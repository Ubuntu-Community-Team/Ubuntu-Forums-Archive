---
title: "root nautilus launcher without terminal"
date: 2008-08-17
forum: General Help
---

### Post by zorkerz on 2008-08-17
I have created a launcher that runs the command 'gksudo nautilus'. This is great because it asks for my password and then opens a nautilus window in root. However it also opens up a terminal.

Is there a way to create a launcher that opens nautilus in root without a terminal window?

---

### Post by zorkerz on 2008-08-17
Scratch that. In the launcher properties under **type** I selected application instead of application in terminal. Don't know how I missed this before. Sorry for the needless thread.

---

### Post by tekno62 on 2008-08-18
how would you do this?

---

### Post by Oldsoldier2003 on 2008-08-18
> **tekno62 said:**
> how would you do this?

right click the desktop, select create launcher. The type is "application",for the command put in ```
gksu nautilus
```.

---

### Post by LinLux451 on 2010-01-25
Any idea how to do this with a jar file? I'm a real fan of Angry IP Scanner > Zenmap, so and my current launch command is
```
java -jar /home/tom/.ipscan-linux64-3.0-beta4.jar
```

adding gksu to the beginning doesn't work. Any ideas?

---

### Post by sisco311 on 2010-01-25
> **LinLux451 said:**
> Any idea how to do this with a jar file? I'm a real fan of Angry IP Scanner > Zenmap, so and my current launch command is
```
java -jar /home/tom/.ipscan-linux64-3.0-beta4.jar
```

adding gksu to the beginning doesn't work. Any ideas?

```
sh -c "java -jar /home/tom/.ipscan-linux64-3.0-beta4.jar"
```

---

