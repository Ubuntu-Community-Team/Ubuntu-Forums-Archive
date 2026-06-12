---
title: "Boinc+Optimus technology+Using GPU"
date: 2012-03-04
forum: Hardware
---

### Post by Palm&#279; on 2012-03-04
Hello, I have a laptop dell xps l502x with Geforce 540m. I have installed bumblebee, my Ubuntu version is 11.04. Have anyone tried running boinc client using GPU and maybe someone knows how to do so?

---

### Post by sawrubh on 2012-10-05
I am on Linux Ubuntu 12.04 64-bit and have a NVIDIA 540M having Optimus technology. I am facing the same problem and would really appreciate if someone could provide some help. I am currently using Bumblebee[1] as a temporary solution, but even that doesn't seem to be compatible with BOINC, since my BOINC client doesn't identify any GPU's in the system. This is the output of **lspci | grep VGA** :

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)

I am not installing the NVIDIA official drivers from the website, since I read somewhere that it can cause display and graphics problems when used with Gnome on Ubuntu, which I am using.

Thanks in advance.

[1] - [http://bumblebee-project.org/install.html#Ubuntu](http://bumblebee-project.org/install.html#Ubuntu)

---

### Post by pop.horea on 2013-03-31
Install bumblebee with nvidia drivers. Run: optirun ./boinc

---

