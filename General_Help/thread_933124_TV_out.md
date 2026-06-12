---
title: "TV out ?"
date: 2008-09-29
forum: General Help
---

### Post by mchaley on 2008-09-29
Hello,
I'm relatively familiar with sending the desktop of a machine to a TV. I've never done it through linux though. This laptop has an RCA port so it's a straight shot to the TV. Has anyone been able to do this? If so, could you point me in the right direction?

I have an intel 82830 CGC video card

Thanks

---

### Post by jonian_g on 2008-09-29
Just connect the cable, open the terminal and type:
```
sudo displayconfig-gtk
```
And configure your second screen from there (it's a gui app).

---

