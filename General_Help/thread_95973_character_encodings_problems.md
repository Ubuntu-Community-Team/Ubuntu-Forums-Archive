---
title: "character encodings problems"
date: 2005-11-27
forum: General Help
---

### Post by kovu-cat on 2005-11-27
hi all!

i'm from germany and i'd like to use the encoding iso-8859-15. i use ubuntu breezy badger and everywhere i told my system to use 8859-15. when i type in "locale" into the terminal, it says:

$ locale
LANG=de_DE@euro
LC_CTYPE="de_DE@euro"
LC_NUMERIC="de_DE@euro"
LC_TIME="de_DE@euro"
LC_COLLATE="de_DE@euro"
LC_MONETARY="de_DE@euro"
LC_MESSAGES="de_DE@euro"
LC_PAPER="de_DE@euro"
LC_NAME="de_DE@euro"
LC_ADDRESS="de_DE@euro"
LC_TELEPHONE="de_DE@euro"
LC_MEASUREMENT="de_DE@euro"
LC_IDENTIFICATION="de_DE@euro"
LC_ALL=de_DE@euro

(de_DE@euro is the right encoding)

but now gnome / nautilus seems to use only 8859-1, because when i type in some letters, the terminal and all other kde programms don't show the right letter. any idea how i can tell the gnome control center explicit which encoding to use?

kovu

---

### Post by Bachstelze on 2005-11-27
try running "sudo dpkg-reconfigure locales"

---

### Post by kovu-cat on 2005-11-27
it doesn't help. :(

---

### Post by [HUN]Levente on 2005-11-27
I have another locale problem. I want all locales to be en_US.UTF8, but LC_TIME should be hu_HU.UTF8. I set the locale to en_US.UTF8 with "sudo dpkg-reconfigure locales", but how can i set the LC_TIME?

---

