---
title: "Custom menu launcher doesn't have permission to do anything?"
date: 2008-10-25
forum: General Help
---

### Post by Queue29 on 2008-10-25
This worked fine in 8.04.1, I went to 8.10 RC today, and my customized menu launcher for the Arduino IDE doesn't work anymore. Instead I get, "Failed to execute child process "/home/seth/arduino-0011" (Permission denied)". 

This is the contents of the script that should execute:
```

#!/bin/sh

CLASSPATH=java/lib/rt.jar:lib:lib/build:lib/pde.jar:lib/core.jar:lib/antlr.jar:lib/oro.jar:lib/registry.jar:lib/mrj.jar:lib/RXTXcomm.jar
export CLASSPATH

# put the directory where this file lives in the front of the path, because
# that directory also contains jikes, which we will need at runtime.
#
cd /home/seth/arduino-0011

PATH=`pwd`/tools:${PATH}
export PATH

# put the directory with the native RXTX libs in the library path
LD_LIBRARY_PATH=`pwd`/lib:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

java processing.app.Base

```

---

### Post by dcstar on 2008-10-25
> **Queue29 said:**
> This worked fine in 8.04.1, I went to 8.10 RC today, and my customized menu launcher for the Arduino IDE doesn't work anymore. Instead I get, "Failed to execute child process "/home/seth/arduino-0011" (Permission denied)". 
........

Well, what are its permissions?

---

### Post by Queue29 on 2008-10-25
> **dcstar said:**
> Well, what are its permissions?

It has Read and Write permissions for all users, and the "Allow executing file as program" is checked.

It does invoke: 
```
java processing.app.Base
```
Would that be a problem now?

---

### Post by Keen101 on 2008-11-08
you could try a different method of creating a shortcut.

[http://ubuntuforums.org/showthread.php?t=949229](http://ubuntuforums.org/showthread.php?t=949229)

---

### Post by jamesstansell on 2008-11-08
What are the permissions for /home/seth/arduino-0011 ?

---

