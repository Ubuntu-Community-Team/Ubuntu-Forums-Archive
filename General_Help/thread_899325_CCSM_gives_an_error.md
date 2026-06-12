---
title: "CCSM gives an error"
date: 2008-08-24
forum: General Help
---

### Post by itsjareds on 2008-08-24
I had compizconfig working fine, but when I installed emerald and did emerald --replace, it brought me back to the original window manager, and there weren't any effects.

Tried running ccsm from the terminal, but it gave me this error:

```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/
allscreens/options/initiate_edge. Settings from this path won't be read. Try to 
remove that value so that operation can continue properly.
```

But there is no folder called /apps

Since I'm guessing this is why emerald isn't working, how can I fix it?

---

### Post by Diabolis on 2008-08-24
> /apps/compiz/plugins/scale/allscreens/options/initiate_edge

It is not a path to a file, it is a configuration key. Look it up by typing this command:
```
gconf-editor
```

---

