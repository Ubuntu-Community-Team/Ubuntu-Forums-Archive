---
title: "Software Sources rendered unusable"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by graceful1 on 2009-02-21
In Administration->Software Sources, I switched from the United States server to "other". Then I clicked on the "Select Best" button. After some tests were conducted, mirror.cc.columbia.edu was selected for me. Then a dialog box appeared, saying that I must reload. I clicked OK, and now everything is greyed out in the Software Sources box and it is unusable -- cannot click on any tabs, cannot click on any check-boxes, cannot click on anything.  I am using Ubuntu 8.10.

---

### Post by x33a on 2009-02-22
see if you can run, from the terminal:
```
sudo apt-get update
```

---

### Post by graceful1 on 2009-02-22
> **x33a said:**
> see if you can run, from the terminal:
```
sudo apt-get update
```
Yes, I was able to do that.

---

### Post by emshains on 2009-02-22
The greying out is a way of showing that the gui or the whole program has crashed. You may have a bit less ram than would be needed to run it, or you had some other problems, but the app sources thingy "crashes" a lot for me too. You should rather stick to editing the sources list manually via gedit or a cli text editor. But if you ran ```
sudo apt-get update
```
then you should be good to go from now on.

---

### Post by x33a on 2009-02-22
i can't say if it's a ram issue.

to update from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

see if you are able to update. if not, then paste any error messages you get, here.

---

### Post by harrkou on 2009-03-06
I recently reinstalled ubuntu and now when i try to load a packag i receive the message 

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Maybe this has something to do with the prob our friend mentioned be4?

---

### Post by oldos2er on 2009-03-06
You can only have one package manager running at one time.

---

### Post by Vadi on 2009-03-06
> **harrkou said:**
> I recently reinstalled ubuntu and now when i try to load a packag i receive the message 

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Maybe this has something to do with the prob our friend mentioned be4?

Close other programs that might be dealing with packages such as Synaptic or Add/Remove.

---

