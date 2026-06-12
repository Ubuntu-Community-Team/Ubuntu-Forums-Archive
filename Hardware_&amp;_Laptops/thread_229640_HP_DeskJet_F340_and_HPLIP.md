---
title: "HP DeskJet F340 and HPLIP"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by seanf on 2006-08-04
I've got an HP F340, which is listed as a supported device for HPLIP here...

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

It prints fine under WinXP, but I'm having no luck under Ubuntu. Ubuntu detects it as HP DeskJet F300 Series, and I'm selecting the printer that uses the hp:/... port. The printer wizard suggests the DeskJet pcl3 driver, so I select that. But when I print a test page, the job shows up in the queue for a few seconds, then disappears, and nothing prints, no activity from the printer at all.  HP Toolbox can see the printer, but lists it as 'unsupported' on the status page.

I noticed the HPLIP in Dapper is a few versions behind the stable HPLIP package, so I tried to compile and install it, but I hit a dependency problem with libcupsys2-dev. The dev package in Dapper is 1.2.0, while the binary is 1.2.2, so Synaptic won't let me install it.

Can any one give me some pointers on either a) getting the HPF340 to work with Dapper's HPLIP, or b) resolving the libcupsys2-dev dependencies so I can compile the newer HPLIP?

gracias,

Sean

---

### Post by seanf on 2006-08-19
Solved: got libcupsys2-dev from Launchpad:

[https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06](https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06)

and was able to build HPLIP from source :)

---

### Post by Nubunti on 2006-09-13
Hi,
I am new to Ubuntu also. I cannot get my HP Deskjet F340 all-in-one to print on Ubuntu. I have tried everything so far that I have read in the Original Buntu Book and on line. Seanf may have my solution. Could you provide me the source code you used to set up you printer?  I'd be most appreciative and would hve more fun with Ubuntu if I could print!

Thanks,
Another Nubuntu

---

### Post by towsonu2003 on 2006-09-20
nice :) thanks for the help!

---

### Post by Sef on 2006-09-20
> Could you provide me the source code you used to set up you printer? 

Read this to  [install from source and any other way.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by towsonu2003 on 2006-09-20
> **Nubunti said:**
> Hi,
Could you provide me the source code you used to set up you printer?
uhm I didn't see this part of your message. the hplip source code did not compile in Dapper ("hplip couldn't find command") so I used the deb package hplip homepage provided. here: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) get the self extracting archive installer.
I believe it won't work in edgy (did anyone try? even with qemu / vmware? - it's hard for me to get the edgy iso)

---

### Post by SinoDave on 2006-10-31
> I believe it won't work in edgy (did anyone try? even with qemu / vmware? - it's hard for me to get the edgy iso)

I'm using edgy (actually Kubuntu 6.10 RC1) and was able to compile, but it was a huge pain. I'm very new to Linux and learning as I go, so all of this stuff is a little over my head. In the end I was able to compile the hplip Debian package that I got from Sourceforge after activating the Universe and Multiverse sites in my sourcelist file and running apt-get several times with different strings.

The package installer also errored out every time when I chose automatic installation and answered yes when it asked if I was using Ubuntu 6.10, but if I answered no and then proceeded to select Ubuntu 6.10 from the menu, it compiled. Don't ask me why this is, but it worked!

I still can't print though. I've got a Deskjet 380 and I'm trying to make it work through my XP machine using the SAMBA setup. I saw on the compatibility list (Sourceforge again) that this model of printer is not supported over a network. The most luck I've had so far is to get it to recognize the printer and send a file to the XP print manager. It always stalls there, though. The XP print manager says that it has sent 64k of however much and the printer makes some warm up noises, but nothing ever happens and I can't even cancel the print job without turning off the printer.

If anyone has any luck installing a supposedly unsupported printer over a network with an XP machine, please let me know. I could just move the printer over to the Linux machine, but I'm afraid I won't be able to use it from my XP machine.

---

### Post by 11hjpphty76lkjj on 2006-11-08
>  The package installer also errored out every time when I chose automatic installation and answered yes when it asked if I was using Ubuntu 6.10, but if I answered no and then proceeded to select Ubuntu 6.10 from the menu, it compiled. Don't ask me why this is, but it worked!

Can you run:

cat /etc/issues

and post that for me?

---

