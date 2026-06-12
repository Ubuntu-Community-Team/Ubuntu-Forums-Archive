---
title: "Emerald Theme Manager Problem"
date: 2008-07-15
forum: General Help
---

### Post by Techrocket9 on 2008-07-15
For me to get emerald themes to work, I have to open a terminal, type ```
sudo emerald --replace
``` I then have to open the emerald theme manager and select a theme. Next, I close the terminal and open a new one. While the terminal is closed, I have no window decoration. There I type ```
emerald
``` If I close the terminal window, I loose the theme. How can I fix it so that I do not have to do this whenever I log on?

---

### Post by Execute_Method on 2008-07-15
They way I do this is:

```
emerald --replace & exit
```

I've been doin it like this for a while, always works.

When I found this fix, it had been stated there was a bug with emerald & Hardy.

I haven't cared enough to find a different way cause it works.

I ended up putting it in a a script that runs at startup like so:
```
#!/bin/bash
sleep 5
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
sleep 5
emerald --replace
```

you may not need the always indirect option, just put the  compiz command the way you would in terminal.

---

### Post by Execute_Method on 2008-07-15
BTW you don't need to be super user to change window managers.

---

### Post by tuxxy on 2008-07-15
System > Preferences > Sessions 

Add compiz as a startup program using 

```
emerald --replace
```

This way Compiz will be loaded by default at startup

---

### Post by Techrocket9 on 2008-07-16
I will try that, tuxxy. [COLOR=Red]Edit[/COLOR]: It did not work. It did not affect anything.

Execute_Method, how (exactly) would I do that, assuming what I am trying now does not work?

[IMG]http://www.todojuegos.com/modules/Forums/images/smiles/gathering.gif[/IMG]

Thanks for all help.

---

### Post by DaymItzJack on 2008-07-16
I put
```
#!/bin/bash
sleep 5
compiz --replace &
sleep 5
emerald --replace & exit
```
In a file called ".compizemerald" in my home folder. Then type in terminal
```
chmod +x ~/.compizemerald
```
Then add "~/.compizemerald" into the sessions manager.

This however did take forever to load.

---

