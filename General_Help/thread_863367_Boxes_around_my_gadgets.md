---
title: "Boxes around my gadgets"
date: 2008-07-18
forum: General Help
---

### Post by sparkyjoe34 on 2008-07-18
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78169&stc=1&d=1216397542[/IMG]
As you can see above everytime I boot my laptop and Google Gadgets loads there are boxes around my gadgets. If I right click on the google icon and close them and then restart them with Alt-F2 --> ggl-gtk they come back up without the boxes and look great. Has anyone else had this problem? How can it be fixed?

---

### Post by DaymItzJack on 2008-07-18
This is a pure guess but:

I'm assuming Google notices you don't have compiz currently running so it goes to a backup "do-not-use-transparency" setting and adds those borders around the side. To test if this is true, make a startup script that loads compiz then Google Gadgets.

---

