---
title: "Need help with Chandler install - Hardy"
date: 2008-07-10
forum: General Help
---

### Post by John Azelvandre on 2008-07-10
Hello,

Today I read about the Chandler PIM, looked over their website and was eager to give it a try.  However, installing on my Hardy box is apparently not as straightforward as their download page would lead one to believe.

When I follow their instructions for installing a deb package, I get dependency errors and a broken package.

Their instructions are as follows:

> Debian Package (*.deb)

Note: This binary is built for Ubuntu 7.10, aka Gutsy Gibbon. Other platforms may have to build from source.

Download Chandler_linux_0.7.7-1_i386.deb and save it to disk.

Select the downloaded file in your file manager of choice and double-click on it. In Ubuntu this will start the Package Installer and you can follow it's prompts to install

Or you can install it manually:

Change your shell's current directory to the location you saved the file and unpack the distribution via:

   sudo dpkg -i Chandler_linux_0.7.7-1_i386.deb

This will install Chandler. If you do not want to use sudo and wish to install it locally:

   dpkg -i Chandler_linux_0.7.7-1_i386.deb --instdir=path/

Run Chandler:

   chandler

I tried both using the package manager that is invoked from the Firefox download utility, and also the dpkg method.  The first failed with a "wrong architecture" warning, while dpkg spat out unmet dependency errors and left the package broken and unconfigured.  Kind of weird, because I thought the whole point of Debian package manager was to automatically seek out and install the needed dependencies.

Anyway, if anyone has actually installed this on Hardy Heron, hit me back.  Not much to go by on the Chandler website.

---

### Post by John Azelvandre on 2008-07-10
Follow-up:

I was able to download and run chandler using the the tarball:

(their tarball instructions:)

> 
Compressed Image (*.tar.gz)

Note: This binary is built for Ubuntu 6.06 LTS, aka Dapper Drake. Other platforms may have to build from source.

Download Chandler_linux_0.7.7.tar.gz to a directory on your computer. Change your shell's current directory to the directory you copied the file to, and unpack the distribution by typing the following:

   tar zxf Chandler_linux_0.7.7.tar.gz

This will create a Chandler_linux_0.7.7 subdirectory. Cd into that directory:

   cd Chandler_linux_0.7.7

Run Chandler:

   ./chandler

So I've got something to play around with.  I would have preferred to install it the Debian way, but perhaps this is ok for now?

---

### Post by fowie on 2008-07-10
A "wrong architecture" error probably means you're not using the i386 kernel.  Do you have a dual-core or 64-bit system?  If you type uname -a into a console it should show you the kernel name and it will say something like _generic, _i386, _x64, etc... and that probably won't match with the _i386 of that .deb package.  Find the package that matches your architecture.  Otherwise just keep the program version you compiled from source.

---

### Post by John Azelvandre on 2008-07-10
Interesting.  I use the "generic" kernel, because the i386 kernel causes major problems on my machine.  (I always presumed my system was 386, but uname claims it's 686 -- I'm pretty much underwater when it comes to these kernel distinctions).

Odd that this won't run on a pretty ordinary Hardy Heron box, since they built it on Gutsy. 

There is no package for Chandler that I know of made for the "generic" flavor.  Their download page is pretty minimal.  (see [http://downloads.osafoundation.org/chandler/releases/0.7.7/#enduserlinux]("http://downloads.osafoundation.org/chandler/releases/0.7.7/#enduserlinux")) 
 
The only other option is the tarball.  That runs.  Haven't had a chance to really play with it, however.

I didn't compile anything from source, unless that is what unpacking a tarball does, which I doubt.  But I'm only a part-time linux geek, so what do I know .... :)

---

