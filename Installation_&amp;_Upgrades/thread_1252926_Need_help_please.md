---
title: "Need help please"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by xdweaver on 2009-08-29
HELP.. i installed ubuntu studio 9.04. Everything went well but when i tried To enable the Medibuntu repository i keep getting this error.

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
E: Type '[...]' is not known on line 1 in source list /etc/apt/sources.list
E: Type '[...]' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type '[...]' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type '[...]' is not known on line 1 in source list /etc/apt/sources.list
E: Couldn't read list of package sources

Any help to a newbe would be great. thank you

---

### Post by Moop on 2009-08-29
That command is just trying to add the keyring for medibuntu. Did you add the repository to your sources list first? 

I always use the command that's listed first under adding the repositories on the medibuntu site. It adds the repository to sources, installs the keyring and updates, all in one command.

---

### Post by linux_tech on 2009-08-29
For 9.04, this may help-
```

sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by xdweaver on 2009-08-29
Thank you for the help and your time. I am wondering if you could show me how that command that you use... lol I am thinking i bit a little more than i can chew.. Guess this is a good way to learn.

---

### Post by Moop on 2009-08-29
Click on Applications, then Accessories and choose terminal. You can copy and paste the commands into terminal, one command at a time.

---

