---
title: "Played with multiple monitors, after reboot system wont start up??"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by kajillin on 2007-12-13
ok so i think it is my video driver malfunctioning (well i almost know it is), 

because i can access the recovery mode just fine but whenever i need rendering done i get the good old blank screen, anyone know how i can fix this through recovery mode?

im on gutsy
ati x1600 proprietary drivers :( fglrx

Thanks,

---

### Post by kajillin on 2007-12-13
anyone have a real answer?

---

### Post by kajillin on 2007-12-13
:( needs answer LiveCD = LAME

---

### Post by kajillin on 2007-12-13
:(

---

### Post by kajillin on 2007-12-13
ok so i got my system back

did

```
startx
```

wouldnt start so the i did

```
dpkg-reconfigure xserver-xorg
```

and now its back up

Cheers,

---

### Post by dward526 on 2007-12-13
> **kajillin said:**
> ok so i got my system back

did

```
startx
```

wouldnt start so the i did

```
dpkg-reconfigure xserver-xorg
```

and now its back up

Cheers,

Just solved similar issues using 

```
dpkg-reconfigure xserver-xorg
```

I am going to start using it sooner now :)

glad to hear it is fixed

---

