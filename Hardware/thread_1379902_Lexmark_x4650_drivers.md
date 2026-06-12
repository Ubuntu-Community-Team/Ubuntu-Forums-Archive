---
title: "Lexmark x4650 drivers"
date: 2010-01-13
forum: Hardware
---

### Post by Godspell on 2010-01-13
Hi there,

I'm using Ubuntu 9.1 64-bit on Acer Aspire 5542. Everything has been fine apart from this printer issue.

Being an Ubuntu noob doesn't help either, I suppose, as I don't know if I should use existing available drivers instead.

When I connected the printer with USB cable, the window popped up asking me which drivers I wanna install. There were loads but nothing close to my series of Lexmark x4650.

Any ideas on how to get round this? Your suggestions would be greatly appreciated :D
Thank you very much.

Regards,
GS

---

### Post by Cheesemill on 2010-01-13
The x4650 is classed as a paperweight meaning you'll never get it to work.
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X4650](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X4650)

Lexmark are renowned for making printers that are completely incompatible with Linux.

---

### Post by Godspell on 2010-01-13
:S that really is a bad news lol
Well, at least I know something now. Thanks anyway :)

Regards.

---

### Post by imazman on 2010-02-21
Shoot...I just paid $50 for a Lexmark paperweight but the pulsating power light works :)   I strongly suggest linux users stay away from Lexmark.  By previous HP worked great with linux...I guess I will have to go out an buy an HP tomorrow.

Zman

---

### Post by ahillsbe on 2010-03-09
Here is a [link]("http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US+&locale=en&oslocale=en_US") for the lexmark driver. I have succesfuly printed over the network via wifi on opensuse. Not a paperweight!

EDIT:

I just got this working in Ubuntu 9.10 x86. 

use "AppSocket/HP JetDirect" under network printer in the "new printer" menu.  Host is printer IP address leave port number at 9100.  It will ask for printer manufacturer and model for driver.  If you successfully installed the lexmark drivers from the download you should be able to find the 3600-4600 printer driver. 

Hope this helps.

---

### Post by wordini on 2010-03-14
Just figured this out myself and I am not very good with running the terminal... I was making it way to hard.  All you have to do is go to the link*** ahillsbe*** gave, download to your desktop, extract to desktop then double click it (in Karmic) When it asks for your root password give it if you know it ( i didn't but I found a place online that told how to change it) They said it was dangerous to log in or anything under the root administrator but i just changed the password and nothing else in the terminal with

 **$sudo passwd root**   

after that the lexmark  proceeded to load everything else no problem.  I did have to set it as the default printer in the system/printing menu and restart but it seems to be working perfectly hooked up via USB.

 Hope this helps!

---

### Post by Godspell on 2010-03-21
Both **Wordini** and **Ahillsbe** thank you very much for your help. Those drivers work like a charm. I've just printed out some pages for my project. I'm using the printer with usb cable on Karmic.
Wouldn't have known this if it wasn't for you two. Sorry for my late reply I thought this issue can't be resolved and ignored the thread.
Now I'm gonna prefixed this to SOLVED. Special thanks to you two. Cheers

Regards,
GS

---

### Post by sites on 2010-03-30
> **ahillsbe said:**
> Here is a [link]("http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US+&locale=en&oslocale=en_US") If you successfully installed the lexmark drivers from the download you should be able to find the 3600-4600 printer driver. 


Sorry but this isn't solved for me.  Upon driver installation i keep getting an Lua error saying there's not enough space for the widget.

Any ideas?

---

### Post by wordini on 2010-04-14
hey sites, not sure if you figured it out yet but i just did a fresh 10.04 install and it worked (again)like a dream with the same method described above... make sure you do the install as simple as possible, everything closed, printer unplugged... then extract and run. it should work.. if you plug the printer in *before* hand, the new install  tries to find it but it just *doesn't* work:)

---

### Post by dog_biscuits on 2010-05-03
Thanks,  Just followed these instructions and everything's working.  My wife isn't so smug with her windows laptop now...

---

### Post by jessecohn on 2010-05-03
I was having a hell of a time getting my Lexmark 4650 installed and working -- the instructions above helped greatly, thanks! -- and then I couldn't for the life of me get it to print wirelessly (I had had no problem doing this when my laptop was still on Windows).  The sticking point turned out to be figuring out how to determine the IP address of the printer correctly -- NOT the same thing, it seems, as the IP address of our router.  This page at Lexmark ([http://support.lexmark.com/index?page=content&id=HO3375&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=content&id=HO3375&locale=EN&userlocale=EN_US)) helped.  It was actually very simple: the printer itself, if you press the right buttons ("Setup," then select "Network Setup" and keep telling it "OK"), prints out a sheet divulging its IP address.

Whew!

Surely, though, there's got to be an easier way.  I wonder if somebody's got a nice app to determine what's connected to your wireless network (and, say, to control the router -- set password protection, etc.).

---

### Post by sites on 2010-05-28
No i have not figured it out.  I'm back at my friend's trying to get this printer to work over the wireless network.  Still getting the "not enough space for widget" error.  Doesn't matter if i install via terminal as root, or by executing the file from nautilus.  I might try to upgrade to 10.04 as a last resort.  This is driving me nuts.

It wouldn't be an issue if the HP LJ3015 would print his pages from the SunTrust site properly, but it spits out pages of lines and empty boxes.

EDIT:  Problem solved after following instructions in the following post.  [http://ubuntuforums.org/showpost.php?p=7777070&postcount=6]("http://ubuntuforums.org/showpost.php?p=7777070&postcount=6")

---

### Post by fire.for.effect on 2010-07-12
Let me be the guy who asks why after running it (the Lexmark driver), I get a message that says my root password entered is incorrect when I am without doubt that it's correct.

Any takers?

Thanks in advance.

---

### Post by willyboy666 on 2010-08-08
> **fire.for.effect said:**
> Let me be the guy who asks why after running it (the Lexmark driver), I get a message that says my root password entered is incorrect when I am without doubt that it's correct.

Any takers?

Thanks in advance.
Same here
any help

---

### Post by bedwards2000 on 2010-09-03
Finally!

I've been trying to get my Lexmark X4650 printer working with Ubuntu since I switched to Linux early last year.

I just followed the instructions outlined in this thread and it now works both connected and wireless.  I did, however, need to make a small adjustment on how I installed the driver that gets downloaded.  After extracting the driver I had to run the executable out of the terminal using sudo otherwise just double clicking it to run it and entering the pwd failed every time.

Nice job fellas.  Not just a paperweight anymore.

Thanks a ton

---

### Post by izzysdaddy on 2010-09-19
> **willyboy666 said:**
> Same here
any help

Only three of us have this problem? I KNOW my password. Is the root password different from my startup login? I'm an eager noob, but have been working with Windoze since 5.1... doesn't seem that long ago.
Anyway, I finally got my wireless to work on my Samsung N130, and wanted to print to our new Lexmark X4650, wirelessly, since I see a couple of posts suggesting success at this.

Any Help will be much appreciated!

---

### Post by bedwards2000 on 2010-09-19
The root pwd is the same as the login if you are the administrator of your system.  I had the same problem with the pwd error at first when I tried installing the driver by just double clicking it and having it install that way.  I have no idea why that error occurs, but I was able to get around it by using the command line to install the driver.

---

### Post by Godspell on 2010-12-08
The drivers from the above link worked perfect with 32bit Ubuntu but NOT AT ALL on 64.

I'm using Ubuntu 10.04 64bit and the drivers were installed well. No errors whatsoever was found but they just won't work.

Does anybody know how to configure? Is there a 64bit version of this drivers???
Please let me know.

Many thanks and regards,
GS

---

### Post by Godspell on 2010-12-15
The printer started to work itself without any fix being applied which is great BUT there's NO duplex option available.

I can duplex manually like printing out odd numbered pages and put them back in the printer afterwards but it's annoying, time-consuming and not at all the way forward. 

Another thing is, I don't think print preferences can be saved in a profile (like you can on Windows) either.

With these issues at hand, I think it's safe to say the printer does NOT entirely work.

So, any ideas folks? If you've got any magic tricks that can ease my pain, hit me up here :)

Many thanks and regards,
GS

---

### Post by cca02143 on 2010-12-17
Cheers cheers to ahillsbe and wordini!  Got my x4650 working via wifi and usb now.  I no longer need to use my wife's computer to print stuff -- love it.

---

### Post by Godspell on 2010-12-17
> **cca02143 said:**
> Cheers cheers to ahillsbe and wordini!  Got my x4650 working via wifi and usb now.  I no longer need to use my wife's computer to print stuff -- love it.

You can't do duplex either, can you?

It's really frustrating for me :S

---

### Post by wordini on 2011-02-11
Godspell, I don't think the x4650 has duplex capabilities... Could be why it's not working. ??

---

### Post by Godspell on 2011-02-11
> **wordini said:**
> Godspell, I don't think the x4650 has duplex capabilities... Could be why it's not working. ??

You're right. It's got no duplex and other printer options.

Frankly speaking, the drivers are not at all suitable for those who wish to do everyday eco printing i.e. draft quality, duplex, grayscale, etc.

I don't think Lexmark make comprehensive drivers for Ubuntu like they do for Windows which is a big shame.

Meh...what can you do, eh?

---

### Post by charlieluna on 2011-02-20
> **ahillsbe said:**
> Here is a [link]("http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US+&locale=en&oslocale=en_US") for the lexmark driver. I have succesfuly printed over the network via wifi on opensuse. Not a paperweight!

EDIT:

I just got this working in Ubuntu 9.10 x86. 

use "AppSocket/HP JetDirect" under network printer in the "new printer" menu.  Host is printer IP address leave port number at 9100.  It will ask for printer manufacturer and model for driver.  If you successfully installed the lexmark drivers from the download you should be able to find the 3600-4600 printer driver. 

Hope this helps.

i'm trying to get my x4650 to print wirelessly. i have the driver successfully installed and everything, it just won't print wirelessly. i've tried what you recommended to the other person but i can't seem to figure out what to do. i'm a noob as well.

---

### Post by Godspell on 2011-02-20
I'm probably not being helpful but I tried what that gentleman suggested and it never worked for me.

Truth be told, these drivers aren't as comprehensive as the ones that are available on Windows (a lot of people wouldn't like to hear this). They don't do duplex, colour control, customised printer profile and so on.

I started this thread with intention to make my printer works on Ubuntu and it did, BIG thanks to people who contributed the solution but at the end, I end up going back on Windows for printing.
The services these drivers provide are simply not good enough for everday printing.

I don't believe Lexmark support Linux that much :S

Anyway, sorry to cut in like this.
I'm sure somebody will get back to you on your question :)

Cheers and regards,
GS

---

### Post by sateal8 on 2011-03-31
> **bedwards2000 said:**
> Finally!

I've been trying to get my Lexmark X4650 printer working with Ubuntu since I switched to Linux early last year.

I just followed the instructions outlined in this thread and it now works both connected and wireless.  I did, however, need to make a small adjustment on how I installed the driver that gets downloaded.  After extracting the driver I had to run the executable out of the terminal using sudo otherwise just double clicking it to run it and entering the pwd failed every time.

Nice job fellas.  Not just a paperweight anymore.

Thanks a ton

So sorry to ask but what command did you type into the terminal to get it to install? I cannot get it to install without telling me my password is invalid.

---

### Post by bedwards2000 on 2011-03-31
I just ran the executable from the command line.

sudo lexmark-08z-series-driver-1.0-1.i386.deb.sh

and that did the trick for me as far as getting the driver installed

---

### Post by Eugezilla on 2011-06-09
Thanks for all the good information.  One question, what does it mean to double click the file, "in Karmic?"

---

### Post by Eugezilla on 2011-06-10
I tried saving it to the desktop and double clicking it but received this error message:

[FONT=monospace]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.


I also opened the terminal and entered the command listed above but was told "command not found"[/FONT]


Any suggestions?

---

### Post by pnhearer on 2011-08-27
> **Eugezilla said:**
> I tried saving it to the desktop and double clicking it but received this error message:

[FONT=monospace]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.


I also opened the terminal and entered the command listed above but was told "command not found"[/FONT]


Any suggestions?

Have you gone into the file properties and set the executable bit?

and person above asking about in Karmic. That is the alias for that particular version of Ubuntu.

---

### Post by feralfinds on 2012-03-18
i'd like to install the lexmark X4650 printer, i'm running ubuntu 11.04.

is there a thread or site that would explain this process, step-by-step
to a new person? 

i found the lexmark page with the driver link....

thanks! jennifer

---

### Post by Godspell on 2012-03-22
> **feralfinds said:**
> i'd like to install the lexmark X4650 printer, i'm running ubuntu 11.04.

is there a thread or site that would explain this process, step-by-step
to a new person? 

i found the lexmark page with the driver link....

thanks! jennifer

Hello,

The following link is from post #8, Page-1.

[http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US+&locale=en&oslocale=en_US](http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US+&locale=en&oslocale=en_US)

If you click it, you'll be re-directed to a Lexmark page and asked to download a file.
As far as I remember, you just need to double-click it (like an .exe on Windows) and it'll guide you through the installation.

However, there are some issues with this drivers package.

1. It's meant to be for a 32-bit Linux.
I have tested it on both Karmic and Lucid 64-bit back then and it worked BUT only after some tweaking and several restarts. So, it's best ONLY when you're on 32-bit.

2. These are basic drivers i.e. you don't have comprehensive printing support like duplex, detailed page adjustments, etc. The things that you'd normally have on Windows.
(I have posted this issue somewhere in this thread before but don't think there was any solution-reply.)

3. These drivers don't support wireless printing. So, you'll be forced to use a USB cable. Like I said, they're pretty basic.

All in all, leave this driver package for the last resort.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Having told you how NOT great the above drivers are, I also searched for latest X4650 Linux drivers on Lexmark website. Found the following. Unfortunately, they're also mainly for the 32-bit Linux. (Don't know what's up with this.)

[http://support.lexmark.com/index?docLocale=en_US&page=content&segType=recommendedSegmentLINUX_UNIX&id=DR20523&locale=EN&userlocale=EN_UK](http://support.lexmark.com/index?docLocale=en_US&page=content&segType=recommendedSegmentLINUX_UNIX&id=DR20523&locale=EN&userlocale=EN_UK)


You said you've also found a Lexmark page with a driver link. So, could it be the above? If so, there are installation guidelines on the page. Try'em out. They shouldn't be complicated. Although, let us know when you get stuck :)

Next time you post, please state what version of Ubuntu you're using. So that we get a better idea of your problem.

From my experience, and I'm NO expert, I was never able  to get my X4650 working as good as it does on Windows. Simply because they don't do good-enough drivers for Linux, I guess. So, it maybe wise to have Ubuntu dual-boot with Windows :)
Solely my opinion.

Hope this somewhat helps.

Best wishes.

---

### Post by Hack.The.Pow. on 2012-06-04
I'm running 12.04 64 bit and can't seem to get this working.  When I was on 10.10 I just used the same driver and installed libstdc++5 and everything worked fine.  Now not so much.

Can anybody help?

---

### Post by isaac12345 on 2012-06-05
I've been trying to set it up on 12.10 32bit and have been getting problems installing the driver. If I go through the route of double clicking the .sh file, the installer doesnt let me go past the root password page even though I am pretty sure I am entering the correct password. The current user is set as the administrator and I am entering that password. Then I tried the "Run through terminal" option but it simply executes through the terminal and then takes me to the GUI installer and I get stuck again at the root password stage.
I tried sudo lexmark-08z-series-driver-1.0-1.i386.deb, entered my password and it says that the command is not found. I cant quite figure out what the problem is. Any help would be appreciated.

---

### Post by Hack.The.Pow. on 2012-06-05
> **isaac12345 said:**
> I've been trying to set it up on 12.10 32bit and have been getting problems installing the driver. If I go through the route of double clicking the .sh file, the installer doesnt let me go past the root password page even though I am pretty sure I am entering the correct password. The current user is set as the administrator and I am entering that password. Then I tried the "Run through terminal" option but it simply executes through the terminal and then takes me to the GUI installer and I get stuck again at the root password stage.
I tried sudo lexmark-08z-series-driver-1.0-1.i386.deb, entered my password and it says that the command is not found. I cant quite figure out what the problem is. Any help would be appreciated.

how did you extract the .deb file out of the .deb.sh?  Maybe i can try and force architecture with dpkg

---

### Post by kev77 on 2012-06-20
I can confirm I have Lexmark x4650 working on ubuntu 12.04 



```
sudo apt-get install ia32-libs xz-lzma
wget http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz -O lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
tar xzvf lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark
cd lexmark
tar xJvf instarchive_all
dpkg-deb -I lexmark-08z-series-driver-1.0-1.i386.deb
mkdir raw-lexmark-archive
dpkg-deb --raw-extract lexmark-08z-series-driver-1.0-1.i386.deb raw-lexmark-archive
sed -i "/^ $/d" raw-lexmark-archive/DEBIAN/control
cat raw-lexmark-archive/DEBIAN/control
dpkg-deb -b ./raw-lexmark-archive fixed-lexmark-08z-series-driver-1.0-1.i386.deb
sudo dpkg -i fixed-lexmark-08z-series-driver-1.0-1.i386.deb
```


Many thanks to thread #2 on askUbuntu, [http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise]("http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise")

---

### Post by jpeg729 on 2012-07-19
Got it working on wifi. A piece of cake really, at least for the printer part of it. No idea how to get the scanner working.

I had to boot into windows to use the printer utility to configure the printer's wifi connection. If your wifi router has a button to allow things to connect automatically, use that instead.

You will need to make sure the router always gives the printer the same ip address. Or you can just try your luck and when it stops working that will probably be the problem. See below for how to check the ip address of the printer.

You will also need to get the lexmark drivers and extract the files from them. No need to install them as shown above.
```
wget http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.t in windows though, otherwise I couldn't get the printer to connect to the wifi networkar.gz -O lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
tar xzvf lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark
cd lexmark
tar xJvf instarchive_all
dpkg-deb -I lexmark-08z-series-driver-1.0-1.i386.deb
mkdir raw-lexmark-archive
dpkg-deb --raw-extract lexmark-08z-series-driver-1.0-1.i386.deb raw-lexmark-archive
```

Next load up the CUPS config page  in a web browser [http://localhost:631/]("http://localhost:631/") and add a new printer.

Choose "AppSocket/HP JetDirect" as the printer type.

It will ask you where it can find the printer. Type this into the box.
```
socket://ip-address-of-your-printer:9100
```

(To find the ip address of your printer, press the spanner button on the printer, then choose Network configuration -> TCP/IP -> Show IP address.)

On the next page give the printer a name.

On the next page choose to give it a ppd file. And look in the unpacked deb file for the following file:
```
raw-lexmark-archive/usr/local/lexmark/08zero/etc/lx36-46.ppd
```

Then choose your default print options.

Now you can close that web page and look in the printer setup. It will be there. Try a test page and enjoy. :)

---

### Post by jpeg729 on 2012-08-23
Can't see how to edit my post again.

In fact you do have to install the driver just as kev77 does.

And if you are running a 64bit version of linux you will also need to install libcupsimage2:i386
> sudo apt-get install libcupsimage2:i386

I discovered that because it stopped working a day or two ago, so I tried all sorts of things before finding out why.

The ppd file designates a custom filter 
> /usr/lexinkjet/08zero/bin/printdriver
I tried running it on the commandline and it said
> /usr/lexinkjet/08zero/bin/printdriver: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory
libcupsimage2 **was** installed, so I figured it needed the i386 version, and it works now.

---

### Post by digimark on 2012-11-19
HI Everyone,

Tried all of the above. Running 12.04 . None of these work (yes even the step by step instructions in terminal!)....the error I get is

============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz5333/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****


Please acn anone advise.....

For the record when this printer dies i wnt be buyinganother lexmark.....what a nightmare!

---

### Post by digimark on 2012-11-19
HA! sorted it. Installed now and can be seen across WiFi BUT....it wont print.....the CUPS page sees an error...

&#9660; Queue Name &#9660;	Description	Location	Make and Model	S[B][COLOR="Red"]tatus
Lexmark_4650	wireless	Sues_Office	Lexmark 3600-4600 Series, 1.0	Idle - "File "/usr/lexinkjet/08zero/bin/printdriver" not available: No such file or directory"

Any ideas??? also in the printer view the printer shows with a big red exclamation mark on it......

ANy idea welcome!

Many thanks all......

---

### Post by digimark on 2012-11-19
OK so managed to edit the PDD file to point to the right place for the prindriver link. HOWEVER I now get

Idle - File "/home/mark/lexmark/raw-lexmark-archive/usr/local/lexmark/08zero/bin/printdriver" has insecure permissions (0100555/uid=1000/gid=1000).

I have chmod the file to br r-x r-x r-x and reinstalled the printer to no effect.....

Now I really am out of ideas.....

Thanks chaps.....

---

### Post by vincentvega2 on 2013-03-11
i know this thread is old but im unable to execute the --raw-extract option in dpkg-deb. its not a valid switch for me. any ideas on how to either add the option or work around not having it?

---

### Post by kylemoo on 2013-12-05
> **vincentvega2 said:**
> i know this thread is old but im unable to execute the --raw-extract option in dpkg-deb. its not a valid switch for me. any ideas on how to either add the option or work around not having it?

I just followed the instructions listed on page 4 and they worked for me with 13.10 64 bit install on an old HP 8510p laptop and a lexmark x4650 printer connected to wifi.  I printed test page wireless no problem.  Going to see if I can get it to scan now.  I have 7zip installed on my machine, do you have a zip extractor installed?

---

### Post by kylemoo on 2013-12-05
> **vincentvega2 said:**
> i know this thread is old but im unable to execute the --raw-extract option in dpkg-deb. its not a valid switch for me. any ideas on how to either add the option or work around not having it?


to clarify I did not use the cups method mentioned.  I just went into the printers program and added the printer in the same manner shown for the cups website.  I got the ip address in the host field and kept 9100 as the port, then selected the dpp location shown in the post and found it in the file location as shown the posts previous shows looking in bin but it is actually in /etc as shown on page 4 unless you extracted or installed the package to another location.  Hope this helps, also I am available on google helpouts if anyone wants help with this.  Search CAD and I am one of the first to pop up.

---

### Post by kylemoo on 2013-12-05
> **digimark said:**
> OK so managed to edit the PDD file to point to the right place for the prindriver link. HOWEVER I now get

Idle - File "/home/mark/lexmark/raw-lexmark-archive/usr/local/lexmark/08zero/bin/printdriver" has insecure permissions (0100555/uid=1000/gid=1000).

I have chmod the file to br r-x r-x r-x and reinstalled the printer to no effect.....

Now I really am out of ideas.....

Thanks chaps.....


Looks like you need to look in the following file location, just look to that directory using the printers program

raw-lexmark-archive/usr/local/lexmark/08zero/etc/lx36-46.ppd

---

