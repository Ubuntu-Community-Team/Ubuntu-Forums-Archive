---
title: "Hanvon tablet small problem &quot;hanvon.ko&quot;"
date: 2015-08-11
forum: Hardware
---

### Post by LioNeeZ on 2015-08-11
_**Hello everyone**_,
I would like to start by saying that I am very new to linux so often when I manage to get things working somehow on my other laptop which has lubunutu (I am using on my other laptop Ubunutu).
Anyway the problem is that I cant remember how I got my tablet working on my other pc, I am pretty sure I am missing some stuff maybe a ppa or some basic commands.
[PHP]
make hanvon.ko
make: *** No rule to make target `hanvon.ko'.  Stop.[/PHP]
even when I use sudo I get the same error, but I remembered than that actually all you need to do is make the files by running Makefile or hanvon.c, but when I run them I get this:
when I run **". Makefile"**:
[PHP].PHONY:: command not found
obj-m: command not found
all:: command not found
No command 'shell' found, did you mean:
 Command 'bshell' from package 'avahi-ui-utils' (universe)
 Command 'pshell' from package 'python-pyramid' (universe)
 Command 'shelr' from package 'shelr' (universe)
 Command 'spell' from package 'spell' (main)
 Command 'lshell' from package 'lshell' (universe)
shell: command not found
PWD: command not found
make: *** /lib/modules//build: No such file or directory.  Stop.
clean:: command not found
No command 'shell' found, did you mean:
 Command 'shelr' from package 'shelr' (universe)
 Command 'spell' from package 'spell' (main)
 Command 'pshell' from package 'python-pyramid' (universe)
 Command 'bshell' from package 'avahi-ui-utils' (universe)
 Command 'lshell' from package 'lshell' (universe)
shell: command not found
PWD: command not found
make: *** /lib/modules//build: No such file or directory.  Stop.
No command 'archive:' found, did you mean:
 Command 'archived' from package 'sympa' (universe)
archive:: command not found
[/PHP]
When I run **". hanvon.c"**:
[PHP]bash: hanvon.c: line 13: syntax error near unexpected token `DRIVER_AUTHOR'
bash: hanvon.c: line 13: `MODULE_AUTHOR(DRIVER_AUTHOR);'
[/PHP]
clearly I am missing something, but as I am new to linux I cant really pin point what.
could someone please help me understand/fix this problem please?

Thx for your time.
~***[COLOR=#ff0000]Red.ChickenN[/COLOR]***

---

### Post by coffeecat on 2015-08-11
Welcome to the forum!

I presume you mean you are trying to get a Hanvon **pen** tablet working with a computer running Ubuntu. The Ubuntu Phone and Tablet forum is for small devices such as phones and tablets (the ones that look a bit like an iPad) running Ubuntu. So...

*Thread moved to **Hardware**.*

Good luck.

---

### Post by LioNeeZ on 2015-08-12
Never mind, I managed to get it working.
I followed this post: [http://ubuntuforums.org/showthread.php?t=2096052](http://ubuntuforums.org/showthread.php?t=2096052) to get it working, I guess the problem was that I typed "**make hanvon.ko**" thinking it needs to make the file but in actuality you need to only use "**make**" and it does the rest from within the folder.
Big thx**[COLOR=#C61919] Sandyd [/COLOR]**[COLOR=#000000]and sorry for my misunderstanding.[/COLOR]

---

