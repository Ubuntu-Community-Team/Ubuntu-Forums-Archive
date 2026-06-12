---
title: "wierd installation conflicts"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by jherskow on 2009-07-30
many programs canntot isnstall via add remove OR synaptic.

error messages list other programs (different ones every time) and say they must be installed as well.
i tried to insall these once or twice and recived a similar message with more programs in it

attached is an example of one such error message.

please help,

jherskow

---

### Post by oldos2er on 2009-07-30
Do you have all repositories enabled?

---

### Post by merlinus on 2009-07-30
Try this:

```
sudo apt-get update
```or choose Edit/Reload Package Information in synaptic.

Also look in Settings/Repositories and make sure the appropriate boxes are ticked.

---

### Post by jherskow on 2009-07-30
im not sure what you mean by "all repositories" i have all the default ones enabled. i also installed a bunch with ubuntu tweak, but it was giving me all sorts of problems so i removed it andt the repositories.

btw, im also running the earlier kernel bcz the recent one messd up all of the graphics.

ill try the update thing in a second.

---

### Post by jherskow on 2009-07-31
ok, i updated, and no update thingies were available_ so no help

im fairly sure all the right boxes are ticked

reloaded all package info- still the same problem

it always lists a dependencie, which lists  its own dependencies.....and so on

can this be because of the older kernel?

---

