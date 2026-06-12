---
title: "Dell Dimension 8200 / HP Officejet 6500 problems"
date: 2009-11-01
forum: Hardware
---

### Post by StephenOK on 2009-11-01
Hi,

I've recently installed Ubuntu 9.10 on a Dell Dimension 8200 and I'm having 
a problem configuring the HP Officejet printer.

I entered the appropriate commands in terminal to begin the installation process after downloading the hplip package from the appropriate site.
However, shortly after the installation began and I answered some installation related questions, I was told that certain dependencies were missing and needed to be installed.

Here they are in the order presented on the installation log:

warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

I entered synaptic manager and searched for the appropriate gcc - GNU Project C and C++ Compiler. Turns out that the C compiler is already installed on the machine, and I can't find the C++ compiler in synaptic.

This is a multi-function Printer: Printer, Fax, Scanner. I'm curious to see how I can resolve this issue and get the printer - with all of its features - up and running.


Thanks in advance for any assistance,


Stephen

---

### Post by StephenOK on 2009-11-01
Is this a 9.10 issue? Possibly the gcc 'drivers' aren't prepared for the updated distro yet.

Any ideas?

---

### Post by StephenOK on 2009-11-01
I forgot to mention that I found gcc GNU objective C/C++ compilers, but that's significantly different than C and C++. I'm really at a loss here and
don't know what to do.

---

### Post by StephenOK on 2009-11-03
Can anyone offer any advice concerning this issue? I'm sure others have run into similar situations.

---

