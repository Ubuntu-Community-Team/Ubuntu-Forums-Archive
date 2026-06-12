---
title: "How do i install .bin files in Ubuntu?"
date: 2008-07-27
forum: General Help
---

### Post by UK-Wobbie on 2008-07-27
Hey i like to know how to install bin files in Ubuntu.


Thanks

---

### Post by dexter.deepak on 2008-07-27
move to the directory wher you have your binary file and issue :
```
./filename.bin
```

---

### Post by Canis familiaris on 2008-07-27
You must have marked it as executable though:

```
chmod +x filename
```

Also if possible avoid installing binary files. Maybe try Synaptic or install by source.

---

### Post by UK-Wobbie on 2008-07-27
Hey,
What am having a go on doing is installing RealPlayer 11.
Have any one had any luck on this?

---

### Post by dexter.deepak on 2008-07-27
even i had installed it through binary file.
just make it executable:
```
sudo chmod a+x Real*
```
and then run it:
```
sudo ./Real*
```
you are on your way.

---

