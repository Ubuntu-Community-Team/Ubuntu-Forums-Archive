---
title: "[SOLVED] 3d cube"
date: 2008-07-28
forum: General Help
---

### Post by kabel_kabel on 2008-07-28
Dear all,

I'm having problems with 3d cube, i can't make it to work, i've tried several things, but without success. I have installed nvidia drivers, extra plugins, advanced desktop effects settings and the whole nine yards and still nothing. I seems like that whatever i do i cannot increase the number of virtual desktops from two to four. I've right clicked on virtual desktops --> Configure Desktops --> i've changed the number of the virtual desktops from two to four --> apply and then is going back to two no mater what i do. It pisses me off, but what i can do. So, help is needed, does somebody know how to fix this, or how i can increase the number of virtual desktop without using GUI, please help me :(!

Than you in advance!
Kabel

---

### Post by dark_harmonics on 2008-07-28
The first thing to do is to make sure that you can get compiz to load at all. 

If you launch compiz --replace from a command prompt does it work or does it crash? if it crashes what error codes?

To directly answer your question you can set that in ~/.config/compiz/compizconfig/Default.ini
Right at the top under [core] you can set s0_hsize = 4 to get for it hink.

---

### Post by kabel_kabel on 2008-07-30
I tried your suggestion your and it didn't work. What i've ended doing is reinstalling compiz and it solved the problem, but i'm not a certain if i replaced it with newer version of compiz. However, it is working now and i'm happy again.

Thank you for your response and your input.
Kabel.

P.S. I've checked ~/.config/compiz/compizconfig/Default.ini and there is nothing like "s0_hsize = 4". I can see only two virtual desktops on my taskbar and "3d cube" is working properly. Hm-m-m-m-m. Thank you again.

---

