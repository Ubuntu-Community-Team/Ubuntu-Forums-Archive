---
title: "Editing xorg.conf  E45: 'readonly' option is set (add ! to override)"
date: 2008-10-06
forum: General Help
---

### Post by africanprinceily on 2008-10-06
Hello, Ubuntu Gods. My computer can never return from sleep mode. To fix this problem I need to edit 'xorg.conf' which is a read only file. Within the file there they tell me to type this in the command line after editing the file: 

```
[CODE]sudo dpkg-reconfigure -phigh xserver-xorg
```[/CODE]

I try to edit the file and this error message comes up on the vi editor
"E45: 'readonly' option is set (add ! to override)"
I type :!wq and :wq! but the file still doesn't save

Help Please,
Imani

---

### Post by alynx on 2008-10-06
if you try to edit the file like this 

sudo vim /etc/X11/xorg.conf

edit the file

escape then wq!

it should work.

you can restart X with ctrl + alt + backspace

---

### Post by Archmage on 2008-10-06
For me it sounds like you forget the "sudo" before the edit comamnd.

---

