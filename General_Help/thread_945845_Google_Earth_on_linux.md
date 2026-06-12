---
title: "Google Earth on linux"
date: 2008-10-12
forum: General Help
---

### Post by Vertoxic on 2008-10-12
hey guys...
how do i install Google earth on my Ubuntu, i downloaded the file but it wont open or do anything?

---

### Post by DougieFresh4U on 2008-10-12
> **Vertoxic said:**
> hey guys...
how do i install Google earth on my Ubuntu, i downloaded the file but it wont open or do anything?

I you have Medibuntu , it will download and install it for you
You can find Medibuntu through search here at the forum.  I shall try to find it

---

### Post by Sam on 2008-10-12
[uhelp]community/Medibuntu[/uhelp]

---

### Post by howefield on 2008-10-12
To et the Medibuntu repositor...

Press "System" -> "Administration" -> "Software Sources".  Under Third Party Software, press Add.

Enter the following and press "Add Source":  
```
deb http://packages.medibuntu.org/ hardy free non-free
```

Type into a terminal.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Vertoxic on 2008-10-12
> **howefield said:**
> To et the Medibuntu repositor...

Press "System" -> "Administration" -> "Software Sources".  Under Third Party Software, press Add.

Enter the following and press "Add Source":  
```
deb http://packages.medibuntu.org/ hardy free non-free
```

Type into a terminal.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
thank you, i did that it all went tru but were is the file/icon

---

### Post by howefield on 2008-10-12
All you have done so far is add the Medibuntu repository to your system, you now need to search synaptic for googleearth and install.

---

### Post by earthpigg on 2008-10-12
and keep in mind that if you use it with compiz turned on, it **will** crash from time to time :)

---

### Post by Vertoxic on 2008-10-12
terrible i downloaded the Ubuntu 4.3 and its all blinking all over the place... do they just don't have the right fix for linux or what?

---

### Post by earthpigg on 2008-10-12
> **Vertoxic said:**
> terrible i downloaded the Ubuntu 4.3 and its all blinking all over the place... do they just don't have the right fix for linux or what?

your 3d card enabled and working properly? if you can do the desktop cube stuff, then that would be a yes...

---

### Post by Sam on 2008-10-12
Try the 4.2.

---

### Post by howefield on 2008-10-12
I don't use it, but might be worth removing and trying 4.2 ?

---

### Post by DougieFresh4U on 2008-10-12
> **Sam said:**
> [uhelp]community/Medibuntu[/uhelp]

Beat me to it

---

### Post by Vertoxic on 2008-10-12
> **earthpigg said:**
> your 3d card enabled and working properly? if you can do the desktop cube stuff, then that would be a yes...
yes i can do the cube just fine i have my ati drivers working allright.

---

### Post by Vertoxic on 2008-10-12
i just tried 4.2 and its even worse...

---

