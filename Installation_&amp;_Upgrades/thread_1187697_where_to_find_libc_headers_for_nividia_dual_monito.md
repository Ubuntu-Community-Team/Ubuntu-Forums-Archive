---
title: "where to find libc headers for nividia dual monitor setup"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Vansch76 on 2009-06-14
Hi Everyone

Im using Ubuntu Studio 8.04
My video card is an Nvidia Geforce 9500.

I'm trying to install the Nvidia drivers for a dual monitor setup.
When I run the install program it tells me
"no pre-compliled kernal interface was found to match your kernal....
Download from Nvidia...yes/no."

a couple of other messages regarding no match to my kernal was not found and it wants to recompile my kernal. I click yes,

then it says.
"you do not appear to have the Libc header files installed on your computer. Please install your distro's Libc development package.....ok

Ive have checked the install disk for Ubuntu Studio 8.04 and the files may be there but Im not sure what I'm looking for.

I have also checked the Synaptic Package manager and it lists many files when I search for "libc" but none specifically say "Libc headers"

So my question is, where are these header files located, what directory and where do I copy them to?

Thanks in advanced
Vanessa

---

### Post by norwoods on 2009-06-17
run the following command in a terminal window:
sudo apt-get install linux-headers-`uname -r`

---

