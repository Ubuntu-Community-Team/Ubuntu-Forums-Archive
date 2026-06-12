---
title: "Update errors after installing brother printer driver"
date: 2008-09-04
forum: General Help
---

### Post by AgentZ86 on 2008-09-04
Hi all

I've installed the printer drivers from the brother solutions site, and the scanner works great, but the printer is not working.
No problems really since I only want the scanner anyhow.

But now the updates give me errors with the follow messages:

Came up on the popup screen:

E: cupswrapperdcp7020: subprocess post-installation script returned error exit status 1

But in the details window I get this:
Details shows this:

(Reading database ... 134929 files and directories currently installed.)
Preparing to replace libtiff4 3.8.2-7ubuntu3 (using .../libtiff4_3.8.2-7ubuntu3.1_i386.deb) ...
Unpacking replacement libtiff4 ...
Preparing to replace libtiff-tools 3.8.2-7ubuntu3 (using .../libtiff-tools_3.8.2-7ubuntu3.1_i386.deb) ...
Unpacking replacement libtiff-tools ...
Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libtiff4 (3.8.2-7ubuntu3.1) ...

Setting up libtiff-tools (3.8.2-7ubuntu3.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupswrapperdcp7020
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperdcp7020

It would appear a problem with the cupswrapperdcp7020 that I installed

I didn't really do anything other then click on the links on the brothersolutions site, they have changed their site to be easier to navigate.
Anyhow, How can I uninstall the printer drivers and get back to normal ?
Or fix them so my updates don't give me errors

Please advise
Thanks

---

### Post by plucky on 2008-09-04
Try this from a terminal one command at a time ```
sudo mkdir /usr/share/cups/model
sudo apt-get -f install
sudo apt-get update
```

The first command actually creates the non-existent directory,the second command should try to fix the install and if those work then see if the update works.

FYI: If you are on Hardy 8.04,the Brother printer drivers are packaged in Synaptic.Much easier to install


Good Luck

---

### Post by AgentZ86 on 2008-09-04
> **plucky said:**
> Try this from a terminal one command at a time ```
sudo mkdir /usr/share/cups/model
sudo apt-get -f install
sudo apt-get update
```

The first command actually creates the non-existent directory,the second command should try to fix the install and if those work then see if the update works.

FYI: If you are on Hardy 8.04,the Brother printer drivers are packaged in Synaptic.Much easier to install


Good Luck

Thanks, I did figure that out about synaptic after I was getting annoyed with the update errors.

I went into synaptic did a search for 7020 and saw the packages that I previously installed along with the ubuntu packages for my printer.

I uninstalled the old and installed the new then printed a test page.

It could not be any easier then that.
Bye the way this printer was given to me by my bro, who had a small roller fall off of it on the ADF, but I must say I wish I could find a roller for it because it's a super fast scanner I was really suprised.

And XSane does multiple page document scanning very nice with this scanner.
Anyhow thanks for the help this is great info.

---

