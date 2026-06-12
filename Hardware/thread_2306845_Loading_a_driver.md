---
title: "Loading a driver"
date: 2015-12-19
forum: Hardware
---

### Post by Kishor_Durve on 2015-12-19
Hello,

I have a new usb camera which I want to run on my Odroid C1+. It is an industrial camera with its own driver. Problem is, the driver needs to be compiled. When I asked the camera manufacturer he said it is necessary to build the kernel and then compile the driver. To complicate matters, the instructions he sent are for a different ARM processor since that is the one that was used by him. He has sent me a bunch of files in a folder named usb_driver. These files include .symvers, .order, .c, .ko, .mod.c, .mod.o etc. files
Is there no way a precompiled driver can be used directly without having to go through this?

Regards,
Kishor Durve

---

### Post by weatherman2 on 2015-12-19
If the kernel doesn't have a built-in driver then you will have to build one - and probably should anyway.  But you don't necessarily have to build the whole kernel, unless for some reason the driver requires a newer or different kernel than the one you are using.

Does the folder have a "makefile?"  Is there no "README" or "INFO" file in the folder?  These are usually basic documentation that tells you how to build the driver.

Typically, to build a driver, you'd do something like (maybe not exactly) this in a terminal:

(Replace "DRIVER_FOLDER" with whatever your folder is called.)

```

cd DRIVER_FOLDER
./configure
make
sudo make install

```

assuming the driver has a makefile associated with it.  The configure command would check your OS environment to make sure you have all required packages (and the right versions) already installed.  The "make" command compiles all the code.  The "make install" installs the kernel module.  It could be pretty easy and quick once you know the correct commands.

---

### Post by Kishor_Durve on 2015-12-20
Hello Weatherman2,

Thanks for your reply.
I navigated to the DRIVER_FOLDER. However, ./configure gives me error "bash: ./configure: No such file or directory". If, after this I try 'make', it gives me error "make[1]: ***No rule to make target 'modules'. Stop.".

What am i missing here?

Regards,

Kishor Durve

---

### Post by weatherman2 on 2015-12-20
Just to be clear: I didn't say those *exact* instructions would work - I said that's typically how you build a driver like that.  It varies depending on how the developers created and distributed the driver code.  Again - look for a "README" or "INFO" file of some sort in that folder to see if there is any information about how to build it.

Could be the developers have only provided a few source files without any easy way to build it.

You are welcome to do an "ls" on the driver folder and post the output here to show what's in the top level folder if you find it confusing.

---

