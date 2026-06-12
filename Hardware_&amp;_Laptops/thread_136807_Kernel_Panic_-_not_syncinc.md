---
title: "Kernel Panic - not syncinc"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by Mangelo on 2006-02-26
**Summary:** Kernel Panic - "not syncing: can't allocate buffers"is my error problem, symptoms and the way i came to this final solution (haha...final problem) are proceeding, but for the sake of sparing the readers, that aforementioned error message is (i think) what i have problems with. thanks in advance if you do brave this entire thing!  I pretty much can't do anything right now w/ this system.  I posted this in the HowToForge forums, and got a decent reply..but nothing that really helps me, in terms of me knowing wtf im doing :confused: . over in the other forums i was pointed to a document that tells me how to edit documents via command line...but that gets me nowhere, cause i cant even use the vi command, i get to a prompt that says "grub>"  

once again, any thanks will be GREATLY appreciated




Heyos all, brand new linux user here! And i need to recover from a total fubar'd newbie mistake! This is the only time i ever touched linux, after (literally) having grown up with a windows system (3.1 and above)...I just had an old machine and a copy of ubuntu 5.10, so im taking myself on a joy ride...

unfortunatly it got cut short. really quickly.

I was following the HOW-TO at [http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10) . Every time i had to open a file to edit, i used gedit in its gui (does it even have a command line interface? i have no clue...is command line interface even the right vocabulary? *shrug*), but anywho... the gui loaded up every time i tried to run it... then i got up to page 3 of the how to, and the steps where you run apt-get to install the packages. 

"Edit /etc/apt/sources.list And Update Your Linux Installation" That is the first step i did that im pretty sure the mistake occured somewhere, because I never tried to open up any other window until I noticed what happened....

I run through the exact tutorial, copy and pasting into the terminal the apt-get commands to update, upgrade, install ssh, install the other softwrae, and set the quota... then i tried to follow onto the next step, which would be to edit fstab... so in keeping with my windows-native way, i go focus on the (already open) file browser...double click on fstab...and wait for gedit to load up like its been doing (BTW i am logged into ubuntu this entire time AS root, not just root permissions through command line. newbie mistake #1, haha). well...gedit doesnt load up! so i try "gedit" in the terminal...and i get the error:

Re: Xlib: connection to ":0.0" refused by server - Xlib: No protocol specified.

so im like "wtf m8"... i do a little searching online (through this windows machine sitting next to the now - fubard' linux box), find its something with drawing windows on the screen..kinda makes sense cause no gui is loading up (i tried to open running services, package manager, file browser, nothing opened).... so i have still no luck... then a light comes on above my head.

i'll just undo everything i've done up until the point i know xlib was working fine! so i type apt-get remove quota

then i type apt-get remove ssh openssh-server

then...i take a look at this nice big line of pure and utter nonsense to me

apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev
little did i know that therefore typing

apt-get remove binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev 

would screw me as it did...cause all of a sudden i saw terminal output saying "removing ubuntu" ! now that struck me as odd..but i dont know much about linux..maybe it was a duplicated name...shortcut? nothing... then i noticed everything else started to get removed....

i havent panicked at this point...it will remove everything and i'll just use apt-get to rebuild the interface...it would be hard, but i have the resources(internet) to find out how to do it...

then the damn thing freezes on it!! (its not the best of computers, never had been). now every time i turn on the computer, my bios (phoenix bios 4.0) runs properly, finds everything correctly (including my cd drive..i thought i can just resotre off the ubuntu cd, apparntly i cant). it hangs up a bit on loading GRUB...and even if i press esc into the menu and select the ubuntu (recovery mode) module, it returns to me the same error

Kernel Panic - not syncing: can't allocate buffers. and ya...thats it... i cant do anything past that. I tried to boot with the installation cd (and right now as i type thjis i got the idea to try the live cd...so as i type im gonna let that try to boot itself up...results will come as they happen), and just reinstall the whole thing, but simply presseing "enter" for base system, or typing "server" to install the bare bones leads me to the same error message, and a freeze in cpu activity.

I just want to get a fresh install of linux, and preferably with any distro that is good at doing file serving throughout my windows based household (3 other windows computers) and yes, i do realize that i was following an isp tutorial, meanwhile i should have been following the samba tutorial instead..i noticed that (after) the whole process started going horribly wrong on me, thats why i want a fresh install so i can follow that one properly.

any help would be GREATLY appreciated! thanks in advance

edit: forgot to include the results of trying the Live cd instead of install....same exact problem -_-

---

