---
title: "Firefox Question"
date: 2008-09-26
forum: General Help
---

### Post by Aiello on 2008-09-26
When opening a link to a webpage in an application such as Evolution or Skype, Firefox goes to my homepage as apposed to the linked page. Any suggestions on how to fix this? Thanks!

---

### Post by Aiello on 2008-09-27
Any ideas?

---

### Post by kokkus on 2008-09-27
In firefox, type about:config, click enter, right click and add new, strang, name it network.protocol-handler.app.apt+http , value: /usr/bin/skype

This was for skype.
And the same thing with other programs you use to open sites but change the value command for each program.

---

### Post by lswb on 2008-09-27
Open Main menu/System/Preferences/Preferred Applications/Internet. Make sure that "Firefox" is selected as the web browser and that the command is "firefox %s".

---

### Post by Aiello on 2008-09-28
Unfortunatly, neither of these methods seem to work. Even after editing the config, it still opens my home page. And if a set the prefered application command to firefox %s, it doesn't open anything. Should I just completly remove Firefox through synaptic and reinstall?

---

