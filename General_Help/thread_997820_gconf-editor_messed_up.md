---
title: "gconf-editor messed up"
date: 2008-11-30
forum: General Help
---

### Post by rolodoom on 2008-11-30
I installed intrepid and I realized that I can't see home, trash, computer icon on desktop, so I run gconf-editor, go to nautilus prefrences and activate the icons apps/nautilus/desktop/ etc... and then I start playing with the value of home_icon_name, and after a while I accidentally deleted it. It's possible to restore initial gconf-editor settings??

---

### Post by bsmith1051 on 2008-12-21
No one else has responded, eh?  You should ask over at gnomesupport.org since this is more of a Gnome question than Ubuntu.

---

### Post by logos34 on 2008-12-22
> **rolodoom said:**
> then I start playing with the value of home_icon_name, and after a while I accidentally deleted it. It's possible to restore initial gconf-editor settings??

try 

right-click in modification pane>"New Key"

name: home_icon_name
type: integer
value: leave blank or use 0

If you get an error, right-click on the key and select "unset key"

that's what I had to do

---

