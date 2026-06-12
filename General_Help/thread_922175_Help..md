---
title: "Help."
date: 2008-09-17
forum: General Help
---

### Post by Dlanir on 2008-09-17
Yes another noob.........

LOL can somebody help me please I'm trying to install Byond i got it un zipped and got in the terminal and cd it but it doesn't really get me anywhere can someone walk me through the process step by step pretty please?

I have Ubuntu by the way...

---

### Post by Dlanir on 2008-09-17
I already unzipped it and started the setup now where do I go?

---

### Post by DrMelon on 2008-09-17
Have you tried finding it with "Add/Remove Applications" or the Synaptic Package Manager? If there is an entry for it, it will automatically download all the required files and dependancies, set it up, and make it ready to use.

---

### Post by iaculallad on 2008-09-17
For sure that's a tarball installer w/c needs the usual make compile process, you might need to install the build-essential file:

```
sudo apt-get install build-essential
```

Once you're finish extracting the archive, try reading either Readme.txt or Install.txt (this comes with the archive file) w/c will guide you through the installation process.

---

### Post by Dlanir on 2008-09-17
I searched it in both synthetic and add/remove it didn't come up at all in add/remove but it comes up in synthetic but I cant do anything with it...

I have build essential stil not getting far in the setup i make it as far as make then make here
 But after i try to type in the source thingy it doesn't work.

---

### Post by Dlanir on 2008-09-17
Will wine allow me to install the windows version?

---

### Post by Dlanir on 2008-09-17
rinald@rinald-desktop:~$ cd /home/rinald/Desktop/byond
rinald@rinald-desktop:~/Desktop/byond$ make
There are two options for installing BYOND.  You can install
it for all users or you can install it for your own personal
use.  To install for all users, you must run this makefile
as root.  In that case, edit this makefile, configure the
installation parameters to your liking, and run 'make install'.

To install for your personal use, simply put the 'byond'
directory where you want to keep it and type 'make here'.

rinald@rinald-desktop:~/Desktop/byond$ sudo make install
[sudo] password for rinald: 
if [ ! -d /usr/local/byond ]; then mkdir /usr/local/byond; fi
cp -R cfg bin /usr/local/byond
if [ "" = "yes" ]; then \
		chown root /usr/local/byond/bin/DreamDaemon; \
		chmod a+xs /usr/local/byond/bin/DreamDaemon; \
		if [ "" = "yes" ]; then \
			chown root host/host.dmb; \
			chmod a+xs host/host.dmb; \
		fi \
	fi
ln -f -s /usr/local/byond/bin/DreamDaemon /usr/local/bin/DreamDaemon
ln -f -s /usr/local/byond/bin/DreamSeeker /usr/local/bin/DreamSeeker
ln -f -s /usr/local/byond/bin/DreamMaker /usr/local/bin/DreamMaker
ln -f -s /usr/local/byond/man/man6/DreamDaemon.6 /usr/share/man/man6/DreamDaemon.6
ln -f -s /usr/local/byond/man/man6/DreamMaker.6 /usr/share/man/man6/DreamMaker.6
ln -f -s /usr/local/byond/man/man6/DreamSeeker.6 /usr/share/man/man6/DreamSeeker.6

*****************
You can find out more about the software by doing 'man DreamDaemon'.
A host server has also been included so edit host/hostconf.txt and
boot up your world server!
*****************


[COLOR="Blue"]This is as far as I get without trouble can someone please direct me from here?[/COLOR]

Now what?

---

