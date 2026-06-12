---
title: "cambiar resolucion"
date: 2008-10-24
forum: Hardware
---

### Post by tsueseres on 2008-10-24
hay alguna forma de cambiar la resolucion a mas de 1024 780  como a 1280 x 800

---

### Post by Aspergillus on 2008-10-24
abris una terminal

sudo gedit /etc/X11/xorg.conf

ahi buscas "Section "Screen""

y en Option donde te pone las resoluciones lo maximo que te tiene que mostrar ahi es la de 1024, agregas la que vos queres por ej yo lo tengo asi

Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"

una vez que agregas las resoluciones que queres cerras y guardas los cambios y reinicias X

yo cuando tuve ese problema lo arregle asi, espero que te sirva

---

### Post by tsueseres on 2008-10-24
> **Aspergillus said:**
> abris una terminal

sudo gedit /etc/X11/xorg.conf

ahi buscas "Section "Screen""

y en Option donde te pone las resoluciones lo maximo que te tiene que mostrar ahi es la de 1024, agregas la que vos queres por ej yo lo tengo asi

Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"

una vez que agregas las resoluciones que queres cerras y guardas los cambios y reinicias X

yo cuando tuve ese problema lo arregle asi, espero que te sirva

si, gracias

---

### Post by hictio on 2008-10-24
> 
 ```

  sudo gedit /etc/X11/xorg.conf
 
```


Yo te recomendaria, solo por si las moscas, que antes de editarlo, le hagas un backup:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Asi si pasa algo infortunado, tenes una copia que funciona (aunque con una resolucion a aumentar)

---

### Post by faktorqm on 2008-10-25
apreta ALT + F2 y escribi
```
gksudo displayconfig-gtk
```
de ahi se cambia. salu2!

---

