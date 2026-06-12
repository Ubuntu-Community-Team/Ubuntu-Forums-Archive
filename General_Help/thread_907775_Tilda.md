---
title: "Tilda"
date: 2008-09-01
forum: General Help
---

### Post by blackvd on 2008-09-01
Is there anyway to add a colored border to tilda? In preferences it has notebook border which when turned on is grey. Is there anyway to change the default color of that to say white? Looked in the config file and didn't see a color option for notebook border.

thanks.

---

### Post by x1a4 on 2008-09-06
Hi,

You may want to try Devil's Pie.  It's in the repos in package **devilspie**.  There's also a GUI for creating Devil's Pie rule files called [gDevilspie]("http://code.google.com/p/gdevilspie/").

Devil's Pie is a window matching daemon which allows you to perform actions on windows, including setting border colours.

---

### Post by blackvd on 2008-09-10
Hey thanks for the reply! To tell you the truth that program confusing the hell out of me. But I'll give it a go anyways. :)

---

### Post by x1a4 on 2008-09-10
> **blackvd said:**
> Hey thanks for the reply!

You're welcome. 

> To tell you the truth that program confusing the hell out of me. But I'll give it a go anyways. :)

There is an easy way of doing it.  First start gDevilspie and create devilspie rules.  Once all the rules are created use gDevilspie to start devilspie, which runs as a daemon.  The rules you create will be loaded when devilspie starts.  Add devilspie to your auto started applications to have it load when you log in.  To have it load at boot, add it to /etc/rc.local.  

To obtain information needed for gDevilspie, info like window_class which you would want to use for Tilda, use tools like xprop.  Run xprop in a terminal and click the window you want to see the properties of.

EDIT:  gDevilspie has a 'Get' button for getting window properties.  Select the properties you want to check for, like window_class, click 'Get' and select from a list of open windows.

EDIT2:  Never mind.  Just ran gDevilspie to double check if my answer was correct and it doesn't have a means to change border colours.  :(  You might want to try to set 'undecorate' to remove the border all together.  Not sure if it will work though, as 'undecorate' removes window manager decorations, and Tilda runs without it already.

---

