---
title: "Gentoo to Ubuntu"
date: 2009-07-12
forum: Hardware
---

### Post by RNA-Wrangler on 2009-07-12
Now, many of you have probably used multiple distributions, including Gentoo and its needlessly alien Portage package management system (for me that is, I'm sure its perfectly understandable and easy to use for lots of people). As I've only just discovered the term "ebuild", I need help translating some instructions for a simple patch to the 2.6.30 kernel, intended to make it work with fglrx. The URL, [http://linux.com/community/blogs/ATI-Catalyst-fglrx-and-Kernels-2.6.30-2.6.29.html](http://linux.com/community/blogs/ATI-Catalyst-fglrx-and-Kernels-2.6.30-2.6.29.html), explains it quite thoroughly, but in terms that don't apply to ubuntu (unless there's a way to use Portage in ubuntu). Please note that I am quite the linux noob, having only used it for 6 months, and whining that "everyone should know that" is not helpful.

P.S. By the way, when I downloaded the most recent fglrx package, titled fglrx 9.6, (in an attempt to fix the display problem) I noticed during installation that it was in fact version 8.62. Why is this? Is it a quirk of the version numbering scheme (two separate versions) or does it have several versions within it, one of which it selects for the individual installation?

---

### Post by Ayuthia on 2009-07-12
I have not tried this, but from what I am understanding, I think that you are supposed to download the 9.6 driver and extract it.  I think that there is an option with the *.run command to extract the file by adding the --extract option at the end of the .run.  From there, you copy the patches into the extracted directory and then apply the patches.

However, I am not for sure if it is just that easy.  From what I recall, there are some additional patches that Gentoo applies (that comes with the portage update).  I don't see them in the bug report.  I am not for sure if they are needed or not.

As for the version numbers, I can't remember how they create them.  I know that there is an explanation somewhere though because I recall stumbling upon it once.

As for Portage, it is not as easy to understand when you are first starting.  If you are using Gentoo, it takes time to understand it, but once you figure it out, it is a very handy tool.

I am not for sure about how much you understand about all this.  I am guessing that you have already successfully installed the 2.6.30 kernel, but I am not for sure if you compiled it or found a .deb to install it.  If you compiled it, you most likely have the tools needed to apply the patches.  If not, you will need to install patch via Synaptic or apt-get.

---

### Post by RNA-Wrangler on 2009-07-15
Ayuthia, about compiling the kernel. What tools are required for that job? Also, once I've added the patches to the extracted .run file, what next? How do I turn it back into a .run?

By the way, I'm intrigued by your work with the HP tx2z. That's actually what this post concerns as one of these wonderful gems is giving me quite a lot of trouble.

---

### Post by Ayuthia on 2009-07-15
Here is a link on what I use to compile Ubuntu kernels:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
It gives you all you need on what to install to build along with the instructions on how to compile it.

As for ati driver, I have not done this in a while, but once you have extracted it, I think it is a matter of going to the fglrx* directory, patching it, and then running ati-installer.sh.

Hope that helps.

---

