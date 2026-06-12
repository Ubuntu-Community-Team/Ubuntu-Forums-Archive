---
title: "Probelm installing drivers of Modem"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Mutant Human on 2005-05-16
Hi 

i have got 3 versions of drivers for my conexant HSf 56k modem.
.rpm
.deb
.tar.gz
i have tried installing all of them but i get this error in the terminal window
Reading Package.....which is followed by

the kernel should be updated & a C compiler should be installed

Please tell me Step By Step what to do...

Thanks

---

### Post by wwwolf on 2005-05-17
[QUOTE=Mutant Human]Hi 

i have got 3 versions of drivers for my conexant HSf 56k modem.
.rpm
.deb
.tar.gz
i have tried installing all of them but i get this error in the terminal window
Reading Package.....which is followed by

the kernel should be updated & a C compiler should be installed

Please tell me Step By Step what to do...

Thanks[/QUOTE]

1. Install the package gcc from the installation CD with kynaptic/synaptic.

2. What kernel version do you have now? type ' uname -r ' to find out.

3a.   do ' sudo dpkg -i name-of-debian-package.deb' to install your modem drivers. If that is the only .deb file in the directory you can instead do 'sudo dpkg -i *.deb' to install it. Don't do this unless you have to. It is better to compile from source.

3b.   So instead, expand the tar.gz file by 'tar -xvzf *.tar.gz' then enter the newly created directory with the same name except for the tar.gz part. There should be some file in there called README, or Install, or something. Read that file and it will give you step-by-step instructions on what to do.

HTH,

keep posting questions if your still confused.

---

### Post by az on 2005-05-17
Install build-essential and linux-headers-386 (assuming that you are using the stock kernel.  You probably are)

Install the deb as mentioned above and it should find the headers and compile the driver automatically.

---

