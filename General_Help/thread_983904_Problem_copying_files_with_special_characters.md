---
title: "Problem copying files with special characters"
date: 2008-11-16
forum: General Help
---

### Post by hjoakim on 2008-11-16
Hi

I'm trying to backup my data on ubuntu to an external HD but got write problems with special characters like Swedish and Japanese. I have to manually change the names on all files before copying them and this will take me forever! Does anyone know how I can give support to my HD so it can write these files?

Thanks!

---

### Post by _sAm_ on 2008-11-16
1. What type of filesystem do you have on the external disk?

2. Could you show us some of the special characters from the Swedish files?

---

### Post by hjoakim on 2008-11-16
NTSF and the Swedish characters are å ä ö :)

I used a some time now to rename and delete files I don't use that have the special characters :guitar:

---

### Post by _sAm_ on 2008-11-16
> **hjoakim said:**
> NTSF and the Swedish characters are å ä ö :)

I used a some time now to rename and delete files I don't use that have the special characters :guitar:

There is lots of characters that NTFS filesystem do not let you use on files/folders(they are not supported at all), like  \/:*?@<>|. The filesystem on Ubuntu will let you use them, but if you do you can not save them on NTFS later. My solution was to reformat my external disk to ext3.

Swedish characters should work just fine on NTFS, just like the Norwegian æ,ø,å :-) So my guess you are using some of those special characters mention above.

Edit: Thunar filemanager can rename files for you faster then doing it manually.

---

