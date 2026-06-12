---
title: "help with script"
date: 2008-09-25
forum: General Help
---

### Post by grumpylad77 on 2008-09-25
I have NO experience with this sort of thing so, if someone could point me in the right direction...

I am looking for a way to be able to launch wpa_supplicant and then, once i am connected, launch the vpn script for my schools network. It is getting to be a real pain having to do that manually each time i want to connect.

Thanks

---

### Post by bodhi.zazen on 2008-09-25
Put the commands in a file. Start the file with :

#!/bin/bash

Make it executable.

Call it with /path/to/file or make a launcher.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

