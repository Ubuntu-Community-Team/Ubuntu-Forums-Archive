---
title: "How to install fjbtndrv for Fujitsu Stylistic ST5032D tablet  with Kubunut Oneiric"
date: 2012-01-28
forum: Hardware
---

### Post by lgharriman on 2012-01-28
I recently purchased a nice Fujitsu Stylistic St5032D tablet from ebay.  It did not come with an operating system so I decided to install Linux on it.  I have installed Kubuntu Oneiric with great results.   Here is the info on how to install the special button driver and screen rotation program.

1 - Go to this website:  [https://launchpad.net/~khnz/+archive/ppa/+build/2976449]("https://launchpad.net/%7Ekhnz/+archive/ppa/+build/2976449")
and scroll to the bottom and download these four files:

           fjbtndrv-2.3.2-1
           fjbtndrv-kernel-source-2.3.2-1
           fscd-2.3.2-1
           fscrotd-2.3.2-1

2 - Using Synaptic package manager:
Go to Settings > Repositories >  Other Software and add the following source files to your sources.list:

  deb [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) natty main
 deb-src [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) natty main

3 - Go to Authentication tab; click on Import Key File add the attached file **[COLOR=Black]gerlachppa.tx[/COLOR]t** 

4 - Open your file manager program (Dolphin) and go to the folder where the four files are saved.

5 - Double click on each one to install.  Your package manager program should come up and ask for the user password.  Enter that and continue installing.
 You will need to install in this order to get the dependencies installed:

fjbtndrv-kernel-source-2.3.2-1
fscrotd-2.3.2-1
fscd-2.3.2-1
fjbtndrv-2.3.2-1

  6 - Once these four programs are installed then reboot the computer.

  7 - The display should show fjbtndrv 2.3.2-1 displayed at the bottom of the screen during the desktop (final) phase of the boot up procedure.

  8 - Enjoy the added features of the buttons and screen rotation.  The screen and stylus rotates in sync, but the mouse doesn't.  The screen rotates 90 degrees left on each press of the rotate button on the tablet.

 I have also installed this on Ubuntu and it worked as well.  If you update the kernel be sure and reinstall the fjbtndrv kernel source file and fjbtndrv file.  The package manager won't allow the fscd and fscrotd files to be reinstalled, but it still works using these two files from the original install.

I have included a snapshot of the screen in portrait mode.  The bottom of the screen is facing the battery pack and name on the tablet.

---

