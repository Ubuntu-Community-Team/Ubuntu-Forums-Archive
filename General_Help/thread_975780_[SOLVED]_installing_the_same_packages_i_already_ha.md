---
title: "[SOLVED] installing the same packages i already have"
date: 2008-11-08
forum: General Help
---

### Post by Tony Flury on 2008-11-08
OK - I have Ubuntu 8.0.4 - and a whole slew of applications installed - including build essential, ajunta, wine, amsn, kopete etc etc etc.

I have also just installed 8.10 in dual boot - and i would like to try to install the same packages on 8.10.

I used this : [http://ubuntuforums.org/showpost.php?p=6115023&postcount=14](http://ubuntuforums.org/showpost.php?p=6115023&postcount=14)

but when i tried the restore bit of this in 8.10 it only got 3 packages - and did not reinstall of the above listed - or any of the many others.

so my question is - does anyone have a method with which i can capture all of the packages i have installed - and then use that list to reinstall them (or their 8.10 versions) on 8.10.

---

### Post by geirha on 2008-11-08
I haven't tried this, so I don't know how well it will work, or if it will work at all, but with
```
aptitude search ~i
``` 
you will get a list of all installed packages. Change the output format to only show the package names and put it in a file:
```
aptitude -F '%p' search ~i > packages.txt
```

Then, theoretically you should be able to install those packages on the other Ubuntu installation with 
```
sudo aptitude install $( < packages.txt )
```

---

### Post by Tony Flury on 2008-11-08
Thank you - I had to do a 
```

sudo apt-get update

```

before it would find the packages.

but this does work - or so it seems.

Thank you

---

