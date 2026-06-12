---
title: "php Scripts in Shell ?"
date: 2008-10-10
forum: General Help
---

### Post by apocalypsxx on 2008-10-10
Hi I`m trying to get a php script to run in a shell


#!/usr/bin/php
<?php
echo "hello blah blah";
?>



sn00pyc0re@n30:~/Documents/Scripts$ ./Hello.php
bash: ./Hello.php: /usr/bin/php: bad interpreter: No such file or directory



So i did a search & found 3 other locations none of which worked..

I`m stuck..:confused:

any help much appreciated..

---

### Post by Titan8990 on 2008-10-10
Php can't be interpreted through the shell. You need to view php content from a web browser.


Also, /usr/bin/php does not exist unless you made something there.

---

### Post by DrMega on 2008-10-10
> **Titan8990 said:**
> Php can't be interpreted through the shell. You need to view php content from a web browser.

Apparently this isn't true anymore. I've read that PHP can be used in a non-web environment now, but I'm not sure how. Someone here will know.

---

### Post by apocalypsxx on 2008-10-10
me@n30:~/Documents/Scripts$ ./Hello.php
./Hello.php: line 2: ?php: No such file or directory
Hello Me!
./Hello.php: line 4: syntax error near unexpected token `newline'
./Hello.php: line 4: `?>'
me@n30:~/Documents/Scripts$ 

got it working kinda...
checked code for sysntax error there is none..
changed#!/usr/bin 
to #!/bin/bash as suggested in another thread
still not quite right though.

---

### Post by apocalypsxx on 2008-10-10
maybe of some interest..:)



[http://www.myokyawhtun.com/tips-tricks/how-to-run-php-script-in-shell.html/](http://www.myokyawhtun.com/tips-tricks/how-to-run-php-script-in-shell.html/)

[http://www.phpbuilder.com/columns/darrell20000319.php3](http://www.phpbuilder.com/columns/darrell20000319.php3)

[http://forums.devnetwork.net/viewtopic.php?f=30&t=78881](http://forums.devnetwork.net/viewtopic.php?f=30&t=78881)
----------------------------------------------------------------------------------------------------------------

REMEMBER dont mess about with stuff like this unless you are wearning a safety harness..hard hat..Hi-Vis jacket
& prepared to reintall your OS if it all goes very very wrong !!

---

### Post by KeyserSoze93 on 2008-10-10
Make sure you have the php5-cli package installed, then try

#!/usr/bin/php5

Make sure it's php5, that works for me in my php shell scripts.

---

### Post by hyper_ch on 2008-10-10
install php5-cli and then you can run it by

```

php5 script.php

```

---

### Post by apocalypsxx on 2008-10-10
Thnx guys..
php-cli installed & works like a dream :)
in the words of Alan Partridge-"Back of the Net !"

:guitar:

---

