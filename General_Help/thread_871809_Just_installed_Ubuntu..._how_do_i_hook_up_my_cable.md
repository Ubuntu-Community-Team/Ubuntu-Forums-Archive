---
title: "Just installed Ubuntu... how do i hook up my cable modem up so I can get Wine?"
date: 2008-07-27
forum: General Help
---

### Post by PsychedelicWonders on 2008-07-27
Alright first thing is first, I have a cable modem that I need to get working with Ubuntu... what is the proper steps in order to do so?

I also need to get Wine going... but I cant do so until I am connected to the internet.

What do I do?

thanks.

---

### Post by sstvinc2 on 2008-07-27
Could you explain your problem a little further?  I don't mean to sound condescending, but my cable modem just plugs in and works.  Is it a problem logging on to a protected network, or do you have an internal modem (do they even make internal cable modems?) or something?

---

### Post by PsychedelicWonders on 2008-07-27
I have tried just plugging my cable modem cable into the back of the machine... and it still wont let me online.

Dont I have to install special linux drivers?

---

### Post by PsychedelicWonders on 2008-07-27
alright I just plugged my cable modem back in the Ubuntu machine... it seems to register it and even connects to a network connection... but still no web pages load up?

---

### Post by sstvinc2 on 2008-07-27
I don't believe you need any special drivers.  I assume you've tried resetting your modem and/or router (that usually solves internetty problems for me).  I'll admit that I'm not incredibly network-savvy, but try posting the output of ```
ifconfig
``` here.  That should help someone more knowledgeable diagnose the issue.

Also, what do you get when you click on the network manager icon in the top-right of the panel?

---

### Post by mbarak on 2008-07-27
Do you use the USB wire or the Ethernet cable?
If you use the USB wire, you do need to install drivers

The best/easiest way to use any modem is with an ethernet cable
When you plug it in, the Network Manager should say "Connected to Wired Network", or something along those lines, and you will be online in seconds

Those modems are made in such a way that they work independently of the Computer and its operating system.  They just connect to your ISP, and connect what ever computer/router that's connected to them - to the internet using standard network protocols.

---

### Post by PsychedelicWonders on 2008-07-27
No I do have it hooked up via the ethernet cable and I do get that good message of "connected to wired network"

But when I open mozilla and try to load a page... nothing still.

Where exactly do I find that ifconfig to copy and paste if for you guys?

would i have to restart my computer after I hook it up?

I have not tried restarting my modem... but when I flip flop it back and forth between this machine and the Ubuntu... its goes right back to working like normal on this machine.

?

---

### Post by mbarak on 2008-07-27
Go to Applications > Accessories > Terminal

At the prompt type in
```
ifconfig
```
Copy and paste that into here

---

### Post by PsychedelicWonders on 2008-07-27
**** this is a problem... because until I get the internet hooked up... I cant copy and paste anything for you guys...

?

---

### Post by gjoellee on 2008-07-27
well you can download WINE .deb's from this site [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) when you get internet back

---

### Post by mbarak on 2008-07-27
You can copy and paste it into a text editor (Applications > Accessories > Text Editor)
save it, copy it to a floppy/usb and upload it to the forums from where you have internet access

---

### Post by PsychedelicWonders on 2008-07-27
man this is exciting.

I've got the internet working... it seems a simple restart of the modem fixed what ever the problem was... for now.  Well see if it acts up agan.

What is a .deb?

Should I download wine via the application searcher in Ubuntu... or via the website you gave me?

---

### Post by steveneddy on 2008-07-27
in terminal

```
sudo apt-get install wine
```

that installs it for you

---

### Post by mbarak on 2008-07-27
The easiest way to install software is through the Add/Remove program

Simply go to Applications > Add/Remove
Search for Wine, check the box and click Apply Changes
*you might want to install Ubuntu Restricted Extras for things like mp3s/wmvs/flash and all those nasty things that can't go into Ubuntu without you paying for Ubuntu

You will have to enable the Universe (community maintained software) and Multiverse (software with Iffy licenses) repositories
do this through the Software Sources (System > Administration > Software Sources)
check all the boxes (except maybe the last one, you're choice) i.e. main, universe, restricted, multiverse
After this, you will be able to install *all* the software available in the Ubuntu repository

.deb are Debian package files

Ubuntu works in a way that all (most) software is downloaded from a  central repository that way all of their dependencies are satisfied without you having to worry about them, and so they get automatically updated when new versions come out

This is what allows you to install Wine through Add/Remove, or through this simple command
```
sudo apt-get  install wine
```

Edit:
Anywhere it asks for a password (ex: when installing software) type in YOUR password
This is a security measure.  Anytime you do something that may potentially affect the entire system rather than you're user files/folders, you need to be the super-user (root)
This system allows you to be the root user temporarily to do what you need to do and return to your safe, secure, harmless user account (ex: installing software :p)

---

### Post by PsychedelicWonders on 2008-07-27
alright, I am going to try that wine install now... but in the meantime help me with my recent firefox 3 upgrade...

First off, it was at like 3% for like 10 minutes, then all of a sudden it was finished.

Now it says firefox done and I can open the upgrade... 

Then when I do that I get this error...

An Error Occured While Loading the Archive

Then there is something called Command Line Output

What exactly is this?

this is what it says...


bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by steveneddy on 2008-07-27
> **PsychedelicWonders said:**
> alright, I am going to try that wine install now... but in the meantime help me with my recent firefox 3 upgrade...

First off, it was at like 3% for like 10 minutes, then all of a sudden it was finished.

Now it says firefox done and I can open the upgrade... 

Then when I do that I get this error...

An Error Occured While Loading the Archive

Then there is something called Command Line Output

What exactly is this?

this is what it says...


bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

What are you talking about? Firefox is included in Hardy. There is nothing extra to install to hav Firefox.

The system in Ubuntu updates itself, the whole thing, apps and all, at one time.

You shouldn't have to download anything from the internet to update Firefox.

Please tell us where you were downloading from?

Or were you updating normally?

---

### Post by PsychedelicWonders on 2008-07-27
I was trying to upgrade to version 3

I want things like tabbed browsing and all of the new extras... doesnt seem I have tabbed browsing and it all looks pretty basic and boring.

---

### Post by mbarak on 2008-07-27
You have version 3
to open a new tab middle click (if you're on a laptop press the 2buttons at the same time - this emulates a middle click) on a link or press Ctrl+shift+T

---

### Post by PsychedelicWonders on 2008-07-27
Hmm, I'm not sure what middle click is... my scroll wheel?

And I tried that crtl shift T deal and it worked once, and I dont even know how I got it to open a tab cause I couldnt open another one.

I seen I can right click and do a tab... but I'm used to i.e. (unfortunately) but I like how I just have one click in my tool bar to open a new tab... is there any way to set up a short cut like that?

This looks to plain jane and boring... if I change the theme in Ubuntu to be a little flashier, will these modifications move over to firefox and like programs to give it a better look?

Or do I have to download something separate for firefox to change the look?

Also, I believe I installed wine... hopefully correctly... what is a way for me to check?

---

### Post by steveneddy on 2008-07-27
:|

---

### Post by PsychedelicWonders on 2008-07-27
Yeah I'm seeing screen shots of a much much better & newer looking firefox.

Whats up with that?

How do I know if wine installed properly?

I want to go get a new game.  :D

---

### Post by mbarak on 2008-07-27
> **PsychedelicWonders said:**
> Hmm, I'm not sure what middle click is... my scroll wheel?
yes
> 
I seen I can right click and do a tab... but I'm used to i.e. (unfortunately) but I like how I just have one click in my tool bar to open a new tab... is there any way to set up a short cut like that?
You can go to the tab preferences (Edit > preferences > tabs) and select "Always show tab bar" that way you can simply double click the tab bar to get a new tab
Optionally you could install the extension called "Basic" to get a "new tab" button on the tab bar
you could also just right click on the firefox toolbar (where the back/forward buttons are) click customize - and drag the "new tab" button onto the toolbar (not the tab bar)

> 
This looks to plain jane and boring... if I change the theme in Ubuntu to be a little flashier, will these modifications move over to firefox and like programs to give it a better look?

Or do I have to download something separate for firefox to change the look?

go to [http://addons.mozilla.org](http://addons.mozilla.org) to get both themes and extensions to firefox

> 
Also, I believe I installed wine... hopefully correctly... what is a way for me to check?
if you installed wine via Add/Remove or with the command line (sudo apt-get install wine)
there should be a Wine folder under Applications

to use wine open the terminal (Applications > Accessories > Terminal) and type in:
```
wine /path/to/program.exe
```
Alternatively you can right-click your .exe and click Open With - then select Wine

---

### Post by eldragon on 2008-07-27
> **PsychedelicWonders said:**
> Yeah I'm seeing screen shots of a much much better & newer looking firefox.

Whats up with that?

How do I know if wine installed properly?

I want to go get a new game.  :D

im going to give you some overall guidance on what you are trying to accomplish..

that is, you want to install wine, which is a windows api translation layer (or something like that). quite hackery if you ask me. half the time it works, and half the time it doesnt. i would first suggest you setup a dualboot environment and continue to play games through windows. since its quite a pain to get games working right under wine. 

secondly. i asume your game needs some kind of 3d graphics in order to work. this makes things extra complicated when using wine. first i would consider having 3d working natively under linux. then consider linux native games (yeah, they are not as top notch as commercial games, i know).

for a not so experienced user, i would suggest you stay away from wine for a while. get comfortable with the Operating system, which is a challenge on its own.

now to answer some of your questions that kept ignored in the thread:

a .deb is a precompiled and packed set of files which usually add functionality to the operating system. programs come prepackaged in .debs even synaptic downloads updates as .deb packages. think of them as the .msi installers from windows.

your cablemodem probably comes with 2 ports, usb port, and ethernet port. the ethernet port is the common port used to network computers. its the most hassle free way to connect your cable modem to your computer, since it requires no drivers. the usb port requires drivers for the USB interface the cable modem provides. adding a virtual network port to your computer. IF you have an ethernet port on the computer, always use that.

firefox 3 comes already installed on ubuntu 8.04 (aka hardy heron). and system updates ensures you get the most current version. system updates are being executed through the small orange star next to the clock on the top bar. just click it when it appears, and follow the on screen instructions. its not so hard. you will need to provide your administrative password.


i hope i cleared some stuff up. and even though there are many shortcomings in using linux vs windows. there are way more benefits. most of which you will probably be aware of, otherwise you wouldnt be here in the first place :D

good luck.

---

### Post by PsychedelicWonders on 2008-07-27
Alright... figured out most of the tabbed stuff... thanks.

But can I move the New Tab icon from the tool bar to the tab bar anyhow?

There is no wine listed under applications... I went through the motions as it prompted me... I never had to enter 

(sudo apt-get install wine)

It just seem to install like a normal windows application... I take it I missed a step?

You mentioned having to type or right click etc etc... but arent there desktop "shortcuts" to double click to open a program like in windows?

As far as adding on windows and just playing games there... I wish it was that easy.  My budget is busted for addtional software (other than a new game), so windows will have to wait.

In the mean time I am going to get either warcraft III or Supreme commander or Command and Conquer 3 or Ages of Empires III, which are all rated to play pretty flawlessly in wine... so I'm hoping it will be a fairy smooth transition... and finally give me something to do and use this machine right away.

The disk I had was for 7.04... should I download the newest version?

It updated about 208 files... but how do I tell if it updated to 8.04?

---

### Post by mbarak on 2008-07-27
Installing something through Add/Remove is the same thing as installing something using apt-get install
you can try typing in the terminal
```
wine --version
```if it sais "This command is not found" you don't have it
if it gives you the version number :p then you have it

> But can I move the New Tab icon from the tool bar to the tab bar anyhow?No, you need the "Basic" extension for firefox
installing firefox extensions are dreadfully simple. you go to the website ([http://addons.mozilla.org](http://addons.mozilla.org)) find your extension - click install
a little popup comes up saying "do you want to install "name of extension" then it asks you to restart firefox (you can ignore it and restart later ex: after more extensions/themese :D)

> It updated about 208 files... but how do I tell if it updated to 8.04?     When you go into the update manager (the orange star or System > Admin > Update Manager) there should be a box near the top saying New distribution available - click here to upgrade

is that what you did? if it isn't, you don't have the newest version yet

Since you have 7.04 you have to upgrade to 7.10 and then to 8.04 (to ensure a smooth upgrade)
or...you could download the cd for 8.04 burn it and start over if you'd like

Edit: To check your version run lsb-release -a in the terminal (Apps > Accessories > Terminal)

---

### Post by PsychedelicWonders on 2008-07-27
Double post

---

### Post by PsychedelicWonders on 2008-07-27
Alright this is what it tells me when I ran the terminal...

psychedelicwonders@PsychedelicWonders:~$ wine --version
wine-0.9.33
psychedelicwonders@PsychedelicWonders:~$ 


so I'm good yes?

How does wine work... Do I first have to have wine open and then try to open the other program I am wanting to use... or do I actually open the program with wine via the right click you mentioned?

I tried typing in  lsb-release -a  in the terminal to check my version and came up with this...

psychedelicwonders@PsychedelicWonders:~$ lsb-release -a
bash: lsb-release: command not found
psychedelicwonders@PsychedelicWonders:~$ lsb-release -a
bash: lsb-release: command not found

When I went to the updates section, there wasnt any tab to update or upgrade.

How & where do I upgrade to 7.10 first?

What do the three digits mean?  what is the difference in 7.04 and 7.10? Not actual upgrades, but in the value of their numbers and positioning.

What do the positions actually mean?

Ive tried adding additional themes or something for firefox, but when i click "Add to Firefox" nothing happens, and right above that tab says really small "Upgrade Firefox to use this tab"

Thats why I tried to download the newest version of firefox.  That and the version I have looks like its from 10 years ago.

---

### Post by Neo_The_User on 2008-07-27
> **mbarak said:**
> 

Since you have 7.04 you have to upgrade to 7.10 and then to 8.04 (to ensure a smooth upgrade)



I never ever update distributions unless its through a CD or DVD like you said. I hate it. It's smoother and cleaner if you start all over. Also, if you update to 8.04, wine 1.0 stable will be right in the repository waiting for you.

---

### Post by mbarak on 2008-07-27
I'm sorry, its ```
lsb_release -a
``` not ```
lsb-release -a
```

and 7.04 means 2007.April

wine works by typing 
```
wine /path/to/program.exe
```
alternatively, right click the .exe - and click open with - then select wine

To upgrade go to System > Admin > Update Manager
click Check. if there are any updates to get, get them
after you install them, click check again.
there should be something saying New Distribution Version available or something like that - with a version number 7.10 (or 8.04) click the button next to the message and watch all the work being done for you

---

### Post by mbarak on 2008-07-27
> **Neo_The_User said:**
> I never ever update distributions unless its through a CD or DVD like you said. I hate it. It's smoother and cleaner if you start all over. Also, if you update to 8.04, wine 1.0 stable will be right in the repository waiting for you.
Agreed - that's what I usually do

---

### Post by steveneddy on 2008-07-27
That explains it.

I didn't think he was on Hardy.

---

### Post by PsychedelicWonders on 2008-07-27
alright I just upgraded to 7.10 and got this message at the end...

Support for some applications ended

Canonical Ltd. no longer provides support for the following software packages. You can still get support from the community.

If you have not enabled community maintained software (universe), these packages will be suggested for removal at the end of the upgrade.


binfmt-support
feisty-session-splashes
gcj-4.1-base
gij-4.1
gnome-cups-manager
libgda2-3
libgda2-common
libgnomecupsui1.0-1c2a
liblzo1
libportaudio0
libslab0
libstlport5.1
openoffice.org-filter-mobiledev
ttf-baekmuk
vnc-common
xvncviewer

what does that mean?

Do I need to re-install it?

---

### Post by Neo_The_User on 2008-07-27
You don't need to re-install. It's just telling you what applications will be removed. You can install them again after installation.

---

### Post by mbarak on 2008-07-27
you can ignore that message
it most likely means that they've moved on to a newer package with a different name (ex: package2), or a different package altogether
you can uninstall those packages

now just do the same thing again
upgrade existing packages, then upgrade you're system, then finally, upgrade to the bug/security release 8.04.1 and - you will be finished with a brand spanking new (FREE) system

---

### Post by PsychedelicWonders on 2008-07-27
so I have to go through the add/remove programs and manually delete all of those one by one?

---

### Post by sstvinc2 on 2008-07-27
One thing that might be a problem is something on your ISP's side of things.  I remember in college I had difficulty at one point getting access to the internet because our network couldn't find any Windows or Mac anti-virus software on my Linux box.  Maybe try calling your ISP and see if that could be part of the problem.

---

### Post by vze57gc8 on 2008-07-27
u need to re set the thingy. un plug it from the computer  nd the power out let. shut dwn the computer and let everything stay unpowered for 5 mins. then restart the computer nd reconnect the modem

---

### Post by mbarak on 2008-07-27
> **PsychedelicWonders said:**
> so I have to go through the add/remove programs and manually delete all of those one by one?

nonononononono :p you can completely forget about those if you'd like - they're harmless

If you truly want to get rid of them
go to System > Admin > Synaptic

type in your password

on the left click "status"
completely remove everything under "Local/Obsolete" and "Autoremovable"
you might have to revisit the "auto-removable" section after uninstalling the packages from "obsolete"

P.S - install something using Add/Remove, Synaptic, apt-get, or aptitude has the same effect
they all use the same system (APT Package Manager) but present it to you differently

---

### Post by PsychedelicWonders on 2008-07-27
So it is apparent that wine is installed properly...

Can I now use this program to run my wireless mouse and keyboard software?

Can you make shortcuts on the desktop like in windows?

Ideally I want my desktop to resemble the MAC OS... I just think its a real clean, minimalist look, but I will figure out how to change that theme later.

What is the next step when I buy Warcraft III soon and try to install it? 

What are my exact steps before I'm playing the game?

---

### Post by cowboyup6983 on 2008-07-27
> **PsychedelicWonders said:**
> Alright first thing is first, I have a cable modem that I need to get working with Ubuntu... what is the proper steps in order to do so?

I also need to get Wine going... but I cant do so until I am connected to the internet.

What do I do?

thanks.

if u have comcast and just connected to a regular comcast modem, shut down pc. remove ethernet cable from back of PC. then unplug the power from the BACK OF THE MODEM. leave unplug for a minute. then reconnect power, wait for all solid green lights. plug in ethernet cable and powerup the PC. if your still not connected then u must have some advance way of connecting. because u dont need any drivers of anykind, unless u were connected via wireless card, of which u would need to download drivers for the device. sounds like something is going on through your internet provided. if u dual boot, go in and make sure your connected through windows. if u are, then im totally lost and dont know whats wrong with connection. other than your Ethernet LAN card is not supported by linux, which is impossible.

---

### Post by todak on 2008-07-27
> **PsychedelicWonders said:**
> man this is exciting.

I've got the internet working... it seems a simple restart of the modem fixed what ever the problem was... for now.  Well see if it acts up agan.

If my electric power gets interrupted, such as during a thunderstorm (or perhaps a "tree falling on a power line in Ohio" that caused the great blackout in 2003!), I must reboot the modem and all attached routers to get everything back to proper working order.

---

### Post by PsychedelicWonders on 2008-07-27
I'm downloading this update... and it said in the beginig that it was going to take like an hour and a half... its been about 45 minutes and still has like 50 minutes left....

Do downloads normally take this long... or is something wrong?

---

### Post by AFarris01 on 2008-07-28
In short...yes, some downloads can take a while, depending on how big they are, how many different packages are needed, etc.

If you sat there and watched it (like i have a habit of doing) you'll probably notice that the download speed fluctuates sometimes (ie going from 150 kb/s to 3000 b/s etc) ive determined that this is an ISP thing, and i have no idea what purpose it serves.  Basically though, if you watch it for a little bit, note the times it says at its slowest download speed, and the time it says at it's highest download speed.  take the average of those 2 numbers, and thats usually a much more accurate time. 

Now, one possible way that you can help speed up the downloads is by selecting a different download mirror (did wonders for my connection.) to do this, follow these steps:

Go to "System -> Administration -> Software Sources" you will be prompted for your password here.  enter it in, and you should see a screen with a few checkboxes, and a drop-down menu that says something like "(YourRegion) Server" or "Ubuntu Main Server." 

Click that drop down box, and click the entry at the bottom, which is called something like "Select a mirror..." or "Choose a server".  a new window should pop up with a big list to the left, and a few buttons to the right.  

click the button on the right in that new window that says something like "select best server" and wait a few minutes.  At this point, the mirror manager pings all of the download servers in the list, one by one, and automatically selects the server with the lowest ping-time, which translates to faster download speeds for you! Just make sure that you're not downloading something else from the internet while doing this, otherwise the results won't be as accurate or dramatic.

Finally, close out of all the windows you just opened via the  'apply' 'ok' or 'close' buttons at the bottom, whichever ones happen to be present.  This should help alleviate any slow download problems you might be having for Ubuntu Updates and for downloading new software from the repos.

Note: If you have a package manager already running, (i.e. you are already downloading some updates, a new program, etc.) do not attempt to change the software source, because it won't let you.  Wait till the download finishes, and the package manager isn't running anymore, then you can change the software source (you could also cancel the active download, change the software source, then restart the download, but this isn't recommended because it could make you start completely over, which would waste more time than it would save).  No computer restart is needed after applying any of these changes either (you may have noticed already, but its not often that you'll have to restart your computer after an update, of something, but when you do need to, Ubuntu will tell you with an icon on the task bar, and a pop-up message)

Also, i saw you mentioned wanting to make your desktop look like a Mac desktop... though I encourage you to first get used to what you have already, and take advantage of it's strengths, there is a pretty good general guide to making Linux look like a Mac here:

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

and for ubuntu-specific, this one is good:

[http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/](http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/)

me personally, I hate the Mac desktop, but a lot of people like it, so its helpful to know how to mess with it when you do the kind of stuff i do.

There...hope thats a helpful bit of info!

Andrew

(PS: i don't remember specifically what some of the dialogs say because im not in front of a linux box right now, cause my workplace hasnt seen the light yet :( so i apologize if some of the directions are a little hazy because of that)

---

### Post by PsychedelicWonders on 2008-07-28
Mac here:

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

and for ubuntu-specific, this one is good:

[http://rockmanx.wordpress.com/2008/0...c-hardy-heron/](http://rockmanx.wordpress.com/2008/0...c-hardy-heron/)


So what are the real differences between the guides on those two lists?  

I like the way the desktop looks in the 2nd link compared to the 1st one.  (maybe its just the background pic and the rest is the same, I have no idea?)

thanks though.

---

### Post by AFarris01 on 2008-08-13
really, the only difference between the 2 is that the first guide isn't targeted at a specific distribution, its just for gnome in general.  i didnt go through every single stem, so i don't know if there's a drastic difference between them, which is why i put them both up.

either way, im glad you found them useful, and hopefully by now you've already successfully changed your gnome desktop as you wished, and enjoying it to its fullest.  Happy ubuntu-ing!

Andrew

---

### Post by maxmanapple on 2008-08-13
Sometimes the old "Working Offline" option on the file menu will be automaticly on when you unplug the internet many times. Check for it. If that's not the problem maybe you would like to try using the Add/Remove Apps window in the Apps menu, or open your console and write>  apt get wine

Hope it helped

---

