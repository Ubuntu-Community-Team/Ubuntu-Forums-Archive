---
title: "Compiz &quot;Expo&quot; plugin won't work at all"
date: 2008-09-13
forum: General Help
---

### Post by MakotoTheKnight on 2008-09-13
Expo was working great up until a few months ago.  I hadn't tinkered with it then since it really wasn't necessary, but I'd like to restore it short of a complete reinstallation of Compiz.

Here's the error:

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Any help is appreciated.

---

### Post by Oldsoldier2003 on 2008-09-13
Moved to Desktop Effects and given a free bump.

---

### Post by Squish on 2008-09-13
One of your hot corners, or edges that you put your mouse over to activate expo, is configured wrong. It has a value in it that doesnt make sense

I think all you need to do is go to the compizconfig>expo>bindings,

and make sure they are all set properly

---

### Post by MakotoTheKnight on 2008-09-14
I still get this message, after trying what you said:

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'expo'

Not sure what to do at this point.

---

### Post by Squish on 2008-09-15
hmmm,

As a last resort, you could try updating to the latest and greatest compiz. I have gotten my fair share of compiz troubles, but getting through them is worth it. I actually do believe I got a similar error, when I was trying to get some external plugins to work. Cant remember what I did, I think I opted to go for a clean install, seeing as it is so easy, and quick... made more sense.

buuut you prob dont want to do that, and I do not call that helpful advice.

I would say to go to synaptic, remove the plugins, and install compiz 7.6

---

### Post by northern lights on 2008-09-15
> **MakotoTheKnight said:**
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

> **Squish said:**
> One of your hot corners, or edges that you put your mouse over to activate expo, is configured wrong. It has a value in it that doesnt make sense.
I think all you need to do is go to the compizconfig>expo>bindings, and make sure they are all set properly

While the initial explanation is true, this problem cannot be solved just by adjusting the bindings in CCSM. This error may appear when upgrading from a pre 0.6.2 compiz to a newer version. The way bindings were chosen in the GUI had been changed in between.

Anyhow, to restore functionality, run ```
gconf-editor
```navigate to '/apps/compiz/plugins/scale/allscreens/options' and set the value to 'Disabled', for instance. Now set your bindings again.

---

### Post by MakotoTheKnight on 2008-09-17
That still doesn't work.

I tried to uninstall/reinstall it, didn't help matters much at all.

Does anyone have any more ideas?

---

### Post by northern lights on 2008-09-17
It must work, at least in slight alteration. Instead of setting it to "Disabled", leave it blank.

---

### Post by MakotoTheKnight on 2008-09-22
Unfortunately, none of that is working.  I dunno what to do at this point.

---

