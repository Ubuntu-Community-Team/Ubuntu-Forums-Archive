---
title: "GF3 Drivers problem"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by AxelW on 2005-06-23
I have recently installed Unbuntu on my computer and overall has it been a positive experience but I have some problems with installing new drivers for my GeForce 3 Ti 200.

When I'm about to install the drivers the following text appears:

"No precomplied kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site"

I have then the posibility to chose between "Yes" or "No". Since "Yes" seems to be the only way to go I picked it only to be met by this message.

"No matching precomplied kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel"

I pressed "OK" and the following text appeared:

"ERROR: unable to find the development tool 'cc' in your path; please make sure that you have the package 'gcc' installed on your system, then please check that 'cc' is in your PATH"

I bet you get questions like this quite often and might be a bit tired of answering them but it would be of great help if you just helped me solving this problem.

Ubuntu 5.04
GF 3 Ti200
NVIDIA-Linux-x86-1.0-7664-pkg1

EDIT: I was able to solve the problem, obviously it wasn't that difficult that I thought it was. But now have another problem arose. After I was able to install 'gcc' and run the driver again this problem occured:

"Error: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel; on Red Hat Linux, for example, be sure you have the 'kernel -source' rpm installed. if you know the correct kernel source files are installed, you may specify the kernel source path with the ' -kernel -source -path' commandline option'"

EDIT: Problem solved

---

