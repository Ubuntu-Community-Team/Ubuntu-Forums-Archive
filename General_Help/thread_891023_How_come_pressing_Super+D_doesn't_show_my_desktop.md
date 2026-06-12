---
title: "How come pressing Super+D doesn't show my desktop?"
date: 2008-08-15
forum: General Help
---

### Post by Sam324 on 2008-08-15
How come pressing Super+D doesn't show my desktop?  I tried setting the key combination to perform this task, but upon holding Super, about to press D, it immediately sets the key combination to just "Super L".  What wouldst thou deau?

---

### Post by drs305 on 2008-08-15
You might check gonf-editor's apps/metacity settings to see if you have the single "Super_L" , "Super_R" or "Super" key assigned to something already. 

I use gconf-editor to assign my shortcuts. For some reason, I cannot get <Super_L>d or <Super_R>d to work individually. However, I ***can*** get <Mod4>d or <Super>d to work using *either* Super key (L or R). If you want either Super key to work, run this command:
```

gconftool-2 --set --type string /apps/metacity/global_keybindings/show_desktop '<Mod4>d'

```
or
```

gconftool-2 --set --type string /apps/metacity/global_keybindings/show_desktop '<Super>d'

```

---

### Post by mgmiller on 2008-08-15
The standard key combination for this in Ubuntu is ctrl/alt/d.  If you want to change that, run the configuration editor.
```
gconf-editor
```On the left side, you will then navigate to:
/apps/metacity/global_keybindings

On the right side of the screen, scroll down to the "show_desktop" entry and double click it.  The default entry says:
```
<Control><Alt>d
```change this to:
```
<super>d
```When you hit enter, the change take affect immediately.

Ideally, you should glue an ubuntu logo over the windows logo on the super key when you do this.

---

### Post by bhagwad on 2009-04-29
Here's how to do it with the GUI:

[http://warrence.com/tech/?p=22](http://warrence.com/tech/?p=22)

---

### Post by Leed on 2009-04-29
have you tried setting it in compizconfig-settings-manager?

---

