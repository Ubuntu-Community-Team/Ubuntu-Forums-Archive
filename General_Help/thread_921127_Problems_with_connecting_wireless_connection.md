---
title: "Problems with connecting wireless connection"
date: 2008-09-15
forum: General Help
---

### Post by ft566 on 2008-09-15
I accidently deleted something from the list of programs that run on startup. I think it was the wireless network manager or something like that, im not sure. Now, when I turn my computer on, it wont connect to the internet. Could anyone help me with this?

---

### Post by aloshbennett on 2008-09-16
Must be the Network Manager.
Try running 
```
nm-applet --sm-disable
```
from command prompt and if that solves your problem, you can add it to startup.

---

### Post by ft566 on 2008-09-16
> **aloshbennett said:**
> Must be the Network Manager.
Try running 
```
nm-applet --sm-disable
```
from command prompt and if that solves your problem, you can add it to startup.

thank you. that seems to work but only as long as the terminal window is open. When i close out the terminal window it disconnects from the internet and the wireless netword icon on the panel goes away. any idea on the cause of this?

---

### Post by aloshbennett on 2008-09-16
you could add it to your startup list.

from System-> preferences -> session
Add a program with the following details:
```

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager Applet

```

A logout/login and things should be back to normal for you :-)

---

### Post by ft566 on 2008-09-16
that worked. thanks alot

---

