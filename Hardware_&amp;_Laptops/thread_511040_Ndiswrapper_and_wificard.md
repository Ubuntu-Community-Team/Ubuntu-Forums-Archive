---
title: "Ndiswrapper and wificard"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by MikeMM on 2007-07-27
I'm not sure if this is the right forum but I installed t he deb packages for ndiswrapper... It installed fine.. Just one issue.. If I try to install drivers via the GUI they just dont install... or even do anything.. so I've been installing them via the terminal using the following:

ndiswrapper -i net8185.inf
ndiswrapper -l (for verification)
ndiswrapper -m

Now, the problem comes when I try to load the module

modprobe ndiswrapper (I would do this from the root account)
and then i would get an error something like 
FATAL: Module not found... or something along those lines.

I was wondering if anyone knew what i was doing wrong..
Because the driver installs... The device is recognized but it wont load the module.

Please and thanks 
Mike

---

### Post by fredj on 2007-07-28
Open a terminal and type sudo ndiswrapper -v. This displays the version of ndiswrapper utils and the
required version of ndiswrapper utils. If the two don't match then you have the defective version of
ndiswrapper from the feisty repositories and it will only work if you are really lucky.
The only way round this is to download the latest source code from the ndiswrapper website. Install the
build-essential package and compile the latest version. One of the files in the standard repository is 
the wrong file - a real pain for beginners to have to face.
Post again in the wireless and networking forum if you need help with the compilation (you will also as
part of this have to uninstall the version presently on your PC).

---

