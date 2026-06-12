---
title: "Post your DMENU scripts with screenshots"
date: 2008-07-24
forum: General Help
---

### Post by Diabolis on 2008-07-24
I just started using [dmenu]("http://www.suckless.org/programs/dmenu.html") and I want to see how others have customized it.

If you don't have it already:
```
sudo apt-get install dmenu
```

> **cardinals_fan said:**
> Install it and make a script with the following:```
#!/bin/sh
$(dmenu_path | dmenu -fn '-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*' -nb '#000000' -nf '#FFFFFF' -sb '#0066ff')

```
Bind the script to your preferred key combo, and enjoy!

[[IMG]http://farm4.static.flickr.com/3223/2707637070_f893a83424_m.jpg[/IMG]]("http://www.flickr.com/photos/silvag/2707637070/")

---

