---
title: "auto start program for all users"
date: 2008-10-13
forum: General Help
---

### Post by ilovelinux33467 on 2008-10-13
Hi I was wondering if there was a way to automatically start a program for users when they log in without having to manually changing auto start settings for each account

thanks

---

### Post by lovinglinux on 2008-10-13
I really don't know if there is another way, but you could use a script for that.

I have a "session" script on my bin folder that starts several programs and I have added this script to the session manager, so when I login the session manager launches the script and thus all applications configured in the script are launched too. You will still need toconfigure the session manager to start the script for each user, but at least is just one thing to add to the session manager.

An example of script would be:

```

#!/bin/bash

fusion-icon
emerald --replace
easystroke
specto
checkgmail
tomboy
cairo-dock

```

This will launch most applications I need on startup. Additionally, you can add a timer for each application to start, so they don't try to launch all at the same time, thus not overloading the machine and reducing desktop loading time. For example:
```

#!/bin/bash

fusion-icon &
emerald --replace &
sleep 5 && easystroke & specto & checkgmail & tomboy &
sleep 10 && cairo-dock
```

---

### Post by cyclobs on 2008-10-13
or you can use the programs start code in the menu system->Perfences->Session.


very easy and it works very well. you can write a script up to start custom stuff or such. i have a script here that overclocks my GFX card everytime i log in cause i got sick of typing the command all the time >.<

---

### Post by lovinglinux on 2008-10-13
> **cyclobs said:**
> or you can use the programs start code in the menu system->Perfences->Session

That is exactly what the OP is trying to avoid. He/she does not want to add all programs needed on start to all users session managers. Kind of time consuming, so I guess the script is the way to go.

---

