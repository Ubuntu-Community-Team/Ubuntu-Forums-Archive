---
title: "6 months w/o updates"
date: 2008-11-16
forum: General Help
---

### Post by carl.alv on 2008-11-16
Hi all! I have ubuntu hardy installed and theres been more than six months since the update manager updated something (just updated acroread and thats all). Is this normal? because i remember that there used to be updates almost every day.

---

### Post by bapoumba on 2008-11-16
No it is not normal.
Please post the output of:
```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by Melindrea on 2008-11-16
have you checked System -> Administration -> Update Manager, and press Check to see if there's new updates? Since I do seem to recall there having been updates the last six months. =) I had the problem before reinstalling my laptop that there was some problem where it wouldn't automatically connect.

---

### Post by carl.alv on 2008-11-16
> **Melindrea said:**
> have you checked System -> Administration -> Update Manager, and press Check to see if there's new updates? Since I do seem to recall there having been updates the last six months. =) I had the problem before reinstalling my laptop that there was some problem where it wouldn't automatically connect.

Yup I have done that, but nothing.

---

### Post by carl.alv on 2008-11-16
> **bapoumba said:**
> No it is not normal.
Please post the output of:
```
cat /etc/apt/sources.list
sudo apt-get update
```

For cat
```
## Uncomment the following two lines to fetch updated software from the network

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.





# deb http://archive.canonical.com/ubuntu feisty-commercial main

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt edgy main


#AUTOMATIX REPOS END
# deb http://packages.dfreer.org feisty main
# deb http://packages.dfreer.org feisty main
# deb http://blognux.free.fr/debian unstable main
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
# deb http://packages.dfreer.org feisty main
# deb http://packages.dfreer.org feisty main
deb http://rowdy.dfreer.org:8080 hardy main

```

and update
```
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US          
Hit http://rowdy.dfreer.org hardy Release.gpg                        
Ign http://rowdy.dfreer.org hardy/main Translation-en_US             
Ign http://archive.ubuntu.com hardy/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release                          
Hit http://rowdy.dfreer.org hardy Release                            
Hit http://archive.ubuntu.com hardy/main Packages                  
Hit http://rowdy.dfreer.org hardy/main Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Reading package lists... Done       
```

---

### Post by bapoumba on 2008-11-16
You do not have the update repos enabled. You can add the repos from synaptic > settings > repositories > update tab.

Then hit the reload button, that should do it.

Or, you can replace your sources.list with this one:

```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Backports.
# deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Partner.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

## Security.
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

And reload the file with:
```
sudo apt-get update
```

---

### Post by carl.alv on 2008-11-16
Yup, it works, thanks :), but it doesn't lets me check the "important security updates" though.

---

### Post by bapoumba on 2008-11-16
> **carl.alv said:**
> Yup, it works, thanks :), but it doesn't lets me check the "important security updates" though.

What do you have in the ubuntu software tab?

---

### Post by carl.alv on 2008-11-16
hehe :p, thanks! hmm but still it wont let me :(

Now its OK, just had to restart :) tnx a bunch!

---

### Post by bapoumba on 2008-11-16
Glad you got it to work, cheers!

---

