---
title: "res wont change!"
date: 2005-11-15
forum: General Help
---

### Post by sunrex on 2005-11-15
no matter what i do, serverx, xorg, whatever, reinstall, the res WILL NOT change, and i know it can go ALOT higher then this since it was alot higher on my other computer, im currently on a amd64, but anyway, i moved the 3d card to this computer (ati) and am using the same moniter, so what gives? any ideas...

---

### Post by teaker1s on 2005-11-15
there are ati patches I beleive that people have mentioned on these forums and I think they are direct from ati for affected products and you can
sudo dpkg-reconfigure xserver-xorg
to reconfigure and change resolution

---

### Post by sunrex on 2005-11-15
i did that alredy. NOTHING HAPPENED i said that above....

---

### Post by teaker1s on 2005-11-15
looks like your be looking for a patch and some manners to go with it.
you can edit xorg either by gediting the txt file or the setup wizard

try searching ati on forums

---

### Post by sunrex on 2005-11-15
sorry about the yelling, so is this just amd thats the problem, couse on intel and with the same 3d card, it was working fine.

---

### Post by sunrex on 2005-11-15
wait..how do i remove some res from the list?

---

### Post by [2]BoxingFiend on 2005-11-16
edit your /etc/X11/xorg.conf

under the Section "Screen"

Most likely you are running Dept 24 mode. so sroll down about half a page.

you should see something like 

Subsection "Display"
  Dept 24
  Modes "1600x1200" "1280x1024" "1024x768" ... 
EndSubSection

delete the one you don't want and restart X

---

