---
title: "open several terminal windows script"
date: 2008-08-26
forum: General Help
---

### Post by dapim on 2008-08-26
how to open several terminal scripts at the same time,
some script or something??
how to open a terminal script in shell??

---

### Post by jigsaws on 2008-08-26
What do you mean?

#!/bin/bash
xterm -e "tail -f /var/log/messages" &
xterm -e "tail -f /var/log/messages" &

---

### Post by qstraza on 2008-08-26
> **dapim said:**
> how to open several terminal scripts at the same time,
some script or something??
how to open a terminal script in shell??
Rephrase the question please ;)

---

### Post by dapim on 2008-08-26
xterm doesn't work

i just want open 5 shell terminals, from comand line? there is any way of doing it? otherwise i have to do CRTL+SHIFT+N ...

---

### Post by kaibob on 2008-08-26
> **dapim said:**
> xterm doesn't work

i just want open 5 shell terminals, from comand line? there is any way of doing it? otherwise i have to do CRTL+SHIFT+N ...

The following will open five terminal windows from the command line the same as ctrl+shift+n. This could be put in a script.

> gnome-terminal ; gnome-terminal ; gnome-terminal ; gnome-terminal ; gnome-terminal

Like the others, I'm not sure what you want to do.

---

### Post by qstraza on 2008-08-26
```
konsole
```

^^ if you are on kubuntu, for ubuntu do as kaibob said

---

### Post by drs305 on 2008-08-26
Have you tried an app called "screen"? It can run multiple terminals in tabs and has profile settings that will allow it to open with all sorts of configurations, including multiple tabs.

```
sudo apt-get install screen
```

---

### Post by dapim on 2008-08-27
gnome-terminal do the job,
but instead of open new windows i would like to open 5 new tabs in the same gnome terminal  by comand line?

---

### Post by LateNiteTV on 2008-08-27
```

#include <stdio.h>

int main(void)
{
int i;

for(i=0; i<5, i++){
     execl("xterm", 0);
     }
return 0;
}
```
 ??????????

---

### Post by qstraza on 2008-08-27
you could write a program which sends key codes "ctrl alt new" but its really easy to just press it on your keyboard. Obviously you dont need a script which will run in background because you want tabs to be opened on gnome-terminal (X server).

Whats the point?

---

### Post by roelpeeters on 2008-08-27
Hi!

This might be not exactly what you are looking for (I still don't understand your use case) however, it might help. Terminator is a package that allows to have several terminals open in one window, organized in a grid.

I have to thank debuntu for this:
[http://www.debuntu.org/terminator-a-multi-view-terminal](http://www.debuntu.org/terminator-a-multi-view-terminal)

Code to install the package:
```

sudo aptitude install terminator

```

Hope this helps to get what you need.

Roel

---

### Post by qstraza on 2008-08-27
screen can do this also:P
i think

---

### Post by dapim on 2008-08-27
the point is to learn. 
go for a bath in bled or listen sidharta , instead of un-intelligents questions

---

### Post by amitkher on 2008-08-27
gnome-terminal claims that the following opens a new tab in last opened window
```

gnome-terminal --tab

```

This does not work for me (gnome-terminal 2.22.2). Maybe it will work for you.

---

### Post by qstraza on 2008-08-27
[quote=dapim]go for a bath in bled or listen sidharta , instead of un-intelligents questions[/quote]
dont flame me, ok?

---

### Post by forger on 2008-08-27
To open multiple tabs in gnome-terminal:
```
gnome-terminal --tab --tab --tab
```

---

### Post by dapim on 2008-08-27
THANK YOU VERY MUCH FORGER, it is always a pleasure learn something with intelligent people like you.

---

### Post by amitkher on 2008-08-27
> **forger said:**
> To open multiple tabs in gnome-terminal:
```
gnome-terminal --tab --tab --tab
```

Does this work for you? For me, it will always open a new window even if an existing gnome-terminal window is open. gnome-terminal --help says
```

--tab                                           Open a new tab in the last-opened window with the default profile. More than one of these options can be provided.

```

---

### Post by forger on 2008-08-27
> **amitkher said:**
> Does this work for you? For me, it will always open a new window even if an existing gnome-terminal window is open. gnome-terminal --help says
```

--tab                                           Open a new tab in the last-opened window with the default profile. More than one of these options can be provided.

```

[https://bugs.launchpad.net/gnome-terminal/+bug/117333](https://bugs.launchpad.net/gnome-terminal/+bug/117333)

He asked to open a new window with a lot of tabs, not to open a tab in the latest window ;)

---

