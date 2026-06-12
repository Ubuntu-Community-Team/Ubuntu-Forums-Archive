---
title: "Bug? Custom network protocol handler not working (firefox or epiphany)"
date: 2008-11-05
forum: General Help
---

### Post by Yuzem on 2008-11-05
I am using hardy.
I want to add a new network protocol handler and it doesn't work.
The same happens in firefox and epiphany.

To reproduce:
```

#!/bin/bash

zenity --info --text "hello world"

```
Save that code and copy it to /usr/bin/myapp

In firefox addressbar go to about:config
Right clic and select add > string
For the string insert:
network.protocol-handler.app.myapp
The value:
/usr/bin/myapp

Now in firefox addressbar type:
myapp://anything

It should pop up a dialog asking if you want to allow that but you can't allow it.

---

### Post by lovinglinux on 2008-11-05
When Firefox prompts you to choose which application should handle the protocol, ignore the listed "myapp", browse the script and select it. Then select the thing to make it remember and click OK. This should work.

I don't know why this happens, but this is the way I'm making custom protocol handlers and works for me.

---

### Post by Yuzem on 2008-11-06
Thanks, it works now.

---

