---
title: "Noob fragge--can i install an *.rpm on Ubuntu"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by paredown on 2006-02-15
Still playing with this. Compaq have a management s/w package that lets you monitor a smart UPS.

I can download and unpack *.tgz and get a file called PowerManagerRA-4.0-10.i586.rpm

when i click i get an error 'Could not open archive type not supported' 

RPM is redhat i think, but can I get the functionality any other way? Basically it gives a web interface, tray icon and admin login for controlling & monitoring the UPS from a browser interface.
dean

---

### Post by MetalMusicAddict on 2006-02-15
Im not sure of the commands but you need to use a program called **alien**. Search the forums for it.

---

### Post by r4ik on 2006-02-15
First you have to install alien.
sudo apt-get install alien
Then do: sudo alien package_file.rpm
And last: sudo dpkg -i package_file.deb

Good luck.

---

### Post by paredown on 2006-02-16
Did that--and I now have a file *.deb, although it appears as locked. So conversion is OK I'm assuming.  

Apparently 2nd line--the "i" command provided--also set it up. I can't see it or use it, since it bypassed setup parameters... 

(and how does *nix distinguish between a program and a whatever--eg alien does not appear as a "program" (I know this is Windows denken, but we're all prisoners of our past...))

How do I re-run the setup? Or at this point it seems I should uninstall and try again.

If I upack all, and try the CPQ provided Setup, it triggers an endless licence agreement, and only then do you get to set parameters. 

If I use the CPQ setup script, the setup fails and tells me to use Alien . . . so clearly it sees the *.rpm package.

(And people ask why I find *nix frustrating....)

I'm looking at the alien command set to see if I can figure out a way to install and get the prompts to agree to the licence . . .

thanks,
dean

---

### Post by paredown on 2006-02-16
Well we're making no progress here--I reran alien directly on the *.rpm with the -i switch (and added the -v so I could see what was up.)
Everthing appears to unpack.

the final lines though are

 mkdir PowerManager-4.0/debian
        hostname -f
        822-date
        hostname -f
        822-date
        chmod 755 PowerManager-4.0/debian/rules
        debian/rules binary 2>&1
        dpkg --no-force-overwrite -i powermanager_4.0-11_i386.deb
        find PowerManager-4.0 -type d -exec chmod 755 {} ;
        rm -rf PowerManager-4.0

Anyone willing to help me decipher? Are these the instructions for completing the install?

Thanks,
dean

---

