---
title: "MSI WIND + packard bell viseo 230 screen: How to change the brightness?"
date: 2009-09-15
forum: Hardware
---

### Post by sdenel on 2009-09-15
Hello everybody!
I own an msi wind U100 which I connected to an external screen so that I have a dual screen, BUT I can't change the brightness of my external screen and therefore reading a text on it really explodes my eyes.
I already try to change it in a terminal but obviously it doesn't work:
> 
root@simon-laptop:/proc/acpi/video# ls
IGD
root@simon-laptop:/proc/acpi/video# cd IGD
# ls
CRT  DOS  info  LCD  POST  POST_info  ROM
# cd CRT
# ls
brightness  EDID  info  state
# cat brightness 
<not supported>
# echo 20 > brightness 
bash: echo: erreur d'écriture : Argument invalide (translation: Writing error: I don't want to collaborate with you)
So my question is: **is there a genius here that would help me?**
Thank you for your help,
Simon.

---

