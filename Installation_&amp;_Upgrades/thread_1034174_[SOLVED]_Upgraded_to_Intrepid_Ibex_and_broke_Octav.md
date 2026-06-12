---
title: "[SOLVED] Upgraded to Intrepid Ibex and broke Octave"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by GreaterCore on 2009-01-08
Hi guys,

I have recently updated to Ubuntu 8.10 from Ubuntu 8.04 and I seem to have broken my copy of Octave. Currently typing "octave" alone points to an obsolete copy of Octave, while typing in "octave3.0" allows me to load up to Octave 3.0.1 but with the following error message:

error: structure has no member `archprefix'
error: evaluating argument list element number 1
error: evaluating assignment expression near line 2141, column 11
error: called from `pkg:getarchdir' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating assignment expression near line 2221, column 12
error: evaluating for command near line 2215, column 3
error: called from `pkg:load_packages_and_dependencies' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: called from `pkg:load_packages' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating switch command near line 269, column 3
error: called from `pkg' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: near line 27 of file `/usr/share/octave/3.0.1/m/startup/octaverc'

I have tried removing and reinstalling the package but this did not fix the problem.

I have tried to install the octave-forge packages and failed miserably. Now I cannot even remove them. I have installed 'octave-ad', 'octave-audio' and 'octave-gsl'.

When I try to run 'sudo apt-get -f install', I get the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up octave-ad (1.0.2-1) ...
error: structure has no member `archprefix'
error: evaluating argument list element number 1
error: evaluating assignment expression near line 2141, column 11
error: called from `pkg:getarchdir' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating assignment expression near line 2221, column 12
error: evaluating for command near line 2215, column 3
error: called from `pkg:load_packages_and_dependencies' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: called from `pkg:load_packages' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating switch command near line 269, column 3
error: called from `pkg' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: near line 27 of file `/usr/share/octave/3.0.1/m/startup/octaverc'

dpkg: error processing octave-ad (--configure):
 subprocess post-installation script returned error exit status 1
Setting up octave-audio (1.1.1-1) ...
error: structure has no member `archprefix'
error: evaluating argument list element number 1
error: evaluating assignment expression near line 2141, column 11
error: called from `pkg:getarchdir' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating assignment expression near line 2221, column 12
error: evaluating for command near line 2215, column 3
error: called from `pkg:load_packages_and_dependencies' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: called from `pkg:load_packages' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating switch command near line 269, column 3
error: called from `pkg' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: near line 27 of file `/usr/share/octave/3.0.1/m/startup/octaverc'

dpkg: error processing octave-audio (--configure):
 subprocess post-installation script returned error exit status 1
Setting up octave-gsl (1.0.6-2) ...
error: structure has no member `archprefix'
error: evaluating argument list element number 1
error: evaluating assignment expression near line 2141, column 11
error: called from `pkg:getarchdir' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating assignment expression near line 2221, column 12
error: evaluating for command near line 2215, column 3
error: called from `pkg:load_packages_and_dependencies' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: called from `pkg:load_packages' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: evaluating switch command near line 269, column 3
error: called from `pkg' in file `/usr/share/octave/3.0.1/m/pkg/pkg.m'
error: near line 27 of file `/usr/share/octave/3.0.1/m/startup/octaverc'

dpkg: error processing octave-gsl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 octave-ad
 octave-audio
 octave-gsl
E: Sub-process /usr/bin/dpkg returned an error code (1)

I would really like to have it fixed, but the solutions on the online forums have eluded me so far. I tried running 'pkg rebuild' from within Octave and it did not work.

Help!

---

### Post by PmDematagoda on 2009-01-08
Can you post the output of:-
```
whereis octave
```

---

### Post by GreaterCore on 2009-01-08
I have ran the command, and this is the output:

octave: /usr/bin/octave3.0 /usr/bin/octave /usr/lib/octave /usr/local/bin/octave /usr/share/octave /usr/share/man/man1/octave.1.gz

---

### Post by GreaterCore on 2009-01-08
I have managed to fix the octave-forge problem by deleting the file /usr/share/octave/octave_packages (or something similar). Delete everything inside /usr/share/octave/packages and octave-forge is fixed! Now, I am still looking into the problem of 'octave' calling up the wrong version.

---

### Post by PmDematagoda on 2009-01-08
Try obtaining and building the source and see if you can use that. Obtain the source from [here]("ftp://ftp.octave.org/pub/octave/octave-3.0.3.tar.bz2"). Extract it, open the extracted folder in a terminal and run(in the given order):-
```
mkdir ~/octave-install
./configure --prefix=/path/to/home/octave-install
make
make install
```
if you get an error, please post it in full here, if, however, the install succeeded. Try and launch the new octave binary by moving into the installation directory and executing:-
```
./octave
```

---

### Post by PmDematagoda on 2009-01-08
Try obtaining and building the source and see if you can use that. Obtain the source from [here]("ftp://ftp.octave.org/pub/octave/octave-3.0.3.tar.bz2"). Extract it, open the extracted folder in a terminal and run(in the given order):-
```
mkdir ~/octave-install
./configure --prefix=/path/to/home/octave-install
make
make install
```
if you get an error, please post it in full here, if, however, the install succeeded. Try and launch the new octave binary by moving into the installation directory and executing:-
```
./octave
```

---

### Post by PmDematagoda on 2009-01-08
> **GreaterCore said:**
> I have managed to fix the octave-forge problem by deleting the file /usr/share/octave/octave_packages (or something similar). Delete everything inside /usr/share/octave/packages and octave-forge is fixed! Now, I am still looking into the problem of 'octave' calling up the wrong version.

Good to hear. About the octave problem, perhaps you can delete the octave binary in /usr/bin and then symbolically link the octave3.0 binary to octave.

---

### Post by GreaterCore on 2009-01-08
Hi guys,

I got it fixed. I uninstalled all the Octave Packages and then deleted almost everything that has the word 'octave' in it. After doing this, reinstalling 'octave3.0' package was a snap.

As for the earlier problem, there should be a way to detect if 'octave_packages' file is obsolete and automatically replaced, and if the '/usr/shared/octave/packages' directory is not there, create it.

That would have saved me a great deal of grief.

But thanks for everything.

---

