---
title: "Gdeb problems"
date: 2008-08-14
forum: General Help
---

### Post by wildman4god on 2008-08-14
When i download a .deb file from the net it pops up and ask me if i want to save it or open it with an application, i select open with gdeb, which is installed on my machine and when i click ok it gives me an error and says it can not open file because associated helper app does not exits, it does exist and when i save the file i can then open it up with gdeb and install it, its not that importaint but i find it anoying and would like it to work correctly, please help and thanks in advanced.

---

### Post by sayakb on 2008-08-14
Open firefox. Goto Edit->Preferences->Applications and scroll down to **Software (application/x-deb) **and change the associated application from *Always ask* to *Use GDebi package install...*

---

### Post by wildman4god on 2008-08-14
i did do this, it still ask and it still can't use gdeb until i save the file and then run it through gdeb.

---

### Post by sayakb on 2008-08-14
I can't exactly guide since I don't have the above mentioned problem. Try selecting *User other..* and navigate to */usr/bin* and select *gdebi* from the file list.

EDIT: This ^^^^ doesn't work.. lol. Maybe someone else can help :)

---

### Post by wildman4god on 2008-08-14
I tried that it didn't work so i reselected the origanal use gdeb package installer option and now it works fine, thanks anyway.

---

