---
title: "New User - A Couple of Installation Problems"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by blipscomb on 2009-03-11
I'm new to Ubuntu and am trying out the 8.10 64 bit version. My hardware is an ASUS M2N-LR mobo, AMD Opteron 1218 processor, ATI Fire gl v5200 graphics, 6 GB ram (2x2GB ocz and 2x1GB mushkin), and a single Western Digital 500 GB ATA HD. I first tried to install from a live cd and got the following whenever I tried to do anything (check the cd, boot from the live cd, or install):

[IMG]http://picasaweb.google.com/lh/photo/_F9CVLhOBHiHfE0ZohaUTg?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink[/IMG]

direct link: [http://picasaweb.google.com/lh/photo/_F9CVLhOBHiHfE0ZohaUTg?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink]("http://picasaweb.google.com/lh/photo/_F9CVLhOBHiHfE0ZohaUTg?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink")

I thought I might resolve the issue and continue with the installation by removing my 2x2GB ocz. When I did this the errors dealing with memory went away but the other errors remained when I typed exit in the shell. Of note is that when I type exit again It said it "could not open /root/dev/console no such file", then "Kernel panic - not syncing: attempting to kill init!" The same thing happened with three different live cds. The first was burned on my work comp with 8x write speed, the second and third were burned on my personal comp with 4x and 1x write speed. I checked the md5 hash for both isos. 

After getting frustrated by the live cd method I decided to install from within windows using wubi. Everything seemed to go alright and upon reboot I got the following:

[IMG]http://picasaweb.google.com/lh/photo/9xR5ayyXtlE-Iy2V-AqnJw?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink[/IMG]

direct link: [http://picasaweb.google.com/lh/photo/9xR5ayyXtlE-Iy2V-AqnJw?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink]("http://picasaweb.google.com/lh/photo/9xR5ayyXtlE-Iy2V-AqnJw?authkey=Gv1sRgCIHA5O6U8ZnsggE&feat=directlink")

I typed exit and ubuntu booted up and here I sit typing in this forum trying to figure out what's going on. I don't really care about the memory problem right now and that can be addressed at a later date since I don't really need all 6 gigs anyway. Ideally I'd like to avoid the wubi installation and just use the live cd.

---

### Post by Neo_The_User on 2009-03-11
Verify the md5sum of the CD and the downloaded iso image and compare to the one in the server that you downloaded.

---

