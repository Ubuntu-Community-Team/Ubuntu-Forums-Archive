---
title: "How do I install MPlayer without an internet connection?"
date: 2008-10-14
forum: General Help
---

### Post by MentalOxide on 2008-10-14
What am I doing wrong?

I'm trying to install Mplayer manually because I don't have access to the internet other than through Internet cafes and a USB stick, but I run Ubuntu on my laptop, so I'm trying to install a tarball, and despite all the guides I'm having no success. 6 months with ubuntu and I still can't figure this out. 
And I can do without the condescending rubbish of the likes of iaculallad: ¨
¨Windoze doesn't teach their users to think, they are fond of spoon-feeding while Linux train it's users for resourcefulness and patience to learn since Linux is way too deep for a single day/week to learn.¨ 

Firstly, I do know how to think , but my speciality is human genetics, not computers. My life is dedicated to problem solving and my time is precious to me, precisely why I can´t waste hours per night trying to intepret that of computer operating systems. 
Secondly, the evolution of computing lies in its ability to allow humans to get things done quicker and easier, aka, progress. Forcing all humans to understand computer coding is backwards. The computers should be learning to understand us so that we can get things done easier and quicker. Attitudes and comments like iaculallad´s doom Ubuntu´s future. 

Now, to the rest of the *helpful* ubuntu community, I have this question:

What am I doing wrong? This is me trying to install Mplayer following the README file in the tarball. 

Guide:
Compiling MPlayer
~~~~~~~~~~~~~~~~~~~~~~~~

Now you can start the compilation by typing

  make

Me:
	redeye@redeye-laptop:~$ make install
	make: *** No rule to make target `install'.  Stop.

Guide:
You can install MPlayer with

  make install


Me:
	redeye@redeye-laptop:~$ make install mplayer
	make: *** No rule to make target `install'.  Stop.

Me guessing what that last line means:

	redeye@redeye-laptop:~$ make /home/redeye/Desktop/Mplayer-1.0rc2.tar.bz2
	make: *** No rule to make target `/home/redeye/Desktop/Mplayer-1.0rc2.tar.bz2'.  Stop.

	redeye@redeye-laptop:~$ make install /home/redeye/Desktop/Mplayer-1.0rc2.tar.bz2
	make: *** No rule to make target `install'.  Stop.

I give up here, and refer to a webpage optimistically claiming 'How to install ANYTHING in Ubuntu!'

Webpage:

	Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)
    Note: not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! 	If the archive is precompiled, there should be an installer or a binary executable inside it. 

Me: 
	How do I recognise that kind of file? Am I meant to be telepathic?

Webpage:
	Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to 	compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there 		is a standard way of installing these files. It will not work in every case, but it will in most (if you have the right 		dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click 	on the package and select Extract Here.

Me: 
	Make folder for mplayer to stop my desktop looking messy, then Extract here. (Extracts to /home/redeye/Desktop/Mplayer/)

Webpage:
	To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When 	you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if 	you're not sure how to do that see: Navigating the terminal. 

Me: 
	Not sure if I have the package build-essential. Also can't click on 'Navigating to the terminal' as it this is a webpage saved from 		the internet being viewed on my offline laptop. So hope for the best and skip to the next step, by navigating to the directory 	using the command cd home/redeye/Desktop/Mplayer/

Webpage:
	When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to 		check for dependencies and then create the makefile.

Me:
	redeye@redeye-laptop:~/Desktop/mplayer$ ./configure
	bash: ./configure: No such file or directory

	Pull at hair.

Webpage:
	The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some 		reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named 		almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for 		compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it 		with make and after it's been compiled you can install it. There are two ways: 

Me: 

	Open Synaptic Package Manager and open search for mplayer. Find mplayer, and click mplayer. 

Synaptic:

	W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-7_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-7_all.deb)
	Could not resolve 'archive.ubuntu.com'

Me: 
	Obviously because I'm offline. Now what?

Website:
	Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run 		make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the 		programmer needs to have enabled them.

Me:
	redeye@redeye-laptop:~/Desktop/mplayer$ sudo make install
	[sudo] password for redeye:
	make: *** No rule to make target `install'.  Stop.

Grrrrrr.

Website:
	Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, 	first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal 	install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). 	If the need arises, this will be easy to take care of from inside the checkinstall program.

Me: 
	redeye@redeye-laptop:~/Desktop/mplayer$ sudo checkinstall
	sudo: checkinstall: command not found

Website: 
	Finished.

Me:
	Lost.. again. 


Ubuntu. Do youself a favour and make self executing files, so that people can download them from the net and install them with one click on offline computers.

---

### Post by Noea on 2008-10-15
Why you compiling mplayer ? Its in the repository list .
Do you had source ? Chceck install is optional you must install them .

---

### Post by MentalOxide on 2008-10-15
I don´t know if I have ´the source´or not, i went to the mplayer website and downloaded the file. That´s it. It was a tar.bz2 I don´t know if that is the source, if I need to compile it, or what. And i obviously do like to use synaptic when I am connected to the internet, but my computer is not connected to the internet now, so i must install manually. Unless you´re telling me that synaptic can install and upgrade without connecting to the internet, which sounds incredible. 

To clarify; what I am asking is how to install a downloaded tarball, without using synaptic or apt-get, while offline.

---

### Post by Slim Odds on 2008-10-15
It depends on what the "tarball" is.

You'd be better of downloading the .deb file instead.

You're making a lot more work for yourself and making your system confused in the process. If you install from the repositories using apt-get (etc.) it will check all of the dependencies for you and do the right thing.

Otherwise, things might break or not work and you won't know why.

---

### Post by oldos2er on 2008-10-15
> **MentalOxide said:**
> I don´t know if I have ´the source´or not, i went to the mplayer website and downloaded the file. That´s it. It was a tar.bz2 I don´t know if that is the source, if I need to compile it, or what. And i obviously do like to use synaptic when I am connected to the internet, but my computer is not connected to the internet now, so i must install manually. Unless you´re telling me that synaptic can install and upgrade without connecting to the internet, which sounds incredible. 

To clarify; what I am asking is how to install a downloaded tarball, without using synaptic or apt-get, while offline.

 Look for any README or INSTALL files that came with the source code. But you're still going to need to somehow download and install the dependencies for mplayer that it needs to compile properly. If I were you I'd see about getting an internet connection for your box; it'll save you a lot of grief in the long run.

---

### Post by aysiu on 2008-10-16
Installing software in Ubuntu without an active internet connection is an exercise in masochism.

My advice: ditch Ubuntu and install a derivative like Linux Mint that includes multimedia codecs by default.

If you must install MPlayer on Ubuntu without an internet connection, download the .deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com), transfer them to a USB key, transfer them to the desktop of your Ubuntu computer and then paste these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` I don't have Hardy handy on me right now, but these are the packages that MPlayer brings with it on Intrepid: ```
 libartsc0 libaudio2 libenca0 libfaac0 libfreebob0 libggi-target-x libggi2
  libgii1 libgii1-target-x libglide2 libjack0 libmad0 libmp3lame0 libmpcdec3
  libopenal1 libsvga1 libx264-59 libxvidcore4 libxvmc1 mplayer mplayer-skins
  ttf-dejavu ttf-dejavu-extra
```

---

