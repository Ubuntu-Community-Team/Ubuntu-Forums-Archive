---
title: "How to get back to Ubuntu ?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by knguyen144 on 2009-02-04
I "made" a mistake to switch from Ubuntu 8.04 to Kubuntu 8.10 due to all hypes about KDE 4.x ...
Kubuntu 8.10 installation is OK, I have no problem. However, I ran into a main problem is I am working on SystemC Verification tool which was working fine on Ubuntu 8.04. 

When I switched to Kubuntu, I can't reinstall the SystemC, eventhough the software package have not changed. 
In Ubuntu 8.04, I used GNU 4.2 Compiler, in Kubuntu the GNU 4.3 was installed. The GNU 4.3 compiler find something mismatches such as:

-----------------------------------------------------------------
ktnguyen@ubuntuk:~/systemc-2.2.0/objdir$ ../configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/ktnguyen/systemc-2.2.0/config/missing: Unknown `--run' option
Try `/home/ktnguyen/systemc-2.2.0/config/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
....

Making all in utils
make[4]: Entering directory `/home/ktnguyen/systemc-2.2.0/objdir/src/sysc/utils'
g++ -I. -I. -I../../../../src/sysc/utils -I../../../../src    -Wall
-DSC_INCLUDE_FX -g -c -o sc_utils_ids.o `test -f
'../../../../src/sysc/utils/sc_utils_ids.cpp' || echo
'../../../../src/sysc/utils/'`../../../../src/sysc/utils/sc_utils_ids.cpp
../../../../src/sysc/utils/sc_utils_ids.cpp: In function 'int
sc_core::initialize()':
../../../../src/sysc/utils/sc_utils_ids.cpp:110: error: 'getenv' is
not a member of 'std'
../../../../src/sysc/utils/sc_utils_ids.cpp:111: error: 'strcmp' was
not declared in this scope
../../../../src/sysc/utils/sc_utils_ids.cpp: At global scope:
../../../../src/sysc/utils/sc_utils_ids.cpp:119: warning:
'sc_core::forty_two' defined but not used
make[4]: *** [sc_utils_ids.o] Error 1
make[4]: Leaving directory `/home/ktnguyen/systemc-2.2.0/objdir/src/sysc/utils'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ktnguyen/systemc-2.2.0/objdir/src/sysc'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ktnguyen/systemc-2.2.0/objdir/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ktnguyen/systemc-2.2.0/objdir'
make: *** [debug] Error 2
-----------------------------------------------------------------

The SystemC source files were not changed since 6/2008 from Open SystemC Initiative (OCSI).
I was thinking about to reinstall Ubuntu 8.04, but the installation won't allow me to install over the Kubuntu 8.10 volume.
I am so scare of the repartition during my first attempt to reinstall Ubuntu 8.04: it asked me to use the whole harddisk which I am dual-booted with WindowXP. I am looking for alternative choice to install over the Kubuntu logical volume. 
I can't afford to loose the Window data, back-up the Window is not a choice. I can't take that risk.

I need both OSs alive for my work.

Please help.

---

### Post by Pumalite on 2009-02-04
Install; go 'Manual' and pick the Kubuntu partition(s), assign mount point '/' and /home if you have it in kubuntu; then follow with the installation. You can ignore /swap.
Remember to save data and backup everything first.

---

### Post by knguyen144 on 2009-02-04
> **Pumalite said:**
> Install; go 'Manual' and pick the Kubuntu partition(s), assign mount point '/' and /home if you have it in kubuntu; then follow with the installation. You can ignore /swap.
Remember to save data and backup everything first.

That is what I am looking for, I got to that point, but I did not know what to do next ... 

Let me ask a little more in details:
I must assign mount BOTH points "/" and "/home" so I won't face the rejection: "no system root available" or something like that to save the setup before move on the installation ?

Thank.

---

### Post by Pumalite on 2009-02-04
One partition with mount point '/' will do it.

---

