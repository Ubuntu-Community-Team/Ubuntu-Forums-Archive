---
title: "[SOLVED] Problem with Startup Manager"
date: 2008-09-26
forum: General Help
---

### Post by Aero-Z on 2008-09-26
Hi,

I wanted to change the usplash boot loader. I downloaded few from gnome-look.org. The problem is that after selecting the desired theme in startup manager then after closing the program the changes are gone. Next time I start startup manager then the default ubuntu theme is back there. I managed to get one theme out of 10 to work. Am I doing something wrong or are the configurations of those themes messed up or..?

---

### Post by Sycron on 2008-09-26
How are you choosing a new theme ? From Login Window ?

---

### Post by Aero-Z on 2008-09-26
> **Sycron said:**
> How are you choosing a new theme ? From Login Window ?
I open up Startup Manager->Appearance->Usplash themes and from the drop down menu.

---

### Post by Sycron on 2008-09-26
Change the usplash and restart computer. After that tell me if works.

---

### Post by Aero-Z on 2008-09-26
> **Sycron said:**
> Change the usplash and restart computer. After that tell me if works.
I worked with only one theme. Choosing any other theme didn't make any effect - after restarting startup manager the theme was changed back to ubuntu's default usplash theme.

---

### Post by Sycron on 2008-09-26
Are you sure that the usplash is compatible with your version of ubuntu,kernel ?

---

### Post by Aero-Z on 2008-09-26
> **Sycron said:**
> Are you sure that the usplash is compatible with your version of ubuntu,kernel ?
usplash itself is working because ubuntu's default boot splash is working. It's either the program's fault or there's something wrong with the themes. The themes are *.so files.

---

### Post by Aero-Z on 2008-09-28
Bump.

I'd like to get this theme to work. [http://gnome-look.org/content/show.php/Ubuntu+Wheel+Usplash+(also+widescreen)?content=84841](http://gnome-look.org/content/show.php/Ubuntu+Wheel+Usplash+(also+widescreen)?content=84841)
There's source only. Could anybody tell me what commands to run to get a theme file from it?
I've googled a bit but it's a bit over my head.

Thanks

---

### Post by Aero-Z on 2008-09-28
Bump

---

### Post by Aero-Z on 2008-09-29
Got it to work. Had to manually install alternatives:
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/ubuntu-wheel.so 10
```

---

### Post by Sycron on 2008-09-29
Well, you made it. Good job.

---

