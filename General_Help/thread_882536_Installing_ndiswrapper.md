---
title: "Installing ndiswrapper"
date: 2008-08-07
forum: General Help
---

### Post by smallsea on 2008-08-07
I'm running Ubuntu Hardy and I'm a bit slow witted. I've unzipped ndiswrapper-1.53 and read the following in the INSTALL file:

"You need a recent kernel, at least 2.6.16, with header files for the
kernel. Make sure there is a link to the kernel source from the modules
directory. The command
  ls /lib/modules/`uname -r`/build
should have at least 'include' directory and '.config' file."

Problem is I don't have either 'include' directory or '.config' file.

brian@brian-laptop:/lib/modules$ ls 
returns
2.6.22-14-generic  2.6.22-15-generic  2.6.24-19-generic

Is this the link they speak of?
What can I do?

---

### Post by cariboo on 2008-08-07
You don't need  to compile ndiswrapper as it is on the live cd. Mount your livecd, just stick it in the drive, right click and open. Navigate to pool/main/n. You will find ndiswrapper-utils, ndiswrapper common and the gui file ndisgtk. Just double click ndiswrapper-utils, and gdebi will open and install ndiswrapper for you, once this is done navigate to the ndisgtk folder and install the gui, it will make things a lot easier

Jim

---

### Post by caljohnsmith on 2008-08-07
Smallsea, another option is to just install that "ndisgtk" program using Synaptic Package Manager.

---

### Post by Guy_AD on 2009-04-10
Try:

sudo apt-get install linux-headers

If that doesn't work, add an asterisk to the end.

If I remember correctly, when you were my teacher you had some issues with compiling. I suspect your headers and libraries are to blame.

sudo apt-get install build-essentials

---

