---
title: "command for visiting webpage.."
date: 2008-07-23
forum: General Help
---

### Post by Mia_tech on 2008-07-23
is there a command out there that would allow me to visit a webpage...I've tried with wget, but instead of visiting the page this only download the page

any help appreciated

thanks

---

### Post by LaRoza on 2008-07-23
"firefox"

If you want a text browser, try links, links2, elinks, lynx and such.

---

### Post by Mia_tech on 2008-07-23
yep but typing firefox "webpage" would actually open the browser... I want to be able to do this from the shell open lets say 5 instances of the page and then kill the process
I'll take a look at the others you mentioned, I thought that lynx is only for mirroring sites on your localmachine

thanks

---

### Post by LaRoza on 2008-07-23
> **Mia_tech said:**
> yep but typing firefox "webpage" would actually open the browser... I want to be able to do this from the shell open lets say 5 instances of the page and then kill the process
I'll take a look at the others you mentioned, I thought that lynx is only for mirroring sites on your localmachine

thanks

No, lynx is a web browser in the terminal.

---

### Post by Mia_tech on 2008-07-23
ok I'm using lynx but why I don't see the visit counter go up.. it is not registering the visits

is it because some html or javascript code do not execute when using text base browser?

thanks

---

### Post by pooyaplus on 2008-07-23
Just wondering if you need to telnet the pages!?

---

### Post by Mia_tech on 2008-07-23
> **pooyaplus said:**
> Just wondering if you need to telnet the pages!?

telnet the pages?...elaborate please


thanks

---

### Post by LaRoza on 2008-07-23
> **Mia_tech said:**
> telnet the pages?...elaborate please


thanks

You don't want to do that...

---

### Post by Mia_tech on 2008-07-23
I wouldn't want to do what... this is for testing and is in a save enviroment.. anyway I came with this little script it works the only problem is that it waits for user input like it waits for me to close the browser and then it moves to the next instruction...I would like to open pages x amount of times and each in a separate tab...I looked at firefox help but I couldn't find anything...
here's the script...```
#!/bin/bash

A=0

while [ $A -le 5 ] ; do firefox http://website.com
count=`expr $A + 1`

done

killall firefox

exit

```

any help appreciated

thanks

---

### Post by retrow on 2008-07-23
You could record a macro in xnee, and replay your recording from shell script in a loop.

---

### Post by Mia_tech on 2008-07-23
I'll try it.. but I'm really trying to keep this simple, and if it could be done from a script even better

thanks

---

