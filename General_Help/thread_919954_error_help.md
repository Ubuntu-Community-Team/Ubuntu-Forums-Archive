---
title: "error help"
date: 2008-09-14
forum: General Help
---

### Post by Masterhazim on 2008-09-14
I have ubuntu 8.04 lts which i installed from a cd and whenever i open synapatic package manager this come and pops up: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do i do

---

### Post by Patrick793 on 2008-09-14
Open a terminal and enter this:

```
sudo dpkg --configure -a
```

---

### Post by drs305 on 2008-09-14
> **Masterhazim said:**
> I have ubuntu 8.04 lts which i installed from a cd and whenever i open synapatic package manager this come and pops up: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do i do

Run the following command:
```

sudo dpkg --configure -a

```

Type your password, you won't see it but it will be entered.

---

### Post by Masterhazim on 2008-09-14
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

 Now it says this

---

### Post by lisati on 2008-09-14
> **Masterhazim said:**
> E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

 Now it says this

A similar problem (and a possible solution) is described [here]("http://ubuntuforums.org/showthread.php?t=919603")

---

### Post by Masterhazim on 2008-09-14
dosent help

---

### Post by drs305 on 2008-09-14
My suggestion was probably the same advice as what you were referred to. If the following is what you tried or you do this and it doesn't work, post the results of your sources.list and we will try to figure things out.

The following will repair your the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

If the above doesn't work, post the results of:
```

cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by Masterhazim on 2008-09-14
thanks

---

