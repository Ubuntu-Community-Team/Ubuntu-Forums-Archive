---
title: "[SOLVED] Failed to check for installed and available applications"
date: 2008-09-18
forum: General Help
---

### Post by gabe.c on 2008-09-18
hi im a newbee, i have downloaded the ubuntu 8.04. i tried to download the winehq aplication but ever since ive been having some problems which i have been trying to solve for the last few days.
when i try to enter the add/remove applications i get an error:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

when i try to go to synaptic i get an error:
E: Type '--22:14:31--' is not known on line 1 in source list /etc/apt/sources.list.d/mediabuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

does anyone have any ideas as what to do?

---

### Post by mb_webguy on 2008-09-18
I think I know what your problem is (though I still don't understand why people are having it).  Could you open the terminal and post the output of "cat /etc/apt/sources.list.d/mediabuntu.list"?

EDIT:  Scratch that.  You've somehow botched adding the Medibuntu repository.  It should be "medibuntu.list", not "mediabuntu.list", and you most definitely have an error in it at any rate.  Delete the file using the command "sudo rm /etc/apt/sources.list.d/mediabuntu.list" and try adding the repository again using [these directions]("https://help.ubuntu.com/community/Medibuntu").  Do not try to type the commands, but instead copy the commands from the web browser and paste them into the terminal using Ctrl-Shift-V.

---

### Post by whizbaby on 2008-09-18
Please post the output of
```
cat /etc/apt/sources.list.d/mediabuntu.list
```
there might be a syntax error in it.

---

### Post by gabe.c on 2008-09-18
i deleted the file and added the repository using the directions you gave me. the output i get from; cat /etc/apt/sources.list.d/medibuntu.list
is this:
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by gabe.c on 2008-09-18
hey guys thank you for your help. i managed to fix my problem. apparently there was some problem with the winehq application i downloaded, and using the command you gave me to delete the "mediabuntu" file, i deleted the winehq program, and thus ending my problem.
thanks again for your help

---

