---
title: "bash background process help"
date: 2008-08-18
forum: General Help
---

### Post by boblemur on 2008-08-18
hey all, i was just wondering if someone could help with a quick yestion i have about scripting.

say i have a bash script:
```

#!/bin/bash

echo "hello"
sleep 1000&
echo "world"

kill <sleep command>

```
how can i find the pid for my sleep without running killall sleep?

---

### Post by amo-ej1 on 2008-08-18
You can use the build in $! variable for this (see [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html#table_03_03](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html#table_03_03) )

so your script would look like:

```

#!/bin/bash

echo "hello"
sleep 1000&
echo "world"
kill -9 $!

```

---

