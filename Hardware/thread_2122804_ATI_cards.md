---
title: "ATI cards"
date: 2013-03-06
forum: Hardware
---

### Post by SkeeterBum on 2013-03-06
I am starting to get headaches trying to figure this all out. 

What I want to do is get my 4 graphics cards bitcoin mining for me again but on ubuntu. I have finally managed to get ubuntu to recognize all of my cards, but now it seems I cannot get OpenCL to work/be recognized.
(System x4 5830s, Evga Z77 FTW, Intel 3570K)

So the furthest I have gotten is being able to run the command ```
sudo lspci | grep VGA
``` and get all four cards to show up, and also run ```
sudo aticonfig --adapter=all --initial
``` reboot and run ```
aticonfig --adapter=all --odgt
``` and see each card and its temprature. 


Where I am failing is with my mining software trying to use OpenCL. 
I am going by this guide [http://www.distrogeeks.com/install-cgminer-2-10-4-ubuntu/](http://www.distrogeeks.com/install-cgminer-2-10-4-ubuntu/) and I fail at step #25. I get the feedback from ```
./autogen.sh
``` 
```

Configuration Options Summary:    
curses.TUI...........: FOUND: -lncurses   
OpenCL...............: NOT FOUND. GPU mining disabled.

```


Here is some other advice I have gotten [https://bitcointalk.org/index.php?topic=149528.0](https://bitcointalk.org/index.php?topic=149528.0); 

The best they can tell me is 
> 
There will be a mismatch between the AMD.APP\bin\x86\opencl.dll and the  syswow64\opencl.dll. Cgminer will crash, unless you have precompiled  kernels (*.bin) files that are compatible in the folder. By copying the  AMD.APP dll's (amdocl64.dll/amdocl.dll and opencl.dll) to system32 and  syswow64 it will work. Remember to take ownership of the file, then  change the filerights (as Windows protects those files by default).

But that is for windows. (original article for the quoted info [http://devgurus.amd.com/thread/160032](http://devgurus.amd.com/thread/160032) )

I was also told go here [https://bitcointalk.org/index.php?topic=78229.0](https://bitcointalk.org/index.php?topic=78229.0)
> 
Never mind it's gotten much easier now.

In case anyone is wondering...

Install Restricted AMD drivers from repos 
Download [http://developer.amd.com/Downloads/AMD-APP-SDK-v2.6-lnx64.tgz](http://developer.amd.com/Downloads/AMD-APP-SDK-v2.6-lnx64.tgz)
cd to where you saved it
sudo ./Install-AMD-APP.sh
Reboot
sudo apt-get install python-pyopencl

Then download your mining software of choice and you're good to go.

But I really doubt it is that easy.... 



So. Can anyone help?

How can I tell which version of AMD-APP-SDK I have? How can I tell if I have OpenCL downloaded, installed, and enabled?

---

### Post by superdaveozzborn on 2013-03-29
Perhaps this may help, [http://www.distrogeeks.com/?p=7105](http://www.distrogeeks.com/?p=7105)

A walk threw for installing cgminer with AMD/ATI video cards.
it apears that you may not have coppyied the ADL_SDK files to the correct folder before configuring cgminer source

this will also install  the latest cgminer release. and later if you wish to upgrade to newer version simple start at step 19.

Hope it helps.

---

