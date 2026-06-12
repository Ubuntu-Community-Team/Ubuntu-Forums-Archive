---
title: "Error: a problem occured when checking for the updates"
date: 2008-11-28
forum: General Help
---

### Post by ayet on 2008-11-28
theres this error on the notification area "a problem occured when checking for the updates" , and when i run it the synaptics package manager runs and quits automatically, how do you resolve this?

---

### Post by Coreigh on 2008-11-28
Open a terminal window and type
```
sudo apt-get update
```
this will update the sources list and my shed light on the problem.

Then
```
sudo apt-get -s upgrade
```
This is a "test" run (the -s switch) and it may give more information

If no errors are encountered then try a real run
```
sudo apt-get upgrade
```

Basically the code above is the manual way to do what the updater does.

---

### Post by ayet on 2008-11-29
tnks problem solved....what cuz my problem anyways?

---

