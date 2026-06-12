---
title: "i wanna know my integrated graphic card name"
date: 2008-10-13
forum: Hardware
---

### Post by mostafamehiri on 2008-10-13
[CENTER][SIZE=4][COLOR=RoyalBlue]**[FONT=Comic Sans MS]i need to install driver for my integrated Graphic card[/FONT]**[/COLOR][/SIZE][COLOR=RoyalBlue]
[/COLOR][SIZE=4][COLOR=RoyalBlue][B][FONT=Comic Sans MS] all i need now is to know my graphic card's name and reference

help please !!!!!!!!!!
[/FONT][/B][/COLOR][/SIZE][/CENTER]

---

### Post by howefield on 2008-10-13
type the following into a terminal

```
lshw
```

---

### Post by prshah on 2008-10-13
> **mostafamehiri said:**
> 
all i need now is to know my graphic card's name and reference


Any one of these will tell you:```

lspci | grep -i graphics
```

```

lshw -C display

``` (Ignore warning)

---

