---
title: "install drivers and kernel source"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by 1veedo on 2005-11-06
I dont get the whole headers thing.  I installed the kernel-tree and my appropriate headers but the headers never "went in" to the kernel source.  The ls looks like this

linux-headers-2.6.12-9           linux-source-2.6.12
linux-headers-2.6.12-9-amd64-k8  linux-source-2.6.12.tar.bz2
linux-patches

Ok so I have no idea what I'm doing.  I rebuilt a kernel before in fedora trying to get my mp3 player recognised.  The only thing I did there was specify modules.  Now I have an unpacked driver dir with a confusing readme and a make output of 

Makefile:135: *** Linux kernel source not found.  Stop.

The readme says> ...2.4...
---------------------------------------------------------------------------
Configure viafb options with "fbset" tool

    "fbset" is an inbox utility of Linux.

    1. Inquire current viafb information, type,
           # fbset -i

    2. Set various resolutions and refresh rates,
           # fbset <resolution-vertical_sync>
       example,
           # fbset "1024x768-75"

       Check the file "/etc/fb.modes" to find display modes available.

    3. Set the color depth,
           # fbset -depth <value>
       example,
           # fbset -depth 16

---------------------------------------------------------------------------
Building and loading viafb device driver for Linux kernel 2.6
---------------------------------------------------------------------------
Building fbcon console module.
    Step 1: Change to folder /usr/src/linux-2.6.
            # cd /usr/src/linux-2.6.
              The linux-2.6 directory depend on your kernel version, so if your kernel version is
              2.6.5-1.358, you should type "/usr/src/linux-2.6.5-1.358".
    Step 2: Configuring the kernel module
            # make menuconfig
    Step 3: Select fbcon item to module.
            -> Device Drivers->Graphics support->Console display driver support->
               <M> Framebuffer Console support
    Step 4: Save the current setting and quit.
    Step 5: Make fbcon module.
            # make modules
              Note that if no any error, this step will be produced "fbcon.ko" in 
              /usr/src/linux-2.6./drivers/video/console folder.
    Step 6: Copy fbcon.ko to lib folder.
            # cp /usr/src/linux-2.6./drivers/video/console/fbcon.ko  \
              /lib/modules/2.6./kernel/drivers/video

---------------------------------------------------------------------------
Building viafb as a module. (for Linux kernel 2.6)
    Make sure you have the kernel sources in /usr/src/linux-2.6.
    Change to the viafb directory, and then following below steps:
    
    Step 1: change to folder /usr/src/linux-2.6.
            # cd /usr/src/linux-2.6.
              The linux-2.6 directory depend on your kernel version, so if your kernel version is
              2.6.5-1.358, you should type "/usr/src/linux-2.6.5-1.358".
    Step 2: copy viafb folder in current directory.
            # cp -rf .../viafb ./
    Step 3: change to viafb directory
            # cd /viafb
    Step 4: Clear all object file.
            # make clean
    Step 5: Make source code
            # make
              Note that if no any error, this step will be produced an object file "viafb.ko".
    Step 6: Install viafb.ko framebuffer driver
            # make install

---------------------------------------------------------------------------
Using the viafb module. (for Linux kernel 2.6)
    If you want to modprobe viafb.ko into kernel and change the display mode in Linux kernel 2.6 and later versions,
    you need a framebuffer device driver(viafb.ko) and a framebuffer console module(fbcon.ko).
    Modprobing viafb will not change the display mode until you modprobe fbcon.
    You can see the related steps below.

    Step 1: Start viafb with default settings.
            # modprobe viafb
              Note that you can see the other options from "Using the viafb module. (for Linux kernel 2.4)" section.
    Step 2: Modprope fbcon.
            # modprobe fbconIt tells me to go to the source directory.  I could follow these just fine but I think it's assuming I know something I dont.  Never does it tell me to build the driver source.  I dont even go back to the unpacked directoy.  

I think I was supposed to unpack it someware special in the source tree?



Oh, also, there's a problem with transfering USB stuff.  It diserves a thread of its own but I think there might be a patch that'll fix it.  When I go to /usr/src/linux-patches/amd64/2.6.12/apply and type ./debian (the only file in there) it says  Not in kernel top level directory.  Exiting.

---

### Post by az on 2005-11-06
What driver are you tying to make?  Please include the link.

---

### Post by 1veedo on 2005-11-12
I got it.  It's not what I'd call a driver unless it was installed wrong.  I'm getting an nvidia though so it doesn;t matter.

---

