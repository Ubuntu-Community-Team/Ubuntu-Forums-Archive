---
title: "Canon i250 HOW TO!"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by Rodrigo on 2005-04-23
Yes FINALY! I install my canon i250 printer and its fully functional :D, if there is a better way PLEASE! let me know!!!!!

"intalling Canon i250 printer drivers for KUBUNTU"

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop. 
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it :D

---

### Post by xodeus on 2005-04-30
[QUOTE=Rodrigo]Yes FINALY! I install my canon i250 printer and its fully functional :D, if there is a better way PLEASE! let me know!!!!!

the L4m3 way: lol...

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop. 
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it :D (at least for me IT WORK)[/QUOTE]
 I've got my i250 working through turboprint.
But thanks for this advice. I'll remember it.

---

### Post by ksudbury on 2005-04-30
Do you know if the i450x works ? as then i would not need windows :D

---

### Post by Rodrigo on 2005-04-30
[QUOTE=K31TH]Do you know if the i450x works ? as then i would not need windows :D[/QUOTE]

I think the same way, the problem is to FIND the .deb package  :?

---

### Post by ksudbury on 2005-05-01
Ahhh in the morning (ok its 5:30 AM here) so when i wake up! ill have  look ! will post back if i have any luck!!! :)

---

### Post by jotagood on 2005-05-02
Thank you SO MUCH! It really worked! I had to extra download and install the libtiff3g package but I can't believe I'm looking right now at a Printer Test Page!!! Wow. Super! \\:D/

---

### Post by Rodrigo on 2005-05-02
[QUOTE=jotagood]Thank you SO MUCH! It really worked! I had to extra download and install the libtiff3g package but I can't believe I'm looking right now at a Printer Test Page!!! Wow. Super! \\:D/[/QUOTE]

many welcomes haha

---

### Post by xodeus on 2005-05-11
[QUOTE=Rodrigo]many welcomes haha[/QUOTE]
 Really can't find the printer in Add A Printer.
The closest is ImageRunner something.
Please help.

---

### Post by müller on 2005-05-19
Hey.
I too want to thank you for this short how to.
My Canon i250 works.   :grin: 

But i sugest that you dont force the package, just write 
dpkg -i canoni250......
and the console will tell you wich packages are needed.
This way you will learn more about it.

Thanks again.

---

### Post by FtX on 2005-07-06
i don't know why, but it didn't work on mine.
it says "canon-i250 its already in its latest version", but it doesn't print!
why?!?!

thanks in advance!

---

### Post by mjurce on 2005-07-11
I did all you say,but I can't see in add Printer the model canon -i250.

---

### Post by blacksadness on 2005-07-30
well after reading a few posts here's how i got it running.. (and that happened today)

first go to canon and download the rmps bjfilter cups and bjfilteri250
then in super user mode (su or just use sudo infront of everyline) do this:
alien bj*
after that dpkg -i *.deb
now since these packages were made for redhat 9 there are some dependencies..
so do this
apt-get install libtiff3g libxml1 libglade0 libpng2
that should do it.. now just add a printer and choose the i250 driver
now the problem i had is with the resolution.. i can only run high quality printing.. do you have anyway of printing draft papers.. it's not a good idea to print a full book with high quality (i learned that the hard way)

later all..

---

### Post by Servus on 2005-09-28
:-({|= 
OH GOD!!! I GOT IT WORKING!!! IT WORKS!!!!!!
thank thank thank you...I am dancing!!!
\\:D/ 
I was not able to install libcupsys2 on Warty, but on Hoary I did it!

---

### Post by Breezy Badger on 2005-10-27
ok I have followed the instructions

> "intalling Canon i250 printer drivers for KUBUNTU"

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop.
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it 

when i go to install the printer in detects i250 as being plugged in, this is great, 
but now on step two what model to I pick, i250 is not on the list for drivers, should it be? I am no sure what to do

ALSO*** I cannot apt-get install libtiff3g, it says its dependent on something else and I cannot get it, I think this may be the problem, any suggestions?

```
xxxxxxr@xxxxxxx:~$ sudo apt-get install libtiff3g
Reading package lists... Done
Building dependency tree... Done
Package libtiff3g is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtiff3g has no installation candidate

```





Badger

---

### Post by Breezy Badger on 2005-10-30
Ok I have used these instructions

>  "intalling Canon i250 printer drivers for KUBUNTU"

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop.
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it


I looked and I have libtiff3g installed, its there for the love of god its there, I have pulled my hair out over this.  I get these results for step one

```
root@badger:/home/badger/Desktop# dpkg --force-depends -i canon-i250_2.3_i386.deb
Selecting previously deselected package canon-i250.
(Reading database ... 101735 files and directories currently installed.)
Unpacking canon-i250 (from canon-i250_2.3_i386.deb) ...
dpkg: canon-i250: dependency problems, but configuring anyway as you request:
 canon-i250 depends on libtiff3g; however:
  Package libtiff3g is not installed.
Setting up canon-i250 (2.3) ...

```

Now when i run step two this is what happens

```
root@badger:/home/badger/Desktop# apt-get -f upgrade Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  canon-i250
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2949kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 101862 files and directories currently installed.)
Removing canon-i250 ...
dpkg - warning: while removing canon-i250, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing canon-i250, directory `/usr/local' not empty so not removed.

```

so basically the damn thing does not install because its convinced I dont have libtiff3g which i clearly do, then when  run the upgrade it uninstalls the driver

lot of damn good this is doing me.

I ran turbo print and the printer works just fine, but I have to pay like 30 dollars for the program and im not willing.

Please help me, im dying here

---

### Post by Breezy Badger on 2005-10-30
I am to the point of begging now, yes thats right i am that crazy... please please please someone try to install this driver for the love of god, even if you dont have the printer just try to install it and see if you get the same errors with this libtiff3 garbage.  I have to know if its on my end or its a general problem

Badger

---

### Post by iluciv on 2005-11-25
I'm having the same problem as Breezy badger. Installs recognises the printer but has dependency problems and doesn't have i250 driver in the new printer section. 

How do I remove the dpkg installation (the --forced-depends one) so I can try the installation agian? I tried useing the reverse of the installation command but this isincorrect as I require the names ofthe files that were installed; How does one do this? 

Many thanks

---

### Post by nder on 2005-12-14
I installed everything sucessfully, but the printer is not showing up.  Im on Breezy.

---

### Post by nder on 2005-12-14
Ok, printer shows up now, but wont print test page.  Also, I cannot seem to install libtiff3g.

---

### Post by pppoe_dude on 2005-12-25
Ok, if you follow all the above instructions, it should work, you might need to install libtiff3g (search on google "libtiff3g ubuntu", i installed the hoary version and it works fine.

IF YOUR PRINTER DOESNT SHOW UP IN 'ADD NEW PRINTER', then do sudo /etc/init.d/cupsys restart and it should work.

bye

---

### Post by Luke771 on 2006-02-01
I followed all the steps and got the right output on the final apt-get, but it's still refusing to print. No biggie, I dont use the printer so much anyway and if I need to, I can still swithch to Windows (I'm on a dual boot machine) but I would like to make my i250 work on Breezy too.

---

