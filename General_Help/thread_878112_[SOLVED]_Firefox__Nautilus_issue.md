---
title: "[SOLVED] Firefox / Nautilus issue"
date: 2008-08-02
forum: General Help
---

### Post by seamuso on 2008-08-02
Hardy x64, FF3.01

Right clicking on any supported file and choosing "open in firefox" no longer does so (double clicking is the same, nothing happens)

for instance, dbl click / right click -> "open in firefox"  whatever.html (.jpg, .php) won't launch firefox or open in a new tab as it has previosly done.

I can however right click -> open in konqueror and things open correctly.

Default browser is set to firefox ..

```
seamuso@blue-buntu:~$ sudo update-alternatives --config x-www-browser

There are 2 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/firefox-3.0
 +        2    /usr/bin/konqueror

Press enter to keep the default[*], or type selection number: 

```

it's also set in system -> preferences -> preferred apps.

Obviously I've managed to disable something, I just am not sure where to go to re-enable. Any ideas?

---

### Post by mbarak on 2008-08-02
what happens when you open something in the terminal?
```
firefox /path/to/page.html
```

---

### Post by seamuso on 2008-08-02
> **mbarak said:**
> what happens when you open something in the terminal?
```
firefox /path/to/page.html
```

firefox in and of itself works correctly, the trigger between nautilus and firefox is broken.

All my other apps (gimp, bluefish, etc) launch correctly through nautilus.

It's a pain in the butt when I'm working on things in a remote directory.

---

### Post by mbarak on 2008-08-02
Right click on your html - go to Open With - click on firefox
if that doesn't work, type in "firefox" (no capitals) in the "custom command" box

---

### Post by seamuso on 2008-08-02
> **mbarak said:**
> Right click on your html - go to Open With - click on firefox
if that doesn't work, type in "firefox" (no capitals) in the "custom command" box

I have .. ;)

[quote=seamuso]
Right clicking on any supported file and choosing "open in firefox" no longer does so (double clicking is the same, nothing happens)

for instance, dbl click / right click -> "open in firefox" whatever.html (.jpg, .php) won't launch firefox or open in a new tab as it has previosly done.
[/quote]
[quote=seamuso]it's also set in system -> preferences -> preferred apps.[/quote]

---

### Post by aysiu on 2008-08-02
Launch Nautilus from the command-line: ```
nautilus
``` and then right-click the file and try to open it with Firefox. If there are any error messages in the terminal, post them back here.

---

### Post by seamuso on 2008-08-02
hmm .. fixed it, but I'm not sure why it stopped working with the default config.

I had to set the full filepath ( /usr/bin/firefox ) and it started to work again. Go figure.

---

