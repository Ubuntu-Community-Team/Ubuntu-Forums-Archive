---
title: "probs with vmware on breezy"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by maltje on 2005-10-14
I get the next error trying to install vmware.(with hoary I haven't got problems)
Your kernel was built with "gcc" version "3.4.5", while you are trying to use 
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware 
Workstation cannot work in such configuration. Please either recompile your 
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5". 

please can smoebody a good explenation what I have to do ,because I'm still a newbie.

---

### Post by zootm on 2005-10-14
Try:

sudo apt-get install gcc-3.4
export CC=gcc-3.4

Then running the installer thing again in the console you typed those commands in.

---

### Post by maltje on 2005-10-15
I did that whitout problems
Now i've got this error
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? 
Any idea's???

Maybe better that I go back to hoary?

---

### Post by diantel on 2005-10-15
Do you have headers for your kernel?

uname -r to view your kernel version

sudo apt-get install linux-headers-2.6.12-9-386

---

### Post by maltje on 2005-10-15
Your kernel was built with "gcc" version "3.3.5", while you are trying to use
"/usr/bin/gcc-3.4" version "3.4.4". This configuration is not recommended and
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc-3.4" version "3.4.4" anyway? [no] y

next error

I put back hoary on my system ,but as you see again probs.
I deleted gcc with synaptic and install as you say ,but...

---

### Post by maltje on 2005-10-15
it is ok now I saw this one
[http://www.ubuntuforums.org/showthread.php?t=65638](http://www.ubuntuforums.org/showthread.php?t=65638)

---

