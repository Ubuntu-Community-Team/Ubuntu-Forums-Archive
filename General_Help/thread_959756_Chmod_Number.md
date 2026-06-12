---
title: "Chmod Number?"
date: 2008-10-26
forum: General Help
---

### Post by ukera on 2008-10-26
Hai guise.  So I just installed apache, and PHP, in terminal.  So anyways, I go to /var/www in firefox, so that I can see the index.htm file there.  So then I do a simple:

[PHP]<?php
echo "test";
?>[/PHP]

Then I saved it to filesystem.  But it wouldn't let me save it there, then I tried to save to desktop, and it worked, I figured I could just go and drag and drop it to /var/www.  It still wouldn't work.  So I asked my friend, and he says I should chmod 777 it.  I'm not sure if that would be the best idea.  Then I said sure why not, so I asked for the command on the chmod number and he didn't know it so I googled.  and I got:

[PHP]ls -l[/PHP]

Then I seen that the chmod status is different then what I was expected I was thinking it would be numbers like 777 for example.  But it was more like this:

[PHP]drwxr-xr-x[/PHP]

Then maybe I thought I should try and go to terminal and get root then I would copy it from my desktop to /var/www, but I'm not quite sure of the command.. Any tips?

-ukera

---

### Post by Dr Small on 2008-10-26
This should help you out:
```
r = 4
w = 2
x = 1
```

So say I wanted to give a directory rw-r-r, I would use "644". For rwx-rx-rx, "755".

---

### Post by Zimmer on 2008-10-26
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

Best explanation I found...
from Nana....

---

### Post by jerome1232 on 2008-10-26
Me personally, I use another syntax method for chmod, not that the numbers are hard to learn it's just more human readable to me. Most people use the number system though.
some examples:
```

chmod ugo+rwx
# gives the owner (**u**), **g**roups, and all **o**thers **r**ead, **w**rite, and e**x**ecute permissions, this equivalent to 777, or -rwxrwxrwx.

# I don't think you can actually set this in real life it's just an example of removing permisions.
chmod ugo-rwx
# this removes **r**ead, **w**rite, and e**x**ecute permissions from the owner (**u**), **g**roup, and all **o**thers. aka 000 ----------.

#you can of course mix this up.
chmod ug+rwx,o-rwx
# that would give the owner and group members read, write, and execute permisions while removing all others read, write, and execute permisions. aka 770, -rwxrwx---

# last example
chmod u+rw,u-x,g+r,g-wx,o-rwx
# so that would be the same as 640, or -rw-r-----
```

---

### Post by ukera on 2008-10-26
Thanks for the quick replies guys. :D

But I ended up just doing:

[PHP]sudo chown -R ukera /var/www[/PHP]

@DrSmall, I didn't know that.  /me takes notes.  And thank the rest of you for helping me :)

-ukera

---

