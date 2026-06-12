---
title: "Driver for Intellimouse Explorer 3 to activate MOUSE4 and MOUSE5"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by MurnShaw on 2007-03-17
Like the title says, does anyone know how I could get my two extra buttons working? I have cake and punch for all helpers available.

Thanks in advance!

;-D

---

### Post by octoberdan on 2007-03-25
Edgy Eft: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Mice](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Mice)
Dapper: [http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)

Hope they help you as much as they helped me.

---

### Post by octoberdan on 2007-04-06
> **octoberdan said:**
> Edgy Eft: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Mice](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Mice)
Dapper: [http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)

Hope they help you as much as they helped me.

Oh! I should have added, when I followed those tutorials my side buttons were swapped with my scroll wheel so I changed:

```

Identifier     "Configured Mouse"
...
    Option         "ZAxisMapping" "4 5"
...
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

to

```

Section "InputDevice"
...
        Option      "ZAxisMapping" "6 7"
...
        Option      "ButtonMapping" "1 2 3 4 5"
EndSection

```

---

