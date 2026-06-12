---
title: "Problems with Ubuntu on VMWARE"
date: 2008-09-09
forum: General Help
---

### Post by kostakizz on 2008-09-09
Hello guys, i have a prob.

I installed vmware a while ago all is fine working and i decided to install ubuntu on it.

So i had it all done. I open terminal and tried to install nmap

so i wrote "sudo apt-get install nmap"

and see what happened:

[http://img353.imageshack.us/my.php?image=asdtn8.png](http://img353.imageshack.us/my.php?image=asdtn8.png)

Any help?

---

### Post by Rocket2DMn on 2008-09-09
Did you run apt-get update yet?  It has to download the package list from the repositories first.
```
sudo apt-get update
sudo apt-get install nmap
```
You may need to check your choice of mirrors from System->Administration->Software Sources.

nmap is in the Main repository.

---

### Post by bodhi.zazen on 2008-09-09
LOL

My guess is you need to enable your repositories :

[uhelp]community/Repositories/Ubuntu[/uhelp]

Then ```
sudo apt-get update && sudo apt-get install nmap
```

---

