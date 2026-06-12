---
title: "xerox phaser 3100 mfp"
date: 2010-04-04
forum: Hardware
---

### Post by kornell on 2010-04-04
dear friends,

I just bought a xerox phaser 31oo mfp provided with ubuntu 7.1 drivers. on the machine i have ubuntu 9.1 and i'm not able to let it work. all files are in correct directory but sane is not able to see it and continue to give me "hardware not found" error. Do you have any suggestions?

i forgot to say that the printer works correctly

---

### Post by luissil on 2010-04-27
> **kornell said:**
> dear friends,

I just bought a xerox phaser 31oo mfp provided with ubuntu 7.1 drivers. on the machine i have ubuntu 9.1 and i'm not able to let it work. all files are in correct directory but sane is not able to see it and continue to give me "hardware not found" error. Do you have any suggestions?

i forgot to say that the printer works correctly

i have the same problem i've been surfing the web, and i can't find any answer, i have ubuntu 9.10 64 bits... :(

---

### Post by indupati on 2010-05-26
Hi 
i've found the solution
for 32 bit systems here

just use debian driver 

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3100MFP&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3100MFP&Xlang=en_US&Xcntry=USA)

```
indu@krasota:~/Downloads/XeroxPhaser3100-1.0-linux-2.6Debian-intel$  gksudo ./setup 
```

driver should appear in cups

---

### Post by luissil on 2010-05-26
> **indupati said:**
> Hi 
i've found the solution
for 32 bit systems here

just use debian driver 

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3100MFP&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3100MFP&Xlang=en_US&Xcntry=USA)

```
indu@krasota:~/Downloads/XeroxPhaser3100-1.0-linux-2.6Debian-intel$  gksudo ./setup 
```driver should appear in cups


any idea for 64 bit systems??

---

### Post by ein.einhander on 2010-08-13
> **luissil said:**
> any idea for 64 bit systems??
you'll have to install all ia-32* lib's to get it work. (may be need to  to use dpkg -x 
 libcupsimage2_1.3.8-1lenny4.1_i386.deb and then copy libcupsimage.so.2 in /usr/lib32/libcupsimage.so.2)
I'm on Debian amd64 and printing work's ok.
But scaner works only by sudo scanimage. Xsane can't see it.
Any ideas?

---

### Post by TariBuntu on 2010-08-13
Hello there people,

I'm on a 64-bit 10.04 and printing works with the provided 32-bit Ubuntu drivers - I have followed the installation instructions on the CD, and no problems at all.

The scanner is a completely different story. The device is not recognised, even with elevated privileges and 32-bit libraries.

For the time being, I've set up a 32-bit distro in VBOX, solely for scanning purposes. Not the most elegant solution, I know, but it's the best I could come up with.

Just thought I'd share my scenario with the rest of you... :confused:

---

### Post by luissil on 2010-08-18
> **ein.einhander said:**
> you'll have to install all ia-32* lib's to get it work. (may be need to  to use dpkg -x 
 libcupsimage2_1.3.8-1lenny4.1_i386.deb and then copy libcupsimage.so.2 in /usr/lib32/libcupsimage.so.2)
I'm on Debian amd64 and printing work's ok.
But scaner works only by sudo scanimage. Xsane can't see it.
Any ideas?

sorry i don't understand how to do that, could u be more specific? you know... step by step instructions or something... ;)

---

### Post by khartahk on 2010-09-15
I also have this printer/scanner. I can scan an image using scanimage command and also my scanner is recognized if do scanimage -L. But when I try to use simple-scan or xsane they both say that the device is not found. What could be the problem here. O and i have Ubuntu 10.04 64bit. And I installed the Xerox provided drivers for 7.10 for both the printer and the scanner. And I've also added my self to lp group because that was stopping me from using the scanner through a virtualbox machine with XP installed. I've also added my self to the scanner group. Any help would be greatly appreciated.

---

### Post by christos111 on 2010-10-31
I have the same problem and I am running Ubuntu 10.04.
I do not know how to install printer driver that made for ubuntu 7.1 to be install on Ubuntu 10.04.
Any help with be good.

Thank:)

:popcorn:

:guitar:

---

### Post by TariBuntu on 2010-10-31
Update: I have switched to 10.10 since my last post, but that is irrelevant. I can confirm the scanner doing the scanning via terminal with sudo scanimage, but I will stay with a 32-bit Ubuntu in Virtualbox for now.

In reply to **christos111** and **khartahk**, and all interested:

To install the 32-bit drivers from the cd, open "README_Ubuntu.htm" and "Scanner Installation Guide_Ubuntu.htm" for step-by-step instructions. Just read it and do what it says.

To start the install, just go to these folders, open a terminal and start the files with sudo: "XeroxPhaser3100-1.0-linux-2.6Ubuntu-intel/setup" and "XeroxPhaser3100sc-1.0-linux-2.6Ubuntu-intel/setup"

Notes:

1. For this purpose, it's easier if you always choose the GUI step, rather than the terminal commands.
2. The cups server pages on your machine will look completely different from that in the instruction, but you will find what you need (add printer, configure printer, things like that)
3. Virtualbox: You do not need any special setting to scan in there. Just make sure you use the full version which has USB support (see the virtualbox website), and not Virtualbox OSE from the repositories.

I hope this helps someone.:)

---

### Post by christos111 on 2010-11-04
I have followed the instruction, to install printer driver for Xerox Phaser 3100 driver. But I received an error message  saying I must be in root login, but I am in the root login.
 I think the something wrong with my Ubuntu root login.

Please help

Christos111

:guitar:
\\:D/

---

### Post by TariBuntu on 2010-11-04
> **christos111 said:**
> I have followed the instruction, to install printer driver for Xerox Phaser 3100 driver. But I received an error message  saying I must be in root login, but I am in the root login.
 I think the something wrong with my Ubuntu root login.

Please help

Christos111

:guitar:
\\:D/
Here are the steps that should install the printer:

1. Extract the "XeroxPhaser3100-1.0-linux-2.6Ubuntu-intel" on the Desktop
2. Terminal: cd ~/Desktop/"XeroxPhaser3100-1.0-linux-2.6Ubuntu-intel"
3. Terminal: sudo ./setup 
4. Terminal: enter your password
5. Go through the setup wizard
6. Firefox: open "http://localhost:631"
7. Firefox: choose "CUPS for Administrators/Adding Printers and Classes"
8. Firefox: choose "Printers/Add Printer"
9. Firefox: enter your username and password
10.Firefox: just follow the wizard, then configure the printer as you wish

---

### Post by adityachs on 2010-11-06
Hi,

I have a similar problem. Printer driver insatlled and working fine. But Scanner is not working.

I have installed scanner drivers from CD came with machine as well as downloaded from XEROX Support. in both the cases, sane gives an error "failed to open device 'xeroxphaser3100:usb:004:003': Access to resource has been denied".
(I restarted xerox device several times, but same response:(  )

I tried the below command given in the install guide.
[FONT=Arial] # ln –s /usr/lib/sane/libsane-XeroxPhaser3100.so.1 /usr/local/lib/sane/libsane- XeroxPhaser3100.so.1
[/FONT]which gives the below error:[FONT=Arial]
ln: target `/usr/local/lib/sane/libsane-XeroxPhaser3100.so.1' is not a directory
[/FONT]
I am not sure what to do? Plz help[FONT=Arial]
[/FONT]

---

### Post by TariBuntu on 2010-11-06
> **adityachs said:**
> Hi,

I have a similar problem. Printer driver insatlled and working fine. But Scanner is not working.

I have installed scanner drivers from CD came with machine as well as downloaded from XEROX Support. in both the cases, sane gives an error "failed to open device 'xeroxphaser3100:usb:004:003': Access to resource has been denied".
(I restarted xerox device several times, but same response:(  )

I tried the below command given in the install guide.
[FONT=Arial] # ln –s /usr/lib/sane/libsane-XeroxPhaser3100.so.1 /usr/local/lib/sane/libsane- XeroxPhaser3100.so.1
[/FONT]which gives the below error:[FONT=Arial]
ln: target `/usr/local/lib/sane/libsane-XeroxPhaser3100.so.1' is not a directory
[/FONT]
I am not sure what to do? Plz help[FONT=Arial]
[/FONT]
If you're running a 64-bit system it won't work properly. I'm planning to put together a thingy that installs the scanner drivers and provides some basic scanning functionality via scanimage through a gui. I'm amidst a million other things right now so you'll just have to wait a bit for it...

Until then, my advice is to run a 32-bit distro in VirtalBox. If you're into heavy scanning, you might think about switching your system to 32-bit...

Sorry I could not help you more right now.

---

### Post by adityachs on 2010-11-08
> **TariBuntu said:**
> If you're running a 64-bit system it won't work properly. I'm planning to put together a thingy that installs the scanner drivers and provides some basic scanning functionality via scanimage through a gui. I'm amidst a million other things right now so you'll just have to wait a bit for it...

Until then, my advice is to run a 32-bit distro in VirtalBox. If you're into heavy scanning, you might think about switching your system to 32-bit...

Sorry I could not help you more right now.

Nope mine is 32 bit only :(. wats vittalbox (or virtualbox) ?

---

### Post by TariBuntu on 2010-11-08
> **adityachs said:**
> Nope mine is 32 bit only :(. wats vittalbox (or virtualbox) ?

Sorry, typo. I meant VirtualBox. :P It's, as the name implies, a virtual computer in a window - to put it briefly. You can install almost any operating system into any other, and simply start it in a contained safe environment. See [http://www.virtualbox.org ]("http://www.virtualbox.org") for detailed info.

I'm a bit lost when you say you're on 32-bit, because it simply SHOULD work in your case. My advice is to search the forum for similar behaviour, but don't insist on a Xerox. Perhaps someone solved your issue, but with a different scanner...

---

### Post by TariBuntu on 2010-11-10
I have crafted a tool for people like me, who have no access to Simple Scan/XSane, and are probably running a 64-bit Ubuntu.

Be gentle with your responses, it's still a work-in-progress, but better than nothing. :P

Download it from [www.tari.in]("http://www.tari.in")

Here are some screenshots:

[IMG]http://www.tari.in/menu.jpg[/IMG]

[IMG]http://www.tari.in/window.jpg[/IMG]

---

### Post by adityachs on 2010-11-16
Wow, its working...great...thanks boss......

As you said you still need to do some more work to make it to proper shape. Even though it is scanning, its taking lot of time and also it seems it struggling a lot :) any hows its working fine as of now.

Surprisingly my printer is not working. On the first day when i installed system recognised printer. When I installed drivers it worked fine.  But suddenly from 2nd or 3rd it stopped working...no error..simply ignores my prints :(....any help ?
(forgot to mention I am very new to Ubuntu/Linux)

Just now checked the cups page for pinting self test page it gives follwing error :
***Unable to send command to printer driver!***
  [INDENT]***Unsupported format 'application/vnd.cups-command'!***[/INDENT]

---

### Post by TariBuntu on 2010-11-16
> **adityachs said:**
> Wow, its working...great...thanks boss......

As you said you still need to do some more work to make it to proper shape. Even though it is scanning, its taking lot of time and also it seems it struggling a lot :) any hows its working fine as of now.

Surprisingly my printer is not working. On the first day when i installed system recognised printer. When I installed drivers it worked fine.  But suddenly from 2nd or 3rd it stopped working...no error..simply ignores my prints :(....any help ?
(forgot to mention I am very new to Ubuntu/Linux)

Just now checked the cups page for pinting self test page it gives follwing error :
***Unable to send command to printer driver!***
  [INDENT]***Unsupported format 'application/vnd.cups-command'!***[/INDENT]

Thank you for downloading and testing **adityachs**, the best reward for creating something is when others appreciate and use it. 

About your printer:

When I first installed the driver, I added the printer through **System/Administration/Printing**, and I had the same problem - no printing task was registered.

This is what worked for me:

Completely uninstalled the driver, reinstalled it, but this time added the printer through the browser (see my earlier step-by-step post). Since then it's working like a charm.

Anyone else with suggestions?

---

### Post by adityachs on 2010-11-17
> To install the 32-bit drivers from the cd, open "README_Ubuntu.htm" and  "Scanner Installation Guide_Ubuntu.htm" for step-by-step instructions.  Just read it and do what it says.

To start the install, just go to these folders, open a terminal and  start the files with sudo:  "XeroxPhaser3100-1.0-linux-2.6Ubuntu-intel/setup" and  "XeroxPhaser3100sc-1.0-linux-2.6Ubuntu-intel/setup"

Notes:

1. For this purpose, it's easier if you always choose the GUI step, rather than the terminal commands.
2. The cups server pages on your machine will look completely different  from that in the instruction, but you will find what you need (add  printer, configure printer, things like that)
3. Virtualbox: You do not need any special setting to scan in there.  Just make sure you use the full version which has USB support (see the  virtualbox website), and not Virtualbox OSE from the repositories.Is this what you are referring to ?

I tried to install thru GUi only. Just now tried using cups also cups is able to detect printer but same problem(ofcourse cups do not have 3100 drivers, so I chose some other model)

Plz help.

/Aditya

---

### Post by adityachs on 2010-11-17
Hey,

Some how I was able to add printer again. But not from CUPS page. Its seems there was a symbolic link libstdc++.so.5 at /usr/lib. I removed it..now its working after installation :)

---

### Post by khartahk on 2010-12-08
[This Xerox Scanning App]("http://tari.in") is working like a charm. Thank you very much :)

---

### Post by luissil on 2010-12-09
i get this msg when opening your app...:

> The following dependencies must be installed in order to use this application:

convert

The program will now close.i don't know how to install that dependence,,,,:?:

thank u for your help..;)

---

### Post by TariBuntu on 2010-12-10
> **luissil said:**
> i get this msg when opening your app...:

i don't know how to install that dependence,,,,:?:

thank u for your help..;)

"convert" is part of the ImageMagick package. Either install ImageMagick through Synaptic, or do this in terminal:

```
sudo apt-get install imagemagick
```

---

### Post by TariBuntu on 2010-12-14
Hi people,

I promised I would work on it, so here it is: selectable preview, plus a number of visible and less obvious changes/improvements.

The place is the same as before: [http://tari.in]("http://tari.in")

Have a nice day. :P

---

### Post by luissil on 2010-12-17
thank u very much, now works great!

---

### Post by Interruptor on 2011-01-20
Just installed it on a **10.04 x64 headless server** with command:
```
bash XeroxPhaser3100.install
```
(in extracted directory, drivers from Debian: [FONT="Times New Roman"]XeroxPhaser3100-1.0-linux-2.6Debian-intel.tar.gz[/FONT])
It was complaining about [FONT="Times New Roman"]/usr/lib/cups/filter/rastertoprinterbin[/FONT] is not-something.
So I just installed** ia32-libs**:
```
apt-get install ia32-libs
```
and now printer works fine, local and through samba.

---

### Post by Interruptor on 2011-01-20
Just installed it on a **10.04 x64 headless server** with command:
```
bash XeroxPhaser3100.install
```
(in extracted directory, drivers from Debian: [FONT="Times New Roman"]XeroxPhaser3100-1.0-linux-2.6Debian-intel.tar.gz[/FONT])
It was complaining about [FONT="Times New Roman"]/usr/lib/cups/filter/rastertoprinterbin[/FONT] is not-something.
So I just installed** ia32-libs**:
```
apt-get install ia32-libs
```
and now printer works fine, local and through samba.

---

### Post by Interruptor on 2011-01-20
Just installed it on a **10.04 x64 headless server** with command:
```
# bash XeroxPhaser3100.install
```
(in extracted directory, drivers from Debian: [FONT="Times New Roman"]XeroxPhaser3100-1.0-linux-2.6Debian-intel.tar.gz[/FONT])
It was complaining about [FONT="Times New Roman"]/usr/lib/cups/filter/rastertoprinterbin[/FONT] is not-something.
So I just installed** ia32-libs**:
```
# apt-get install ia32-libs
...
[I]Need to get 39.8MB of archives.
After this operation, **164MB** of additional disk space will be used.[/I]
```
and now printer works fine.

---

### Post by Interruptor on 2011-01-20
Just installed it on a **10.04 x64 headless server** with command:
```
# bash XeroxPhaser3100.install
```
(in extracted directory, drivers from Debian: [FONT="Times New Roman"]XeroxPhaser3100-1.0-linux-2.6Debian-intel.tar.gz[/FONT])
It was complaining about [FONT="Times New Roman"]/usr/lib/cups/filter/rastertoprinterbin[/FONT] is not-something.
So I just installed** ia32-libs**:
```
# apt-get install ia32-libs
...
[I]Need to get 39.8MB of archives.
After this operation, **164MB** of additional disk space will be used.[/I]
```
and now printer works fine.

---

### Post by Interruptor on 2011-01-20
Just installed it on a **10.04 x64 headless server** with command:
```
# bash XeroxPhaser3100.install
```
(in extracted directory, drivers from Debian: [FONT="Times New Roman"]XeroxPhaser3100-1.0-linux-2.6Debian-intel.tar.gz[/FONT])
It was complaining about [FONT="Times New Roman"]/usr/lib/cups/filter/rastertoprinterbin[/FONT] is not-something.
So I just installed** ia32-libs**:
```
# apt-get install ia32-libs
...
[I]Need to get 39.8MB of archives.
After this operation, **164MB** of additional disk space will be used.[/I]
```
and now printer works fine.

---

### Post by luissil on 2011-01-28
something happened with the app...

i really don't know since when, but, stopped working, i only can get the preview, but when i click "scan" the status bar moves from a side to another for a few seconds, and then stops, but there's no image scanned...

---

### Post by TariBuntu on 2011-02-04
> **luissil said:**
> something happened with the app...

i really don't know since when, but, stopped working, i only can get the preview, but when i click "scan" the status bar moves from a side to another for a few seconds, and then stops, but there's no image scanned...
Corrected. I advise everyone who use it to [download]("http://tari.in") the new version - there was a bug in the previous one. We killed it.

---

### Post by luissil on 2011-02-04
> **TariBuntu said:**
> Corrected. I advise everyone who use it to [download]("http://tari.in") the new version - there was a bug in the previous one. We killed it.
yeah! works great again!
and thanks for the thanks! lol!

---

### Post by TariBuntu on 2011-05-05
Hello friends,

Since they have shuffled some system files around in 11.04, the old versions of the app will not work if you switch to the Narwhal. [Get the updated app]("http://tari.in") in this case.

If you are not using 11.04, don't bother downloading - not much has been changed.

Have a nice day. :D

---

### Post by luissil on 2011-06-15
> **TariBuntu said:**
> Hello friends,

Since they have shuffled some system files around in 11.04, the old versions of the app will not work if you switch to the Narwhal. [Get the updated app]("http://tari.in") in this case.

If you are not using 11.04, don't bother downloading - not much has been changed.

Have a nice day. :D


mmm i think something is wrong, i update an got this:

No Xerox scanner could be found. The application will now close.

---

### Post by luissil on 2011-06-15
SOLVED. thanks to [TariBuntu]("http://ubuntuforums.org/member.php?u=520431")

---

### Post by mi6ail1234 on 2011-07-09
> **luissil said:**
> mmm i think something is wrong, i update an got this:

No Xerox scanner could be found. The application will now close.
Can you explane in details.I have receive the same message?

---

### Post by luissil on 2011-07-09
> **mi6ail1234 said:**
> Can you explane in details.I have receive the same message?

Well, there was a problem with the driveres, I've noticed that each time Ubuntu upgrades the drivers stop working or something like that, in my case, i just re-install the driveres from the Xerox page, and done, working again.

---

### Post by TariBuntu on 2011-07-09
> **mi6ail1234 said:**
> Can you explane in details.I have receive the same message?

luissil is right. This app is not a substitute for the Xerox driver package, only an alternative to x(sane).

You need to download and install the scanner drivers (the Ubuntu batch) from Xerox. They have a very usable step-by-step HTML HOWTO in the package, so it should not be a problem.

---

### Post by mi6ail1234 on 2011-07-11
I've download scan drivers from official Xerox website,but i can't find step-by-step guide?

---

### Post by TariBuntu on 2011-07-12
> **mi6ail1234 said:**
> I've download scan drivers from official Xerox website,but i can't find step-by-step guide?

I've uploaded the full printer+scanner driver package along with the manuals [here]("http://tari.in/downloads/Xerox Phaser 3100MFP.7z"). These are from the original Xerox CD that came with my MFP.

Hope it helps.

---

### Post by mi6ail1234 on 2011-07-12
Thank you very much.I have a successful installed drivers and everything is working even i shared my printer so my parents can use that printer from their Windows computer.

---

### Post by TariBuntu on 2011-07-14
Hello friends,

I've had a feature request, so here you are: custom file names.
Same [place]("https://tari.in/www/eng/software/xeroxscannerutility/") as before.

Have a nice day. :P

---

### Post by tharpa on 2011-09-17
Reread thread.

---

### Post by TariBuntu on 2011-10-23
Hello friends,

Welcome to the wonderful world of 11.10's Unity + Gnome 3 + no-gnome-classsic + nothing-works-anymore!

This time I'll start with a question: Has anybody had success with making the printer work in 64-bit Ocelot?

(I'm NOT writing a CUPS replacement! :))

---

### Post by TariBuntu on 2011-10-26
> **TariBuntu said:**
> Hello friends,

Welcome to the wonderful world of 11.10's Unity + Gnome 3 + no-gnome-classsic + nothing-works-anymore!

This time I'll start with a question: Has anybody had success with making the printer work in 64-bit Ocelot?

(I'm NOT writing a CUPS replacement! :))

I had my CUPS updated today, and printing is back in 64-bit (with the original Xerox drivers, of course). Viva Ubuntu!

---

### Post by khartahk on 2012-01-08
> **TariBuntu said:**
> Hello friends,

I've had a feature request, so here you are: custom file names.
Same [place]("https://tari.in/www/eng/software/xeroxscannerutility/") as before.

Have a nice day. :P
Hi

the link provided in your post does not work any more. Can you check your site or post an alternative.

Thank you

---

### Post by TariBuntu on 2012-01-08
> **khartahk said:**
> Hi

the link provided in your post does not work any more. Can you check your site or post an alternative.

Thank you

I am really sorry people, GoDaddy(need I say more?) has messed up something with the server so I've temporarily taken down the site - hoping that nobody would miss me.

Here is a [_direct link_]("http://tari.in/XeroxScanner-1.22.zip") for now, I hope they fix their issues soon.

---

### Post by khartahk on 2012-01-10
Thanks again. 

I had do manualy scann from the cli in oneiric :). 
I need to save this to a safe place now.

---

### Post by Juanderboy on 2012-05-24
> **TariBuntu said:**
> I am really sorry people, GoDaddy(need I say more?) has messed up something with the server so I've temporarily taken down the site - hoping that nobody would miss me.

Here is a [_direct link_]("http://tari.in/XeroxScanner-1.22.zip") for now, I hope they fix their issues soon.
TariBuntu

How can I uninstall this to my PC. It's not working to my 32 bit so I want to uninstall it. BTW nice job.

---

### Post by TariBuntu on 2012-05-24
> **Juanderboy said:**
> TariBuntu

How can I uninstall this to my PC. It's not working to my 32 bit so I want to uninstall it. BTW nice job.

It should work on both 32 and 64bit, but you must install all the required stuff first. Please see the download page for the App on my site for details.

If you need help with it, just email me or write me on google talk - I am always happy to assist.

If you've really decided to remove it, run this from terminal:

```
sudo rm '/usr/bin/XeroxScanner' '/usr/share/XeroxScanner/XeroxScanner.png' '/usr/share/XeroxScanner/XeroxScanner.xml' '/usr/share/applications/XeroxScanner.desktop'
```

---

### Post by luissil on 2012-06-07
Another issue with the printer...

I've just made a clean upgrade and now this is the error:

```
luis@luis-despacho:~/Desktop$ sudo ./setup
``````
./setup: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory

```

---

### Post by TariBuntu on 2012-06-07
> **luissil said:**
> Another issue with the printer...

I've just made a clean upgrade and now this is the error:

```
luis@luis-despacho:~/Desktop$ sudo ./setup
``````
./setup: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory

```

This is the first time I'm seeing this - the drivers always install without problems. :confused:

You can try to find if synaptic has what the installer wants (I've looked and there is a ***libpng12-0***). Try to install that one.

---

### Post by luissil on 2012-06-08
> **TariBuntu said:**
> This is the first time I'm seeing this - the drivers always install without problems. :confused:

You can try to find if synaptic has what the installer wants (I've looked and there is a ***libpng12-0***). Try to install that one.


bad  luck:

```
luis@luis-despacho:~$ sudo apt-get install libpng12-0
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpng12-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

``````
luis@luis-despacho:~$ sudo apt-get install ia-32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia-32-libs

```

---

### Post by TariBuntu on 2012-06-08
> **luissil said:**
> bad  luck:

```
luis@luis-despacho:~$ sudo apt-get install libpng12-0
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpng12-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

``````
luis@luis-despacho:~$ sudo apt-get install ia-32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia-32-libs

```

That should be "ia32-libs"

---

### Post by TariBuntu on 2012-11-14
Hello friends,

I've made some major modifications (no more root password!), plus the project is now on Launcpad, which makes it very easy to install and get updates automatically.

Scanner and Printer both tested and work on 32 and 64bit versions of Precise and Quantal (and probably future versions).

1. You need to install the [Xerox drivers]("https://tari.in/downloads/Xerox%20Phaser%203100MFP.7z") first.

2. In Terminal:
```
sudo add-apt-repository ppa:robert-tari/xerox
sudo apt-get -q update
sudo apt-get install xeroxscanner
```

3. Log out or restart

The project page is the [same as before]("https://tari.in/www/eng/software/xeroxscannerutility/").

Have a nice day.

---

### Post by TariBuntu on 2012-11-30
EDIT: You don't need to install the drivers anymore. The installer will configure everything for you.

Just paste these into the Terminal:
```
sudo add-apt-repository ppa:robert-tari/xerox
sudo apt-get -q update
sudo apt-get install xeroxscanner
```
Now restart, then (unplug and) plug in the USB cable

---

### Post by yolandasala on 2012-12-26
Hey hey I've got the latest Ubuntu version and a Xerox Phaser 3100 which seems to be perfectly installed (with the drivers it found itself), but whenever I try to print anything, even test prints it behaves as though it is printing: it makes the "starting to print noise" and no error messages pop-up however it stops there, and never does print.  I would have though it is a problem with the printer, however it does work perfectly when I try it with windows.  Any ideas?
cheers!

---

### Post by TariBuntu on 2012-12-26
> **yolandasala said:**
> Hey hey I've got the latest Ubuntu version and a Xerox Phaser 3100 which seems to be perfectly installed (with the drivers it found itself), but whenever I try to print anything, even test prints it behaves as though it is printing: it makes the "starting to print noise" and no error messages pop-up however it stops there, and never does print.  I would have though it is a problem with the printer, however it does work perfectly when I try it with windows.  Any ideas?
cheers!

Welcome to the forums yolandasala.

You haven't told us what your architecture is (32bit or 64bit) and whether you have installed **xeroxscanner** from the ppa mentioned above.

Whatever your system has found "on its own" will not make the printer work properly.

---

### Post by kwstas on 2013-08-09
i had the exact same problems with "yolandasala" and after i installed the app of "taribuntu" i can finally print! haven't tried the scanner yet...
just to note, the first "test page" printed fine but when i tried to print an actual document, it couldn't print so i checked in options and changed from US LETTER to A4 and printed fine.
many many thanks!

---

