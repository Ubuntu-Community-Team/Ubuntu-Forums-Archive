---
title: "[SOLVED] hello, i get an error when trying to use sudo apt-get"
date: 2008-07-25
forum: General Help
---

### Post by iamcims on 2008-07-25
I have an error in terminal and update manager now after adding a repository, i tired removing it and it didnt fix my error. 


This is the error.

```
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

```

One of these or both caused the problem.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 


sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Thanks for any help.

---

### Post by drs305 on 2008-07-25
Update your sources.list medibuntu repository. A new procedure was started with Hardy, so your list may not have the proper format if you followed older instructions:
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-bad

```

Install Medibuntu Repository for Hardy following the info from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by iamcims on 2008-07-25
Thank you drs305, that fixed my problem.

---

### Post by drs305 on 2008-07-25
You are welcome. Would you please mark the thread SOLVED with the 'Thread Tools' link at the top right of the original post?

---

