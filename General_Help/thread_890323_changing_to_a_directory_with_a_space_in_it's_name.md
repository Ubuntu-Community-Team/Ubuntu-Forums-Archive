---
title: "changing to a directory with a space in it's name"
date: 2008-08-14
forum: General Help
---

### Post by groovomata on 2008-08-14
Hello All,
I want to use the terminal to change to directory:
> /home/erik/.wine/drive_c/Program Files/Common Files/Games/cod
The problem is that the terminal stumbles on the space in the 'Program Files' directory and doesn't know how to get past that point. Does anyone know how to change directories using the terminal that have spaces in the directory's name?

Thanks for your help,
Erik.

---

### Post by iaculallad on 2008-08-14
> **groovomata said:**
> Hello All,
I want to use the terminal to change to directory:

The problem is that the terminal stumbles on the space in the 'Program Files' directory and doesn't know how to get past that point. Does anyone know how to change directories using the terminal that have spaces in the directory's name?

Thanks for your help,
Erik.

Place a backslash character (\):

```
cd /home/erik/.wine/drive_c/Program\ Files/Common\ Files/Games/cod
```

---

### Post by contactmayankjain on 2008-08-14
its easy man use backslash then space .. like cd books\ and\ study\ material/

---

### Post by groovomata on 2008-08-14
Thanks so much! That's exactly what I needed to know.:guitar:

---

### Post by trash on 2008-08-14
you could also use quote's

```
cd "/home/erik/.wine/drive_c/Program Files/Common Files/Games/cod"
```

---

### Post by 7raTEYdCql on 2008-08-14
NOt ues the 'Tab' to complete the keyword when it is to be typed. Very useful option in terminal.

Thought this would help.

---

