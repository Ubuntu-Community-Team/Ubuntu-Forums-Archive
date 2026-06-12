---
title: "Patition sharing between Vista and Ubuntu problems"
date: 2008-11-17
forum: General Help
---

### Post by thurst on 2008-11-17
Hello everyone,
I just used any form of Linux yesterday by dual booting my laptop with Ubuntu.  I followed this guide:
[http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
I have a XPS M1330 and I have it so I can triple boot with the Media Direct button to play DVD's without the harddrive running.  
-I made the /home partition ext3
-I installed FS-Driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) in Vista
-I named the /home partition 'Z:' and Vista can see it but it says it needs to be formatted.  
-When I load the Partition Editor from Ubuntu it show my whole HD (250 gb) as 'unallocated  232.88 GiB'.
-When I load the Disk Manager I see 5 partitions:
[IMG]http://www.public.iastate.edu/~thurst/DM.jpg[/IMG]
I really don't want to reinstall Ubuntu or Vista or Media Direct.  Can anybody help me share a 190 GB partition between Ubuntu and Vista?
Thanks

---

### Post by ohzopants on 2008-11-18
From that screenshot I'm going to guess that you can access your Vista partition from Ubuntu without problems.  Is that correct?

From Vista have you tried this from the site's troubleshooting section:
>  I have installed the Ext2 IFS software and was able to create a drive letter for a desired volume of Linux. But when I try to access that volume I get an error message "The disk in drive X: is not formatted. Do you want to format it now?" (Of course I don't want to!) Or the content of the volume appears, but when I attempt to write something I get an error message "Access denied".

The ext2fs.sys driver did not mount that volume for some reason, or it mounted it read-only.

Please run the mountdiag diagnosis tool, which you can download here: mountdiag.exe (updated, 07-19-2008).

Please run it at the command prompt and give it the letter of the drive you want to examine, for example:
mountdiag G:
The tool will give you a hint on how to resolve the problem. (Note: The mountdiag tool reads data only; it does not attempt to modify anything.) 

---

