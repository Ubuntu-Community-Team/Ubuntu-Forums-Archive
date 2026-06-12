---
title: "Manually start apache"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-02-09
I would like to install apache, thats a no problem with me. but I want it to start ans stop manually. By default, when you install apache, it will automatically start whenever the system starts. how can I remove that? I dont want it automatically start, coz I dont need apache everytime I use my computer. I just want to manually start it when I need it.

Hope you could give me suggestions.

Thanks.

---

### Post by el3ktro on 2006-02-09
The easiest way to control the init scripts (/etc/init.d/...) is to apt-get install sysv-rc-conf. This is a little tool which nicely lists all your init scripts, and you can select/deselect them as you wish.

Tom

---

### Post by wizzkid on 2006-02-09
Thanks so much! :) I will try this out!

---

### Post by engla on 2006-02-09
For starting apache, I think you have a command called apachectl made for that. So manually starting it should be something like

'sudo apachectl start'

---

### Post by dickohead on 2006-02-09
or more universially if sysv-rc-conf isn't available:

/etc/init.d/apache2 start
/etc/init.d/apache start

---

### Post by wizzkid on 2006-02-10
Thanks, I just un-ticked the apache2 on rcconf... so when system starts, apache2 wont start... I want it to start manually whenever i need it.

Thanks

---

