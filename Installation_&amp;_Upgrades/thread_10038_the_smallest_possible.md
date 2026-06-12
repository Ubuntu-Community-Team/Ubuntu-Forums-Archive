---
title: "the smallest possible"
date: 2005-01-04
forum: Installation &amp; Upgrades
---

### Post by edemark on 2005-01-04
Hi everybody 

I have recently installed ubuntu Warty Warthog on an old  machine (PI 150, 84M Ram 2G hdd). 
First I have to say that ubuntu worked perfectly during installation (though it was awfully slow, I guess as this computer is slow). And since than I am able to use everithing I need. 
However I have one big problem. After instalation only 200 M of free space is avaliable on my computer so I was thinking what programs could I remove safely from the machine?
I would like to keep the following programs Opn Office, Evolution, Firefox, Gnome and GDM but I am not doing anything else on this computer than browse the web, access my  e-mail and working with documents and tables. 
Any suggestions? Apache? MySQL?

Please help gathering other 5-600 Mb of free space

thanks

---

### Post by ensiferum on 2005-01-04
Ditch gnome, install fluxbox. Should get you plenty of free space.

---

### Post by feneks on 2005-01-04
Ubuntu seems to install programs which can't be needed at old computers.

*sudo apt-get --purge remove program*

acpi and acpid : powermanagement which isn't supported at your computer
powernowd : cpu scaling which doesn't work with PI
mdadm and mdadm-raid : mangages multipledisk devices like RAID
ppp and ppp-dns : [COLOR=Red]ATTENTION[/COLOR] only if you aren't using any kind of modem (DSL modem included)




These programs can be disabled too if you don't want to use them.

xsane and sane : program to use scanner
gaim : instant messaging client
gnomemeeting : voice over IP, telephone per internet
xchat : IRC 
totem : media player (videos)
sound-juicer : mp3 ripper
rhythmbox : music player
gnome-games : games - what else
gimp : adobe photoshop clone

hopefully this will help

---

### Post by edemark on 2005-01-04
[QUOTE=ensiferum]Ditch gnome, install fluxbox. Should get you plenty of free space.[/QUOTE]
 Hi ensiferum

First thanks for the quick reply. Actually I am using windowmaker as this is a slow computer however I have a fear with removing gnome. As this distro is based on gnome i do not know how to make system wide set up without it. So if there was any other prog, which could be removed I would like to keep gnome for this sole reason

---

### Post by feneks on 2005-01-04
cdrecord : burns CDROMs
gnome-sound-recorder
cupsys : printer server
cupsys-client : printer client
xpp : delete only if you aren't using cups / printer
foomatic-db: delet only if you aren't using cups / printer
hpijs : driver for hp inkjets
hpoj : driver for hp officejets

---

### Post by feneks on 2005-01-04
If you don't want to connect to Windows computers (file sharing or printer sharing) you could delete teh samba-client too.

smbclient

---

### Post by feneks on 2005-01-04
If you want to do it the hard way:
look at the HOWTO for a minimum installation
[http://www.ubuntulinux.org/support/documentation/howto/miniRAM](http://www.ubuntulinux.org/support/documentation/howto/miniRAM)

---

### Post by az on 2005-01-04
Remove the packages found in /var/cache/apt/archives.  These are copies of what is already on the cd put there for convenience.

Try abiword.  You may be able to get away with removing openoffice.  Use gnumeric for spreadsheets.

Whenever you mark packages for removal, you can see what wil happen before it actually does it.  Using synaptic, play around with the packages you do not want.  If they pull something else that you need along with them, go back and start over.  Some packages like ubuntu-desktop are empty packages wich are just dependancies.  You can safely remove them without removing all your desktop...

---

### Post by edemark on 2005-01-04
Thanks toall of you I was able to get some more free space (up to 600 Mb) 
I have removed almost everything you have suggested.
However I have one more question. I have removed emacs, so my question is if this was a good or a bad idea? To be honest I have never used emacs but I am not sure if any of my progs will try to use it.


Thanks again

---

### Post by anthony23 on 2005-01-05
[QUOTE=feneks]If you want to do it the hard way:
look at the HOWTO for a minimum installation
[http://www.ubuntulinux.org/support/documentation/howto/miniRAM](http://www.ubuntulinux.org/support/documentation/howto/miniRAM)[/QUOTE]


Has anyone here tried this minimal install. successfully?/with problems? 

I have been trying to follow this how to but can't get icewm to load from the universe repository. I get access to the repository using apt-get update and I was able to 

install xserver using

# apt-get install xserver-xfree86

but I keep getting error messages and 'can't find package messages when I try to install icewm. 

Has anybody else had the same problem? is there a way around this or an alternative method to do a minimal install?

hope someone can help.
Ant

---

### Post by az on 2005-01-05
"I have removed emacs"

Have you no respect?





...but seriously.  Emacs is a text editor with every possible extention you could possibly every want.  It would take you a few years of study to be able to figure out how it al works.  For fun, install emacs and read the tutorial  (CTRL-h CTRL-t, I think...  It tells you when you fire it up...)

It is quite useful for editing and writing programming code.  I would not use it to write a letter if I was already used to using any other text editor.

If you put a four-year-old in front of emacs and teach her how to use that before she learns anything else, she will complain when you present her with any other editor.  She will tell you that they are a pain in the ass and hard to use.



"but I keep getting error messages and 'can't find package messages when I try to install icewm."

Did you add universe to your /etc/apt/sources.list

did you do apt-get update?

---

### Post by anthony23 on 2005-01-05
[QUOTE=azz]



"but I keep getting error messages and 'can't find package messages when I try to install icewm."

Did you add universe to your /etc/apt/sources.list

did you do apt-get update?[/QUOTE]
 

I followed these instructions: 

vi apt/sources.list

(If you are not familiar with vi you can use nano or any other texteditor instead.)
Enable the universe-repository by removing the Hashmarks (=# (2 times))

removed the hash marks 

then

 apt-get update

then

apt-get install icewm

I receive a number of err and could not stat messages ending with message 

E: Couldn't find package icewm


Somehow the same process worked with x
# apt-get install x-window-system-core

but not icewm

---

### Post by feneks on 2005-01-09
hi anthony

Do you still have the problem to install icewm?

Perhaps a simple **sudo apt-get -f install** can help?

---

### Post by feneks on 2005-01-09
Just to check if your universe at sources.list is activated:

**sudo apt-get install mc**

It's a small program called MidnightComander and is a NortonComander-Clone. Works in non-graphical mode and I like the editor **mcedit file**. Of course you may delete it afterwrds. I just want you to do so because mc is in universe. If it doesn't work you will have to edit /etc/apt/sources.list again.

---

### Post by anthony23 on 2005-01-09
[QUOTE=feneks]hi anthony

Do you still have the problem to install icewm?

Perhaps a simple **sudo apt-get -f install** can help?[/QUOTE]
 Hi Yeah I kind of gave up for a bit and trying instead a default install and then delete stuff, its been loading for the past three days... so think I'm close to giving up with this particular avenue...
thanks I will try these tips and post the results here.

---

### Post by anthony23 on 2005-01-11
[QUOTE=anthony23]Hi Yeah I kind of gave up for a bit and trying instead a default install and then delete stuff, its been loading for the past three days... so think I'm close to giving up with this particular avenue...
thanks I will try these tips and post the results here.[/QUOTE]
 >Perhaps a simple sudo apt-get -f install can help?


>sudo apt-get install mc

both came up with w:couldn't stat package....

so after becoming root and using vi to delete hashmarks

 my apt/souces look like this: 


## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

I also tried deleting the hashmarks on the last two lines.

---

### Post by az on 2005-01-11
Excuse me while I grasp at this straw...

"my apt/souces look like this"

Is your file named apt.sources
or
apt.souces?

I ask because maybe you inadvertently renamed it?


Icewm is most definitely in Universe.

please post the result of 

sudo apt-get update
sudo apt-get install -f
sudo apt-cache search ice



We _will_ get this to work.

---

### Post by feneks on 2005-01-12
[QUOTE=azz] please post the result of 

sudo apt-get update
sudo apt-get install -f
sudo apt-cache search ice
[/QUOTE]
sudo apt-get install -f > aptproblem.output 
will put the output of your screen to the file aptproblem.output which can be viewed and edited with gedit or anyting else.

---

### Post by anthony23 on 2005-01-13
[QUOTE=feneks]sudo apt-get install -f > aptproblem.output 
will put the output of your screen to the file aptproblem.output which can be viewed and edited with gedit or anyting else.[/QUOTE]
 Tried these 

sudo apt-get update
sudo apt-get install -f
sudo apt-cache search ice

'W: couldn't stat source package list' followed by urls

If this is a network problem as I suspect how do I test, configure, setup my network connection (an ethernet to a Netgear adsl router)?

---

### Post by az on 2005-01-13
Type this:

ifconfig

and show the result.

Also, do 

ping [www.google.ca](www.google.ca)

and show the result.

If you are not connected to the internet, do you know how to configure a net connection?

---

### Post by anthony23 on 2005-01-16
[QUOTE=azz]Type this:

ifconfig

and show the result.

Result is

link encap:Local Loopback

UP LOOPBACK RUNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes:1544 (1.5 KiB) TX bytes

Also, do 

ping [www.google.ca](www.google.ca)

Result : 

ping : [url]unknown host

did 

ping router ip address

result unknown host

so how do I configure my network connection from the text prompt?

---

### Post by feneks on 2005-01-16
So the net is dead. - Long live the net.

How do you get to the net?
Modem, ADSL, XDSL, ISDN, Local Network, others ?

Which networkcard/netorkdevice do you use?
the file **/var/log/dmesg** may give you a hint.


--edit---

I miss the 127.0.0.1 inet address at the output of ifconfig.

---

### Post by anthony23 on 2005-01-17
[QUOTE=feneks]So the net is dead. - Long live the net.

How do you get to the net?
Modem, ADSL, XDSL, ISDN, Local Network, others ?

Which networkcard/netorkdevice do you use?
the file **/var/log/dmesg** may give you a hint.


--edit---

I miss the 127.0.0.1 inet address at the output of ifconfig.[/QUOTE]
 so my network connection is an ethernet to a netgear adsl router (most other machines seem fairly intuitive with this device)

looked at 

/var/log/dmesg 

gave quite a lot of info not sure what to make of it all, saw nothing so far about ethernet, network what should I look for exactly?

when I did sudo if config eth0 up 

result : 

ERROR while getting interface flags: No such device

tried  sudo dhclient eth0 

result : 

Inthernet Systems Consortium DHCP Client V3.0.1rc14

sit): unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags

Bind socket to interface: no such device

!!

Ethernet socket flashing at the back of the tower and when I opened it up it looks pretty stable. 


I miss the 127.0.0.1 inet address at the output of ifconfig.

inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope: Host

one option I haven't tried is to use another usb adsl as the usbs look ok, but this is going to put all other machines off for the days so I'm reluctant to do this for the sake of this old box.

---

### Post by aleXL on 2005-01-17
I didn't have any problem with IceWm... 

But when I got to apt-get acroread... htings started going awry...

Couldn't get office...  so then reinstalled normal Ubuntu...

Thankfully I was just trying Mini it for the crack of it... not out of necessity...

Good luck with it all tho'... and hope someone out there/here can help...

---

### Post by feneks on 2005-01-17
[QUOTE=anthony23]so my network connection is an ethernet to a netgear adsl router (most other machines seem fairly intuitive with this device) [/QUOTE]

I suppose you use another computer/software to get to the net by this router. So I'd say netgear works good.  

```
less /var/log/dmesg | grep eth
``` 
should tell us if Ubuntu recognices an ethernetcard.

```
lspci | less 
```
lists all PCI-cards inserted. 

--explanatory note--
The command *less* allows you to scroll output with your coursors 
"q" quits less.

---

### Post by aleXL on 2005-01-18
P.S. I am hardwred to a Netgear DG834G... not WIrelessly...

Oh... while I'm here...

Ebuyer's cheapy wireless cards... any drivers available?

Newbie so have no idea how/where to install... yet...

Hoping...

---

### Post by anthony23 on 2005-01-19
[QUOTE=feneks]I suppose you use another computer/software to get to the net by this router. So I'd say netgear works good.  

```
less /var/log/dmesg | grep eth
``` 
should tell us if Ubuntu recognices an ethernetcard.

```
lspci | less 
```
lists all PCI-cards inserted. 

--explanatory note--
The command *less* allows you to scroll output with your coursors 
"q" quits less.[/QUOTE]

Thanks for this, but I had a little bit of trouble with these two first : I was using Vi to look at /var/log/dmesg which was fine I just don't know what I'm looking for e.g. there is a list of PCI cards, but none recognisably network or ethernet related, but as I said I just don't know what I'm looking for. 

less /var/log/dmesg | grep eth[/CODE]  this didn't give me much, but then I miss this character | on the ubuntubox keyboard.  

so 'less' command didn't seem to work 

and scarily when I used these commands with vi text editor I got the message Warning Output not to a Terminal 

!!

So, sorry, I realise this is frustrating for you, I do not know much, but I am determined to get this to work.  Lets go back to /var/log/dmesg where I get the list and tell me what to look for or I can paste the whole list up here (lots of typing, but if it helps fine) 

A

---

### Post by anthony23 on 2005-01-19
[QUOTE=aleXL]P.S. I am hardwred to a Netgear DG834G... not WIrelessly...

Me too. do you get net? 

as you can see from above I'm having some trouble. If you are getting internet it would be interesting to hear from you how you did it. If not some of the above is probably useful to you.

---

### Post by feneks on 2005-01-19
I was looking for some guides for beginners like you. I have to say that it was easier to find guides in German. 

[http://www.linuxpackages.net/howto/slackfiles/books/slackware-basics/html/shell.html](http://www.linuxpackages.net/howto/slackfiles/books/slackware-basics/html/shell.html)
gives you a short introduction to terminals and there you'll get to know what this "|" does. It's called pipe and is no "el" or uppercase letter of "i".

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
This is a fine guide dealing only with shell and it's capabilities. I think I will read it myself. Although I will start with "writing shellscripts" - where the fun begins.


If you are using an english keyboard you should find "pipe" at [shift]+[backslash (\)] 
[http://www.bimminger.at/content/bereich/tips_diverses/tipp_tastaturlayout](http://www.bimminger.at/content/bereich/tips_diverses/tipp_tastaturlayout)
I'm not sure if this fits to an uk or us keyboard - or booth?

In dmesg you should have a look at lines beginning with eth0. 

And you don't need to type all output.
If you use a terminal in GNOME you can use cut and copy. - in booth directions :wink:
Another possibillity is to use this command:
```
more /var/log/dmesg  > dmesg.txt
```
This will create a file called dmesg.txt filled with the normal screen-output. This file can be opened by openoffice, gedit, vi or any other text-program. I used the suffix .txt but it doesn't matter what you type there. The suffix-name should be logical to you that's all. for example: I think the text is saved in ASCII-code so you could call it dmesg.ascii too.

With lspci you should find something with "ethernet" mostly "ethernet-controller:" 

And HEY EVERYBODY HAS BEEN A BEGINNER ONCE - except me   :-P
(@once: correct word order?)

--edit--
the command more is nearly the same as less but less is better.

---

### Post by feneks on 2005-01-19
@ aleXL
Did you ever get to internet with ubuntu?

---

### Post by anthony23 on 2005-01-20
Thanks for the terminal and shell helpers, I need to get the basics of this sorted before I get on, but I think I know where I went wrong and hope I can find pipe | on the keyboard of the machine otherwise I'll try 'more' instead. Typing output at the moment involves reading from the screen and typing out on another which has net connection i.e. the one I'm using to communicate with you now. No OO, no network, no Icewm. 

get back later with some progress hopefully. 

hope you are learning something about non-knowledge and beggining too.

---

### Post by feneks on 2005-01-20
[QUOTE=anthony23]Thanks for the terminal and shell helpers, I need to get the basics of this sorted before I get on, but I think I know where I went wrong and hope I can find pipe | on the keyboard of the machine otherwise I'll try 'more' instead. Typing output at the moment involves reading from the screen and typing out on another which has net connection i.e. the one I'm using to communicate with you now. No OO, no network, no Icewm. 

get back later with some progress hopefully. 

hope you are learning something about non-knowledge and beggining too.[/QUOTE]


What about floppy?

---

### Post by anthony23 on 2005-01-20
[QUOTE=feneks]What about floppy?[/QUOTE]
 lspci | less

lists 

MTXC
ISA
IDE
USB
Bridge ACPI
VGA

no eth

---

### Post by feneks on 2005-01-29
There is a networkcard in your computer? Are you sure?

---

### Post by anthony23 on 2005-03-09
Back here again. I loaded a distribution called Damn Small Linux [http://damnsmalllinux.org/](http://damnsmalllinux.org/) > and this worked well on my machine if a bit slow. 

I also borrowed an usb ethernet adaptor : AEI USB Fast Ethernet Adaptor

This works so with DSL I could get to the net, firefox, use wordprocessor play pacman etc. 

However, I'm back here cos I'm still interested in Ubuntu and the minimal ram install which I was trying to work through might just run that little bit faster than DSL. 

so 

The OS sees the card 

'less /var/log/dmesg | grep eth0' gives me

eth0: AEI USB FAST ETHERNET ADAPTOR

but I still get network unreachable messages when I ping the router, other machines on the same network or a web address. 

I've led him to water, anyone who can tell me how to persuade this usb ethernet to drink in the net, would be greatly appreciated.

---

