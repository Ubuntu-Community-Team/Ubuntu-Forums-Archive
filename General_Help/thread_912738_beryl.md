---
title: "beryl"
date: 2008-09-07
forum: General Help
---

### Post by douggiephresh on 2008-09-07
Im trying to install a vista theme that i saw on the beryl section at gnomelook. how do i do that?  i have emerald

---

### Post by techstop on 2008-09-07
> **douggiephresh said:**
> Im trying to install a vista theme that i saw on the beryl section at gnomelook. how do i do that?  i have emerald

You download the theme somewhere (Desktop?). You need to get a file with a .emerald extension. Either the file will be downloaded like that, or you need to extract it from an archive. 

Then you open Emerald theme manager, click Import, then browse to the file you just downloaded/extracted. 

I don't have ubuntu open at the moment, but this is the general gist of it. See link in sig for more info.

---

### Post by douggiephresh on 2008-09-07
Now, I have installed them in Emerald, and I can see them, but how do I make it work? Is there more settings that I have to play with?

---

### Post by techstop on 2008-09-07
The answer to that is in my link too. :wink:

> Before you can start using Emerald themes though, you will need to tell Compiz to use Emerald to decorate the windows instead of metacity. To do this, go into the Window Decoration plugin in ccsm (found under the Effects category) and enter the following in the Command text box;

```
emerald --replace
```

You will also need some Emerald themes which you can find here;

[www.beryl-themes.org](www.beryl-themes.org)

To install the new theme, just follow the directions that you usually get with the theme. You will usually just click “Import” within Emerald and then find the theme (ending in .emerald) you just downloaded. You might have to extract it from an archive first. You will also need to restart Emerald to see your new theme, you can do this by rebooting, or by pressing Alt+F2 and entering

```
emerald --replace
```

---

