---
title: "Azureus version update intallation problem"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Santooka on 2009-01-30
Dear All,

each time Azureus downloads a new update and tries to restart and install it fails and shows this message:

```
Error

Installation of at least one component failed. See <A HREF="http://azureuswiki.com/index.php/Failed_Update">AzureusWiki: Failed Update</A> [Azureus2_4.1.0.0.jar,install.act]
```

and after that it shows this and tries to restart again

```
Warning

The location '/usr/share/vuze' isn't writable, this update will probably fail. Check permissions and retry the update
```

so what solution do u suggest that i do that i make /usr/share/vuze be writable?!

how can i change all the / permissions so that i make my user as admin or root of all the system who can read and write on everything?

---

### Post by taurus on 2009-01-30
You definitely don't want to change permissions and ownerships of all the files outside your $HOME.  Doing so can trash your machine beyond repair.  However, you can change the permissions to /usr/share/vuze directory so you can write to it.

```
sudo chmod -R 777 /usr/share/vuze
```
Now, see if you can update azureus.  Again, _do not_ run that command for / or you will be sorry you did.

---

### Post by Santooka on 2009-01-30
man this really worked, really nice!!!!

thank u so much

---

### Post by sayantandas on 2009-05-15
thanks dude. it worked .

---

