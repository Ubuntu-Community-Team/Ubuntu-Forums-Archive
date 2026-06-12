---
title: "Will a Lexmark Z2320 printer work under 8.04?"
date: 2008-07-10
forum: Hardware
---

### Post by indiworks on 2008-07-10
I'd like to buy a simple printer, a Lexmark Z2320. How can I find out if it is going to work? 

Lexmark does not offer an Ubuntu driver for this model and the Synaptic Packet Manger only lists one item when searching for Lexmark: "Lexmark 2050 Color Jetprinter Linux Driver". (I'm also not quite sure if this really is a printer driver since it also says "Filter to convert a Postscript file to Lexmark 2050 format." If it is a printer driver: will it work with a Lexmark Z2320?)

So far all hardware that I tried to use with my new Ubuntu PC just worked. How is the situation with printers? The salesman said that if Linux is not listed on the printer's package then it is not going to work.

Now if this model is not supported, where could I find a list with simple and cheap (b/w) printers that work under Ubuntu 8.04? Thanks!

---

### Post by stchman on 2008-07-10
> **indiworks said:**
> I'd like to buy a simple printer, a Lexmark Z2320. How can I find out if it is going to work? 

Lexmark does not offer an Ubuntu driver for this model and the Synaptic Packet Manger only lists one item when searching for Lexmark: "Lexmark 2050 Color Jetprinter Linux Driver". (I'm also not quite sure if this really is a printer driver since it also says "Filter to convert a Postscript file to Lexmark 2050 format." If it is a printer driver: will it work with a Lexmark Z2320?)

So far all hardware that I tried to use with my new Ubuntu PC just worked. How is the situation with printers? The salesman said that if Linux is not listed on the printer's package then it is not going to work.

Now if this model is not supported, where could I find a list with simple and cheap (b/w) printers that work under Ubuntu 8.04? Thanks!

The openprinting database does not even list that printer so chances are it does not work.

Lexmark is poor when it comes to Linux support.

If you want inexpensive b/w printing go with an HP laserjet.  I have seen them for ~$100 and they typically print 3000 pages per cartridge.

Samsung laser printers are pretty Linux friendly as well.

The ML-2510 can be had for under $100 and works perfectly with Linux.

[http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510)

---

### Post by indiworks on 2008-07-10
> **stchman said:**
> The openprinting database does not even list that printer so chances are it does not work.

Lexmark is poor when it comes to Linux support.

If you want inexpensive b/w printing go with an HP laserjet.  I have seen them for ~$100 and they typically print 3000 pages per cartridge.

Samsung laser printers are pretty Linux friendly as well.

The ML-2510 can be had for under $100 and works perfectly with Linux.

[http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510)

The openprinting database looks just like what I need - thanks!

Strange that some companies still ignore the Linux market - one customer less for Lexmark... This one would have been ideal, a really cheap (> € 40.-) printer currently being offered by a large electronics discounter here in Europe, cartridges can be refilled (though they don't tell you how-to do that of course).

---

### Post by Milos_SD on 2008-12-21
Here is the driver for Lexmark z2320:

[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)

This is a link from lexmark download site. There is packages for Suse 11, Debian, Ubuntu 8.04 and Foresight distros.

---

### Post by dave66 on 2009-05-07
> **Milos_SD said:**
> Here is the driver for Lexmark z2320:

[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)

This is a link from lexmark download site. There is packages for Suse 11, Debian, Ubuntu 8.04 and Foresight distros.

I have downloaded the driver listed above from Lexmark but when I run it, during the installation I'm getting an error:

"Package architecture (i386) does not match system (lpia)"

And then the installation fails. :confused:

I'm trying to install the printer on a Dell Mini-9 running 8.04 LTS can anyone offer advice?

---

### Post by dave66 on 2009-05-08
Ok, so I have contacted Lexmark and they have provided the following solution:

[INDENT]In X23xx and X26xx models the only way to let the user successfully install driver on so called NETBOOKs is to do the following:

1) You need these two scripts, and must copy these two scripts right beside where the  "lexmark-inkjet.deb.sh  "   installer is located.(See attached file: extracter.sh)  (See attached file: deb2lpia.sh)

2) open terminal and go to the location of the Lexmark installer, and do:

in the terminal do --->   sh   ./extracter.sh lexmark-inkjet-09-driver-1.0-1.i386.deb.sh
result, this file gets created ---> lexmark-inkjet-09-driver-1.0-1.i386.deb

3) Rename lexmark-inkjet-09-driver-1.0-1.i386.deb  to installer_i386.deb
by issuing the following command at the terminal --->   mv lexmark-inkjet-09-driver-1.0-1.i386.deb   installer_i386.deb

4) please then do --->    sh   ./deb2lpia.sh installer_i386.deb
result is this file gets created  installer_lpia.deb

5) Finally, at last, do --->    dpkg   -i installer_lpia.deb

That's it. The driver should be successfully installed and got registered into the synaptics record database ( which means, you can open synaptics UI, and can find our driver in the group called "notfree ").[/INDENT]

I'm going to test this out shortly (but expect it to work) and will post to confirm if it worked.

---

### Post by brizio on 2010-01-12
Help me!
I bought the Lexmark S305 and I downloaded the following driver lexmark-inkjet-09-driver-1.0-1.i386.deb.sh "because Ubuntu did not recognize.

 After the first stages of the installation you receive the following error message: "Execute: dpkg-i-Lexmark Inkjet-09-driver-1.0-1.i386.deb 2> & 1 | tee / home / nicola / lua_ixdeyG / installerror_msgs

dpkg: error in lexmark-inkjet-09-driver-1.0-1.i386.deb (- install):
 the architecture of the package (i386) does not match that of the system (amd64)
There were errors in:
 lexmark-inkjet-09-driver-1.0-1.i386.deb. "

and the installation stops.
The S.O. bit Ubuntu 9.10 and the processor is an AMD Athlon 64.
I wonder if the procedure is also indicated in my case.
Thank you very much.

---

### Post by kalon33 on 2010-01-17
Hello brizio,

Use the same procedure as for lpia (the one which dave66 described) with the script I have modified.

It should work !

Have a nice day.

--kalon33

---

### Post by normster on 2010-02-05
I just tried this with my Lexmark S305 and it worked great!!  Thanks for that modified script kalon33!

Is there a good tutorial on creating scripts out there?

Thanks,
Normster

---

### Post by sankara09 on 2010-02-17
Hi,

I used the same for the lexmark Pro 705 as i am using ubuntu 9.10 AMD64 so i got the amd64.deb (many thanks).

I wonder if those lexmark drivers lexmark gives are for both scanner and printer (multi features printer) or are they just for the printer part ? (can we use the scanner part with xsane ?). => i am tired to go to osx or windows via my multiboot or virtual systems to have scanner on printer useable...)

thanks for your help.

---

### Post by Sidster on 2010-03-10
Thanks for the script kalon33. I managed to get the same results buy forcing the i386 package to install in a 64 bit environment using the following command.

```
sudo dpkg --force-all -i installer_i386.deb
```

Although as mentioned above by lexmark, using the conversion script will allow the installed deb to show up in synaptic

The printer works fine most of the time. Certain programs like picasa print garbage though. Things like margins can sometimes be difficult but I can live with it. Considering this is a wireless printer I'm quite impressed that it even works at all.

The best way to print photos is using gimp. If you tweak the settings enough you can get nice borderless prints.

The only thing still bothering me is the lexmark toolbox. The installer puts a link in the menu and everything but it doesn't launch. I've tried to luanch the script manually but no luck. The closest I've come is getting the following error in the terminal.

```
my_laptop:/usr/local/lexmark/lxk09/bin/.scripts$ sh ./lexijtools 
./lexijtools: 16: Syntax error: "(" unexpected
```

Any ideas? Is it even worth using the lexmark toolbox? I mean besides checking the ink levels (which can be done through web interface) what else is there?

Oh and has anybody had any luck getting the scanner to work in 64bit? I've tried both wifi and USB but no luck.

---

### Post by a.quattrinili on 2010-03-19
I had this problem too; I mean lexmark printer toolbox didn't start and didn't show any error message.
I figured out that you have to modify the variable JAVA_CMD in the script file /usr/lexinkjet/lxk09/bin/.scripts/shared, and setting the latter to "java" instead of "/usr/lexinkjet/jre/bin/java". Otherwise it cannot found the java application launcher, which is already in the enviroment variables if you have already installed java package.
 So after the modification it should be: JAVA_CMD="java".


In your case it seems that you have also a syntax error in the script lexijtools, so you have to check it and correct the error. Probably a bracket is missing or something like that at line 16.

If you want, you can upload somewhere the script and I can try to fix it.



By the way you can use lexmark printer toolbox for maintenance purpose (e.g. clean ink cartridges, align ink cartridges, print test pages and setup your wireless printer).

---

### Post by Sidster on 2010-03-22
> **a.quattrinili said:**
> I had this problem too; I mean lexmark printer toolbox didn't start and didn't show any error message.
I figured out that you have to modify the variable JAVA_CMD in the script file /usr/lexinkjet/lxk09/bin/.scripts/shared, and setting the latter to "java" instead of "/usr/lexinkjet/jre/bin/java". Otherwise it cannot found the java application launcher, which is already in the enviroment variables if you have already installed java package.
 So after the modification it should be: JAVA_CMD="java".

Thanks man. That fixed it. I really appreciate the help. Ubuntu community FTW!!! :p

I've no idea what that syntax error was though. It doesn't seem to be causing a problem so far.

Now all thats left is getting the scanner to work. For now I'm just scanning to a flash drive. ;)

---

### Post by emi73 on 2010-04-03
thank you very much.
I use lexmark S300 with ubuntu 9.10 AMD64.

---

### Post by arska on 2010-05-18
Thanks dave66!



I managed to install my Lexmark Prevail Pro709 using lexmark-inkjet-09-driver-1.5-1.i386.deb.sh.

My distro is kubuntu 10.04 amd64. I'm not sure if it's necessary, but I also installed for the compatibility the getlibs-all.deb package.

The printing is ok.

Also the lexitool works thanks to a.quattrinili for the advice!

---

### Post by steveneddy on 2010-05-26
This worked for me in 8.10 and worked perfectly in Lucid.

Now I can print at my GF's house and get some work done.

Thanks.

---

### Post by leoniman on 2010-07-24
Hi,
I've tried this procedures on 10.04 AMD64. 
It works, but the scanner is not visible.
Any idea how to make it visible?

On the same machine I've also an i386, and everything works there.

p.s.
I was also able to succeed in running the lexmark installer by:

- open terminal
- cd where you have the lexmark-inkjet-09-driver-1.5-1.i386.deb.sh file
- ./lexmark-inkjet-09-driver-1.5-1.i386.deb.sh --noexec --target  lexmark
- cd lexmark
- edit config/run.lua and add ** --force-architecture**  to the**  dpkg -i**  lines
- cd ..
- ./startupinstaller.sh
- With this method the package is not visible as installe package.

But also in this case the scanner is not visible.

Thanks for any help.

---

### Post by gold3n_dragon on 2010-10-02
Hi all... I am using alienware laptop installed windows 7 and i am using WUBI to install ubuntu 10.04 to use side by side with windows. I am trying to install driver for LEXMARK INTERPRET s405 and i get this error message 
dpkg: error processing lexmark-inkjet-09-driver-1.5-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 lexmark-inkjet-09-driver-1.5-1.i386.deb

Please help me. I am NEW to this os so really dont know how to do it. Thanks for any help.](*,)

---

### Post by cedricmail on 2010-10-31
Thanks to you guys! I just bought a Lexmark s305 especially because there was a linux logo on the box! I was really desapointed when i saw it didn't work with ubuntu 10.10 x64 :s
Now i'd like to use the scanner and i'm lost!

Lexmark has to move its *** to make it work, it's their job!!!

---

### Post by slaminallaeraew on 2010-12-31
> **a.quattrinili said:**
> I had this problem too; I mean lexmark printer toolbox didn't start and didn't show any error message.
I figured out that you have to modify the variable JAVA_CMD in the script file /usr/lexinkjet/lxk09/bin/.scripts/shared, and setting the latter to "java" instead of "/usr/lexinkjet/jre/bin/java". Otherwise it cannot found the java application launcher, which is already in the enviroment variables if you have already installed java package.
 So after the modification it should be: JAVA_CMD="java".

I am also having problems with finding the Lexmark Printer Toolbox. After I had completed installing the driver and doing the initial setup of the printer, there was an option to open the Printer Toolbox, which I chose and it worked fine. However, after closing it, I went looking for it again, but there is not even a menu option, as the previous poster had mentioned. Apparently your instructions that I quoted above were helpful to others; however, I do not understand them. I went looking for location /usr/lexinkjet but found nothing. I have no clue what these modifications and such are that you speak of, so can someone help me with a step-by-step of what a.quattrinilli's instructions are telling me to do? Sorry, I switched to Ubuntu from Windows last week, so I am still trying to understand how this stuff works. Thank you.

---

### Post by slaminallaeraew on 2010-12-31
> **gold3n_dragon said:**
> Hi all... I am using alienware laptop installed windows 7 and i am using WUBI to install ubuntu 10.04 to use side by side with windows. I am trying to install driver for LEXMARK INTERPRET s405 and i get this error message 
dpkg: error processing lexmark-inkjet-09-driver-1.5-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 lexmark-inkjet-09-driver-1.5-1.i386.deb

Please help me. I am NEW to this os so really dont know how to do it. Thanks for any help.](*,)

I was having the same problem, except backwards. I discovered that i386 and i686 denote 32-bit systems, whereas AMD64 denotes 64-bit systems. In other words, the error message is telling you that the driver that you are trying to install is meant for 32-bit systems, but your system is 64-bit. You should try installing the 64-bit version of the driver.

---

### Post by slaminallaeraew on 2011-01-05
If anybody else is having trouble locating the Lexmark Printer ToolBox, I discovered where it is on my machine. Although I never received any replies elsewhere about how to find it, I discovered it myself while browsing around. Look in System>Control Center>Hardware>Lexmark Printer ToolBox Legacy. That did it for me; I simply clicked it, and it opened fine. Someone else mentioned it being present under the Applications menu, and since I found that to be untrue on my system I assumed that I did not have the ToolBox at all. However, it was simply in the Control Center the whole time.

---

### Post by Kaboontu on 2011-02-24
hello.
it seems that lexmark is NOT doing me a favor.
I bought S305 so that i can have linux support.
Till recently i was using windows, so everything was cool.
BUT since i switched i need to make that thing work.
I downloaded the drivers from lexmark support page.
I did everything correctly, but when it promts me touse the password 
it denies it as if i had used a wrong one.
I could not find a solution to this matter for almost a week now.
I would really appreciate your help.

---

### Post by anglican on 2011-02-25
> **Kaboontu said:**
> hello.
it seems that lexmark is NOT doing me a favor.
I bought S305 so that i can have linux support.
Till recently i was using windows, so everything was cool.
BUT since i switched i need to make that thing work.
I downloaded the drivers from lexmark support page.
I did everything correctly, but when it promts me touse the password 
it denies it as if i had used a wrong one.
I could not find a solution to this matter for almost a week now.
I would really appreciate your help.You should not hijack an old thread about a different printer - you should start a new thread with the name of your printer in the title. However, since we're here now I'll try and help. The problem you describe is very common with Lexmark installations and can be solved by running a shell as root and doing the installation in that shell (I'll assume you've already downloaded the driver file):
```
sudo bash
tar xvfz lexmark-inkjet-legacy-1.0-1.i386.deb.sh.tar.gz
./lexmark-inkjet-legacy-1.0-1.i386.deb.sh
```H

---

### Post by Kaboontu on 2011-02-25
At first i thought it should be more polite to do so in an existing thread.
Then i decided to make a thread.
It wont happen again then:)
Problem solved with sudo -i sh 
thank you.

---

### Post by Lolepops on 2011-09-04
> **dave66 said:**
> Ok, so I have contacted Lexmark and they have provided the following solution:

[INDENT]In X23xx and X26xx models the only way to let the user successfully install driver on so called NETBOOKs is to do the following:

1) You need these two scripts, and must copy these two scripts right beside where the  "lexmark-inkjet.deb.sh  "   installer is located.(See attached file: extracter.sh)  (See attached file: deb2lpia.sh)

2) open terminal and go to the location of the Lexmark installer, and do:

in the terminal do --->   sh   ./extracter.sh lexmark-inkjet-09-driver-1.0-1.i386.deb.sh
result, this file gets created ---> lexmark-inkjet-09-driver-1.0-1.i386.deb

3) Rename lexmark-inkjet-09-driver-1.0-1.i386.deb  to installer_i386.deb
by issuing the following command at the terminal --->   mv lexmark-inkjet-09-driver-1.0-1.i386.deb   installer_i386.deb

4) please then do --->    sh   ./deb2lpia.sh installer_i386.deb
result is this file gets created  installer_lpia.deb

5) Finally, at last, do --->    dpkg   -i installer_lpia.deb

That's it. The driver should be successfully installed and got registered into the synaptics record database ( which means, you can open synaptics UI, and can find our driver in the group called "notfree ").[/INDENT]

I'm going to test this out shortly (but expect it to work) and will post to confirm if it worked.

Hi,

i tried to follow this method, but it doesn't work (i'm on 11.04).

I've got this problem :
```
lolepops@lolepops-msi:/media/Data/Sauvegarde Linux$  sh ./extracter.sh lexmark-inkjet-legacy-wJRE-1.0-1.i386.deb.sh
./extracter.sh: 9: [[: not found
./extracter.sh: 21: ./lexmark-inkjet-legacy-wJRE-1.0-1.i386.deb.sh: Permission denied
cd: 22: can't cd to tmp
./extracter.sh: 23: bin/linux/x86/libc.so.6/lzma-decode: not found
mkdir: impossible de créer le répertoire «vault»: Le fichier existe
tar: ../arch.tar : la fonction open a échoué: Aucun fichier ou dossier de ce type
tar: Error is not recoverable: exiting now
cp: impossible d'évaluer «tmp/vault/lexmark-inkjet*»: Aucun fichier ou dossier de ce type

```

---

### Post by aeriko on 2012-09-17
Hi,

The problem I have is that on a i386 system each print I send went in queue mode. Any idea? pls

---

