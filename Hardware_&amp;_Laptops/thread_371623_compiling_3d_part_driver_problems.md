---
title: "compiling 3d part driver problems"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by deadlinx on 2007-02-27
Hi,

_**explanation of the problem in few words**_:
compiling some drivers, the process exit with errors apperently due 
to the absence of the /lib/modules/2.6.19.2 
where 2.6.19.2 is the kernel I built.



**_"exhaustive" explanation of the problem_**:
I built my own kernel 2.6.19.2 for my Ubuntu Edgy 
following the well known Ubuntu guides,
make-kpkg --initrd --append-to-version -versione kernel_image kernel_headers modules_image and so on


The new kernel works perfectly so I begin installing
external drivers I need: I installed Nvidia driver and 
r1000 (for my Realtek 8168 Gigabit Ethernet card) without 
problems.


Finally I was going to install the ipw3545 driver 
'cause it is not included in the vanilla; 
I followed the "README" of the official project 
that can also be found on a high number of sites and blogs.
After successfully installing the new ieee stack 
I enter the ipw3945 directory and type: make
the process breaks 'cause it seems not to find the directory
/lib/modules/2.6.19.2

For the same reason I'm not able to build and use the 
support for my Hauppauge WinTV HVR900 --> processes breaks
and exit with error 2 appearently because of the absense of 
that directory. 



In these alst 13 days I was searching for a way to solve this 
problem but I'm not able to find a solution. I also rebuilt 
the kernel with the classical way 
(make bzImage, make modules, make_install and so on)
but the result is still the same :-(



Please help me 'cause at this moment the only way to use my 
wi-fi card is using the official Ubuntu kernel, but I need to 
run a custom kernel.


sincerely,

deadlinx

---

### Post by tribaal on 2007-02-28
Would this be that you don't have proper kernel header files installed?

Did you compile the kernel module for your Nvidia driver yourself?

Hope you'll find the answer

- trib'

---

### Post by deadlinx on 2007-02-28
Hi,

this creates also modules:

make-kpkg --initrd --append-to-version -versione kernel_image kernel_headers modules_image

then I installed both the linux-image and headers created as deb package this means
I have the proper kernel headers.

In the end I reboot and I installed from source r1000 driver and the Nvidia.run 
without problem.

sincerely

deadlinx

---

### Post by tribaal on 2007-02-28
Silly idea: what if you just create the empty directory?

- trib'

---

### Post by deadlinx on 2007-03-01
> **tribaal said:**
> what if you just create the empty directory?

- trib'

Hi,

just tried, no success.

sincerely,

deadlinx

---

