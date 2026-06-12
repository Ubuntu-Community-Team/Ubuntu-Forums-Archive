---
title: "bash: deb: command not found"
date: 2008-11-06
forum: General Help
---

### Post by tostrye on 2008-11-06
I am trying to install cinelerra. I use the tutorial on [http://cinelerra.org/getting_cinelerra.php#gutsy](http://cinelerra.org/getting_cinelerra.php#gutsy) (I use gutsy). Everything works ok until I try to do 'deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy main'
Here is what I get:
> leroy@leroy-desktop:~$ deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy main
bash: deb: command not found
:lolflag:

---

### Post by ju2wheels on 2008-11-06
You dont add that line in the command line, well you can but not that way.

Open System->Administration-> Software Sources-> Third Party Software Tab-> Add Button. And paste that deb line in there.

---

### Post by the yawner on 2008-11-06
Uhh... The commands described as quoted below already give the instructions to get the repository for this software.
> 
Installation notes:
- To add this repository in your sources list use the following terminal command:
*sudo wget [http://akirad.cinelerra.org/dists/gutsy.list](http://akirad.cinelerra.org/dists/gutsy.list) -O /etc/apt/sources.list.d/akirad.list*
- Installations from this repository need an authentication key. Add it by typing in your terminal the following command:
*wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update*


But ju2wheels' suggestion should work too.

---

### Post by tostrye on 2008-11-06
I tried that before too I think, and when I try 'sudo apt-get install cinelerra' I get 
The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not installable or
                      cinelerrahv but it is not installable
E: Broken packages

And synaptic says 
cinelerra:
 Depends: cinelerracv  but it is not installable or
 	cinelerrahv  but it is not installable

---

### Post by oldos2er on 2008-11-06
Did you run "sudo apt-get update"?

---

### Post by tostrye on 2008-11-06
the instructions tell me to run:
*wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update*

I did that

---

### Post by xak on 2008-11-06
> **tostrye said:**
> the instructions tell me to run:
*wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update*

Right, that steps adds their repository to your local list of repositories.

Then, you must update your local list of packages from your local list of repositories with:
**sudo aptitude update**

Then, you can install the package with:
**sudo aptitude install cinelerra**.

---

### Post by tostrye on 2008-11-06
I tried *sudo aptitude update* and it worked, But when I did *sudo aptitude install cinelerra* i got:
> Get:1 [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release.gpg [197B]
Ign [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Translation-en_US
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Packages
Fetched 1B in 0s (2B/s)
Reading package lists... Done
leroy@leroy-desktop:~$ sudo aptitude install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  cinelerra 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1180B of archives. After unpacking 4096B will be used.
The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv which is a virtual package. or
                      cinelerrahv which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.


---

