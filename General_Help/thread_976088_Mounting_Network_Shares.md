---
title: "Mounting Network Shares"
date: 2008-11-09
forum: General Help
---

### Post by Selphy on 2008-11-09
Hello,

I've recently figured out how to mount a network share folder in Xubuntu and view folders on my windows network. Problem I'm having is every time I log out and back in I have to do the following

```
Chmod 600 ~/.smb/fusesmb.conf
fusesmb /media/network
```

to allow me to see my shared network folders. Is there any way I can keep from doing this or perhaps have something I can click on to do this automatically? Somewhere I saw someone say you can writ e a script to do something like this but the problem I'm having is I have no idea how to write a script file. Anyone have any ideas on how to solver this?

---

### Post by taurus on 2008-11-09
You mean the script like this?

```

#!/bin/bash
# network.share script...
#
chmod 600 ~/.smb/fusesmb.conf
fusesmb /media/network

```
Then, you just need to make it executable so you can run it, network.share.

```
chmod 755 network.share
```

---

### Post by Selphy on 2008-11-09
> **taurus said:**
> You mean the script like this?

```

#!/bin/bash
# network.share script...
#
chmod 600 ~/.smb/fusesmb.conf
fusesmb /media/network

```
Then, you just need to make it executable so you can run it, network.share.

```
chmod 755 network.share
```

Thank you Taurus, how exactly do I go about making this script, I'm still quiet new to Linux.

---

