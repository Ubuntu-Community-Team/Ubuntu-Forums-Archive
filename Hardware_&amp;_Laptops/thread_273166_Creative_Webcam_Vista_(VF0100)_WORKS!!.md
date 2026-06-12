---
title: "Creative Webcam Vista (VF0100) WORKS!!"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by jahagir on 2006-10-07
Dear All,
After compiling/loading the driver from Michel Xhaard ([http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) ), I am able to use my Creative Webcam Vista Plus/Pro (product id: VF0100, Vendor ID: x041e Device ID: x4029)  on my Dapper Drake (2.6.15.x) installation.

The driver has been recently updated (26th Sept.) and supports a wide range of webcams, specifically for post 2.6.11 kernels. 

This webcam WAS the only piece of hardware that worked in Windows and I couldn't get it to work on Dapper

-- Jaha

---

### Post by oldnat on 2007-09-04
Hi, the link does not exist (any more?).

Could you send me the tarball or a new link?

Thanks

Nathalie

---

### Post by oscarand on 2008-01-06
Hi. I also searched for modules to load to use Creative Webcam Vista. Since a problem with ov511 module, you need to use ov51x-jpeg module. I don't remember the link to website (try to search Ov51xJpegHackedInstall on the web), so I copy instructions below.
==============================================================
Ov51xJpegHackedInstall
From Ov51x JPEG hacked Wiki
Jump to: navigation, search
Contents
[hide] [hide]

    * 1 Preliminaries
    * 2 Compilation and installation
    * 3 Force a parameter at load
    * 4 Install debian module package
    * 5 Installation on OpenSuse 10.x
    * 6 Upgrading from oldest releases


Warning: These are installation instructions for 1.0.0 release. See FAQ for differences with 0.5.x releases
Preliminaries

The module ov511 shipped with default kernel for ov511/ov518 webcams is broken. When you plug your camera, the kernel may load it in first place so the ov51x-jpeg cannot be used later on.

You may unload the module:

rmmod ov511

and then remove the module from /lib/modules/`uname -r`
Compilation and installation

First, you must have a working kernel module build and the videodev module compiled. In most distributions, this you may need some kernel headers corresponding to your kernel. See the command uname -r to get your kernel version.

Basically, you need a kernel with its headers, and the videodev module built with video4linux option (try modprobe videodev as root).

Then, as normal user, type in the ov51x-jpeg-x.x.x directory:

% make

and, as root:

# make install
# modprobe ov51x-jpeg

or if this fails for any reason:

# modprobe videodev
# insmod ./ov51x-jpeg.ko

from the source directory. the 'videodev module may already be loaded.

That's it, you got your camera ready to work with your favorite v4l application!
Force a parameter at load

It can be usefull to force the use of a parameter when the module is loaded, as with the kopete issue.

A clean way to do so is to add this as an option in the file /etc/modprobe.d/options. Simply apend a line of that form to this file:

options ov51x-jpeg force_palette=13


Install debian module package

First, see Ov51xJpegHackedSource for how to add the correct sources to your sources.list

A quick way to build the module is to issue those commands, prefixed by sudo if you are in Ubuntu:

apt-get update
apt-get install ov51x-jpeg-source module-assistant
module-assistant a-i ov51x-jpeg 

If this fails first try the same with -t to look at log:

module-assistant -t a-i ov51x-jpeg 

And then read more documentation on module-assistant.

If then you still think it comes from the package, please mail the issue to [email]ov51x-jpeg@rastageeks.org[/email]

If everything worked so far, then you have a working module installed... You may simply unplug/plug the webcam, or modprobe ov51x-jpeg to see it working !
Installation on OpenSuse 10.x

Install package "kernel-source", "linux-kernel-headers" and "usbvision-kmp-bigsmp" and "usbvision-kmp-default". usbvision is a Linux device driver for video grabbing with USB-onöly connected "webcam" devices.

Then proceed with section "compilation and installation", i.e. uncompress as normal user files in the ov51x-jpeg-x.x.x directory and change directory and replace x.x.x by version number:


% cd /.../path2mydir/ov51x-jpeg-x.x.x
% make

and, as root:

# make install
# modprobe ov51x-jpeg

Finished.
Upgrading from oldest releases

If you are updating from 0.5.x releases, you have to remove first the remaining modules. A quick and dirty command would be:

# find /lib/modules/`uname -r` -name "ov51x.ko" -exec rm -f {} \;

You may also remove loaded module using lsmod and rmmod
Retrieved from "http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall"

---

