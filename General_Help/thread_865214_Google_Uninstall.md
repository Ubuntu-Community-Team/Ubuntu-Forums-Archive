---
title: "Google Uninstall"
date: 2008-07-20
forum: General Help
---

### Post by metalmaniac248 on 2008-07-20
ok, 

i installed Google earth, and when i ran it i didn't have a globe and the fonts were incredibly small

so when i couldn't find a way to fix this or a way to uninstall google earth (so i could reinstall it)
i decided just to install it again

once the installer finished it ran Google earth and it was fine

but when i closed it and tried to run it again it came up with the original one (the one without a globe and really small fonts)

so what i would like to know is how to uninstall everything to do with Google earth off my machine, so i can run the installer again and then i believe i will have a working Google earth.


thanks


P.S. i am running Gusty

---

### Post by pauper on 2008-07-20
The answer is entirely depends on the way you have installed it.

---

### Post by metalmaniac248 on 2008-07-31
i used this method 

[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/")

---

### Post by Archimedes0212 on 2008-07-31
sudo apt-get remove googleearth

---

### Post by metalmaniac248 on 2008-07-31
i got this 


```

nick@nick-laptop:~$ sudo apt-get remove googleearth
[sudo] password for nick:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth
nick@nick-laptop:~$ 
nick@nick-laptop:~$ 
```

---

### Post by LowSky on 2008-07-31
sudo apt-get remove googleearth  wont because you did not install it from the repositories (ie:Medibuntu)
I'm making asumptions that nick is the user name file...
```

sudo -i
cd /home/nick/google-earth
./uninstall
```

---

### Post by pauper on 2008-07-31
> E: Couldn't find package googleearth

That's OK, because you didn't use apt in the first place and so it's not
supposed to know where this package is.

Did you choose /opt directory for installation path and /usr/local for binary?
If so, simply find those exact package locations and remove them manually via
"sudo rm -rf /path/to/package".
Note: Before you do that, check with "ls -l" if any of those packages have any
hard links and remove them as well. But be careful not to remove anything
else not associated with Google Earth.

---

### Post by metalmaniac248 on 2008-07-31
hi lowsky,

your method did not work it said that the directory does not exist 

its wierd its like theres no trace of it being on my system but it will run (not very well tho) 

:confused:

---

### Post by kystorms on 2008-09-26
> **pauper said:**
> That's OK, because you didn't use apt in the first place and so it's not
supposed to know where this package is.

Did you choose /opt directory for installation path and /usr/local for binary?
If so, simply find those exact package locations and remove them manually via
"sudo rm -rf /path/to/package".
Note: Before you do that, check with "ls -l" if any of those packages have any
hard links and remove them as well. But be careful not to remove anything
else not associated with Google Earth.

Hello

I too made the sad mistake of installing GE ( using a guide here some where that had it done via the terminal, starting with :

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install googleearth

well then it asked to be updated, I did and bingo NO EARTH. So I went in and removed it from synaptic and still have a version running. I have no doubt I did something wrong but I want to remove all of the darned things, and found it still exists in my /usr/local/bin/googleearth

can I use your code in same fashion to remove this file as well????

---

