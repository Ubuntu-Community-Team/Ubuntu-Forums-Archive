---
title: "[SOLVED] How do you install something"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by cabbiinc on 2008-12-22
Quite simply, I have Ubuntu 7.10, and I am trying to install Firefox 3. I can download from the site but haven't got a clue as to what command to install.

But I am asking this in a more general question so I don't have to come here and ask the same everytime I want to install something.

Any help is appreciated.

Dan

EDIT----

Just so you don't have to read 5+ pages, my biggest problem was that I needed to add both connections (to DSL modem and Ubuntu box) to my network bridge, and then go into the properties of the bridge and check for updates. It was an unsigned update and Windows was never going to add it to the regular updates. That connected everything to the internet.

---

### Post by rdcatman on 2008-12-22
Please if you get an answer please let me know.  I have 2 programs that are linux format that I want to install but once they're downloaded from the internet, I haven't got a clue what to do to get them on my computer. I have tried using the package manager and the update manager and neither will install the program.  Ubuntu Linux is not user friendly.

---

### Post by xjcannonx on 2008-12-22
I don't really like to just shell out links but this one by [psychocats]("http://www.psychocats.net/ubuntu/firefox") should do it.

---

### Post by xjcannonx on 2008-12-22
> **rdcatman said:**
> Please if you get an answer please let me know.  I have 2 programs that are linux format that I want to install but once they're downloaded from the internet, I haven't got a clue what to do to get them on my computer. I have tried using the package manager and the update manager and neither will install the program.  Ubuntu Linux is not user friendly.

Your problem doesn't seem to be the same as the one posted so you can post a new thread or check this one out also by [psychocats]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by cabbiinc on 2008-12-22
On a side note, the references to coffee on the left side of the posts are making me drink about 3 times as much coffee as I'd normally drink. 8-[ 8-[ 8-[

---

### Post by cabbiinc on 2008-12-22
> **xjcannonx said:**
> I don't really like to just shell out links but this one by [psychocats]("http://www.psychocats.net/ubuntu/firefox") should do it.

Ok, so I did the copy and pasted:

cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
rm firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Now my internet is gone. Clicking Firefox gives an error.
I'm posting from my Vista computer that I finally networked Ubuntu through last night thanks to these forums.

EDIT: CRAP!! I just reallized that I didn't download Firefox to the same location as noted by psycocats. I'll see about recifying this and report back.

---

### Post by SunnyRabbiera on 2008-12-22
Well you may want to install ubuntu 8.04 as 7.10 will be obsolete soon.
Firefox 3 has been known to cause issues with older versions of ubuntu.
or switch distros, Mandriva is pretty good.

---

### Post by cabbiinc on 2008-12-22
> **SunnyRabbiera said:**
> Well you may want to install ubuntu 8.04 as 7.10 will be obsolete soon.
Firefox 3 has been known to cause issues with older versions of ubuntu.
or switch distros, Mandriva is pretty good.

I'm trying to upgrade now, but don't know if it's upgrading to 8.x or just upgrading the current 7.10 to ???

Still don't have FF, but I activated Epiphany, so I do have a web browser until I get an 8.x installed.

---

### Post by cabbiinc on 2008-12-22
> **cabbiinc said:**
> I'm trying to upgrade now, but don't know if it's upgrading to 8.x or just upgrading the current 7.10 to ???

Still don't have FF, but I activated Epiphany, so I do have a web browser until I get an 8.x installed.

The upgrade feature doesn't show any version of Ubuntu available. Can I do an upgrade from the web without burning a CD if the update manager isn't showing a more current version available?

---

### Post by xjcannonx on 2008-12-22
have you looked at [this]("https://help.ubuntu.com/community/UpgradeNotes")

I haven't upgraded like this so I cannot offer any personal experience.

---

### Post by cabbiinc on 2008-12-22
> **xjcannonx said:**
> have you looked at [this]("https://help.ubuntu.com/community/UpgradeNotes")

I haven't upgraded like this so I cannot offer any personal experience.

Yeah, that's where I got the info from. But my update manger doesn't show anything to update too. I've also done the 

sudo apt-get install update-manager-core

that returns:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and
sudo do-release-upgrade
gives me 
Checking for a new ubuntu release
No new release found

If I burned a CD with 8.4 or 8.10 is upgrading from that CD workable or do you need to uninstall the previous version first?

---

### Post by cabbiinc on 2008-12-22
Also, nobody has really said how your supposed to go about installing something. Is it a different procedure for everything? Do you have to learn Linux code for every other program you install or is there a relatively general command that you start with? In Windows you have an EXE command that you look for, it may be different for every program but it's all an EXE file extension. I know that Windows isn't the same thing but I'd assume there's something you guys start with.

---

### Post by twright on 2008-12-22
> **cabbiinc said:**
> Also, nobody has really said how your supposed to go about installing something. Is it a different procedure for everything? Do you have to learn Linux code for every other program you install or is there a relatively general command that you start with? In Windows you have an EXE command that you look for, it may be different for every program but it's all an EXE file extension. I know that Windows isn't the same thing but I'd assume there's something you guys start with.
you can easily install the release of a program which your current version of Ubuntu supports by selecting it from a catalog available via Add/Remove Programs from the Applications menu but this only works well if you have the latest Ubuntu version as otherwise you will only get versions of those programs which are supported for that version. There are generally no commands needed (although you could use sudo apt-get install <program name> or sudo dpkg --install <installer>.deb if you really want). It is a whole lot easier than the whole .exe thing :-). You can also download .deb installers from somewhere like getdeb.net which will install the programs if you run them, these are approximately equivalent to .exe installers but Ubuntu should be able to automatically install any other programs that they require to run (as long as they are in the catalog); Firefox is weird in that it just gives you a single archive file containing the file, you just need to extract it (right click and select extract here) then run the Firefox executable.

I recommend you just download the latest version of Ubuntu and do a fresh install.

---

### Post by cabbiinc on 2008-12-22
> **twright said:**
> you can easily install the release of a program which your current version of ubuntu supports by selecting it from a catalog available via add/remove programs from the applications menu but this only works well if you have the latest ubuntu version as otherwise you will only get versions of those programs which are supported for that version. There are generally no commands needed (although you could use sudo apt-get install <program name> or sudo dpkg --install <installer>.deb if you really want). It is a whole lot easier than the whole .exe thing :-). You can also download .deb installers from somewhere like getdeb.net which will install the programs if you run them, these are approximately equivalent to .exe installers but ubuntu should be able to automatically install any other programs that they require to run (as long as they are in the catalog); firefox is weird in that it just gives you a single archive file containing the file, you just need to extract it (right click and select extract here) then run the firefox executable.

I recommend you just download the latest version of ubuntu and do a fresh install.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

I guess I spent the last 3 days getting the network to work for nothing then.

---

### Post by cabbiinc on 2008-12-22
I won't have access to a CD burner for a while. Is there nothing else I could try?

---

### Post by cabbiinc on 2008-12-22
In reference to the whole "it's easier than the whole EXE thing", are you nuts? I've been at this for close to 5 days and can't seem to get anything done. I can't install jack diddly squat. I can't change anything. I can't do anything. I'm in just as bad a spot as when this computer had Win 98se. Seriously. Nobody is giving any answers, just a bunch of hoopla that it's so easy. 

If it were that easy then why are these forums always so busy?

Sorry if I'm sounding like sour grapes but I'm looking at scrapping what I have done for 5 days and starting over. That's not easy in my opinion, it's down right a headache.

---

### Post by nabilalk on 2008-12-22
> **cabbiinc said:**
> In reference to the whole "it's easier than the whole EXE thing", are you nuts? I've been at this for close to 5 days and can't seem to get anything done. I can't install jack diddly squat. I can't change anything. I can't do anything. I'm in just as bad a spot as when this computer had Win 98se. Seriously. Nobody is giving any answers, just a bunch of hoopla that it's so easy. 

If it were that easy then why are these forums always so busy?

Sorry if I'm sounding like sour grapes but I'm looking at scrapping what I have done for 5 days and starting over. That's not easy in my opinion, it's down right a headache.

Try readin this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by cabbiinc on 2008-12-22
> **nabilalk said:**
> Try readin this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Ok, I read through that, now it looks like I want to burn an ISO of an alternative CD of 8.4 (the next evolution from my current system so that I can manually update my 7.10) but the link [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) shows a bit torrent link that my Vista machine doesn't know what to do with. And my Ubuntu machine doesn't have a CD burner. Is there an app/program for my Vista machine to use to download the bit torrent file with?

EDIT: Oh wait a minute, I found a site that just has the Alternate Istall CD that I need [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by cabbiinc on 2008-12-24
Ok, so I updated to 8.4.
I still don't have firefox
I did the updates thing, took a few hours
I still don't have firefox
I downloaded the firefox file from Mozilla and put it on the desktop
I still don't have firefox

I still dont have fire fox

I STILL DONT HAVE FIRE FOX!!!!!

Can someone please tell me how to install something on this damned computer without trying to convince me that it's easy. This is far from easy. Please don't say how easy it is, it isn't. I just want to know how to install something without having to lose another day from my life.

---

### Post by outcesticide on 2008-12-24
> **cabbiinc said:**
> Quite simply, I have Ubuntu 7.10, and I am trying to install Firefox 3. I can download from the site but haven't got a clue as to what command to install.

But I am asking this in a more general question so I don't have to come here and ask the same everytime I want to install something.

Any help is appreciated.

Dan

did you try synaptic package?

---

### Post by cabbiinc on 2008-12-24
Well I've opened it a few thousand times and still don't see what to put where. I have a folder on my desktop to install Firefox 3. But the Synaptic Package Manager doesn't know it's there.

So yeah, I've tried that.

---

### Post by outcesticide on 2008-12-24
ok well if you open it up and search firefox scroll down, right click apply and it should install with a firefox restart(if you've already tried this im sorry for wasting ur time):popcorn:

---

### Post by cabbiinc on 2008-12-24
> **outcesticide said:**
> ok well if you open it up and search firefox scroll down, right click apply and it should install with a firefox restart(if you've already tried this im sorry for wasting ur time):popcorn:

I know your trying to be helpful but what exactly do I right click? Where?

---

### Post by outcesticide on 2008-12-24
ok heres exact instructions go to SYSTEM-ADMINISTRATION-SYNAPTIC PACKAGE MANAGER and when it pops up click on search or the search bar type FIREFOX and search scroll down until you find firefox 3.0  right click on that firefox 3.0 and select mark for installation and then click apply and click apply again when prompted to

---

### Post by posburn on 2008-12-24
Hi cabbiinc,

Sorry you're getting frustrated.  Here's what you need to do:

In the top menubar on your desktop, click on System > Administration > Synaptic Package Manager.  Once it's open, click on the "Search" button that shows up in the bar of icons at the top of Synaptic.  In the dialog box that opens, type "firefox" and hit Enter.  In a few seconds, the main window of Synaptic should show a list of all executables (they're called "packages" in Ubuntu) with "firefox" in the name. Find the one called simply "firefox" in the list and right-click on the name.  In the menu that opens, click "Mark for Installation".  A dialog box may open asking you to confirm additional files for installation; this is OK, Synaptic is just grabbing everything you need to run Firefox.  Just click "Mark" if such a dialog shows up.  OK, now you have just selected the firefox package (and any "dependencies", other packages needed to install Firefox) for installation.  Now that you've done this, click on "Apply" in the top icon bar in Synaptic.  A dialog box opens asking you to confirm your choices one last time.  Click "Apply" and Synaptic should start downloading the needed files and installing them for you.

If you like, you can then search for other programs and select them in the same manner; this is the most straightforward way to install software in Ubuntu.  You do not need to visit the Firefox website (or any other website) and download anything; Synaptic automatically downloads the necessary files for you.

Hope this helps!

---

### Post by cabbiinc on 2008-12-24
> **outcesticide said:**
> ok heres exact instructions go to SYSTEM-ADMINISTRATION-SYNAPTIC PACKAGE MANAGER and when it pops up click on search or the search bar type FIREFOX and search scroll down until you find firefox 3.0  right click on that firefox 3.0 and select mark for installation and then click apply and click apply again when prompted to

Thanks, well I did that and got as far as finding firefox 3, I right clicked it and clicked re-install. It appeared to work so I clicked ok. It looked like it worked. But it didn't.

When I click on FF it gives me the error:
Could not launch application
Failed to execute child process "firefox" (No such file or directory)

Which is the same thing it's been doing for a day now. I am typing this on my other computer becuase I don't have internet.

---

### Post by outcesticide on 2008-12-24
wait does ur computer with ubuntu have an internet connection?

---

### Post by cabbiinc on 2008-12-24
Just to add, Ubuntu still thinks firefox is installed. I can't install it through the normal chanels because it's already installed. I can't uninstall it because Ubuntu wont let me saying other things are dependant on it. It's a catch 22.

---

### Post by Hangwire on 2008-12-24
Dude.
Seriously. Chill out. 

How to install software, way 1:
Click Applications
Go to the bottom button which reads: Add/Remove... or Add/Remove Applications
Click it, wait for it to load some stuff at the beginning, and there you go. You have categories on the left, a list of the program in a category or from a search in center-up, and a quick introduction about the program in the center-bottom part. Search for programs: Lets say you need a good browser, theres a little field box in the right corner of the screen which you can type stuff to search for in. For example, type "browser", wait a bit, and a few results will come up in the list below. To install programs you want from there, tick the little box on the left from their name in the center-up part where the list is. After that, click Apply Changes - bottom right button to install those applications. Wait a bit, and there you go. A new program installed. You can find them from your Applications menu while searching the category - Games, Programming, Accessories, Education, whatever. 

The second way is through the Terminal: 
Start your terminal window by going to Applications - Accessories - Terminal. 
For the following operations, you need to gain root rights, for this you will use the "sudo" command before everything else.
For example, you need to install firefox. Type in: "sudo apt-get install firefox" and you will see the thing getting installed. Now, firefox is a known package, but every package (installation of a program which you access and search for by apt-get install) has its own specific name, so most time when you need to install something, use the Add/Remove way I described. Apt-get has the same functionality, but Add/Remove way is more user-friendly. In time, and with use, you will get familiar with the terminal and get used to CLI (command line interface).  

Way 3: 
Somebody described that way above.
But.
By .deb files: Its pretty easy, its exactly like an .exe just you have less stuff to click. Now. Lets say you need some .deb packages of programs you want, go here: 

[http://www.getdeb.net/](http://www.getdeb.net/)
or 
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
(scroll down and you'll see a search box)

Download these to your Desktop, or wherever you want, double-click them and after, you just have to press an "Install Package" button that will be in the upper - right part of the newly appeared window of the .deb installer. 

Thats all!
This will be very very helpful to you, I know your pain, I was the same way a couple of months ago when I tried out Ubuntu for the first time, but now its my main operating system and ive made the complete switch. 

Cheers!

---

### Post by cabbiinc on 2008-12-24
> **outcesticide said:**
> wait does ur computer with ubuntu have an internet connection?

It's networked to the internet, I have no browser.

---

### Post by Defrector on 2008-12-24
Describe your catch 22: What things are depending on the browser which are keeping you from completely removing it?

You might be able to remove it depsite, but first lets see what those dependencies are.

I think we're pretty close here.

---

### Post by scorp123 on 2008-12-24
> **rdcatman said:**
>  Ubuntu Linux is not user friendly. Why do you use it then? Nobody forces you to do so. You're free to go back to Windows anytime. Have fun hunting viruses, malware, trojans, worms ... ):P

Still here? Then maybe you wish to rethink that false statement above and get yourself educated a little before posting nonsense such as the above into these forums, yes?

"Linux is not Windows"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by cabbiinc on 2008-12-24
> **Hangwire said:**
> Dude.
Seriously. Chill out. 

How to install software, way 1:
Click Applications
Go to the bottom button which reads: Add/Remove... or Add/Remove Applications
Click it, wait for it to load some stuff at the beginning, and there you go. You have categories on the left, a list of the program in a category or from a search in center-up, and a quick introduction about the program in the center-bottom part. Search for programs: Lets say you need a good browser, theres a little field box in the right corner of the screen which you can type stuff to search for in. For example, type "browser", wait a bit, and a few results will come up in the list below. To install programs you want from there, tick the little box on the left from their name in the center-up part where the list is. After that, click Apply Changes - bottom right button to install those applications. Wait a bit, and there you go. A new program installed. You can find them from your Applications menu while searching the category - Games, Programming, Accessories, Education, whatever. 

The second way is through the Terminal: 
Start your terminal window by going to Applications - Accessories - Terminal. 
For the following operations, you need to gain root rights, for this you will use the "sudo" command before everything else.
For example, you need to install firefox. Type in: "sudo apt-get install firefox" and you will see the thing getting installed. Now, firefox is a known package, but every package (installation of a program which you access and search for by apt-get install) has its own specific name, so most time when you need to install something, use the Add/Remove way I described. Apt-get has the same functionality, but Add/Remove way is more user-friendly. In time, and with use, you will get familiar with the terminal and get used to CLI (command line interface).  

Way 3: 
Somebody described that way above.
But.
By .deb files: Its pretty easy, its exactly like an .exe just you have less stuff to click. Now. Lets say you need some .deb packages of programs you want, go here: 

[http://www.getdeb.net/](http://www.getdeb.net/)
or 
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
(scroll down and you'll see a search box)

Download these to your Desktop, or wherever you want, double-click them and after, you just have to press an "Install Package" button that will be in the upper - right part of the newly appeared window of the .deb installer. 

Thats all!
This will be very very helpful to you, I know your pain, I was the same way a couple of months ago when I tried out Ubuntu for the first time, but now its my main operating system and ive made the complete switch. 

Cheers!

Here's what I did in Terminal for solution 2:

sabryna@sabrynascomputer:~$ sudo apt-get install firefox
[sudo] password for sabryna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libotr2 libntfs-3g16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Defrector on 2008-12-24
With all due respect scorp, let's keep it constructive.

---

### Post by cabbiinc on 2008-12-24
> **Defrector said:**
> Describe your catch 22: What things are depending on the browser which are keeping you from completely removing it?

You might be able to remove it depsite, but first lets see what those dependencies are.

I think we're pretty close here.

When I am in the Add/Remove applications box I try to untick FF and Ubuntu pops up and says 
Cannot remove 'firefox-3.0'

One or more applications depend on firefox-3.0. To remove firefox-3.0 and the dependent applications, use the Synaptic package manager.

Stupid question here, should I remove FF in Synaptic package manager? If so should it be a total removal?

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> Why do you use it then? Nobody forces you to do so. You're free to go back to Windows anytime. Have fun hunting viruses, malware, trojans, worms ... ):P

Still here? Then maybe you wish to rethink that false statement above and get yourself educated a little before posting nonsense such as the above into these forums, yes?

"Linux is not Windows"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I understand that Linux is not windows but you can't tell me that it's user friendly and free and virus free. You can't have it all. I'm just saying that at this point, 5 days after trying to put Ubuntu onto a computer I take one step forward and 2 steps back. First it was the networking, then it was that FF needed a flashplayer plug-in. Then somehow I uninstalled FF without really uninstalling it, so I seamingly cant reinstall it because it's already installed but I can't uninstall it because it's not really installed.

If it were Windows I'd be done. But I'd have a different set of problems to deal with. Viruses would be the least of my worries.

---

### Post by Defrector on 2008-12-24
Yes, use synaptic package manager, do a search for firefox in synaptic, when firefox3 (or any firefox for that matter) shows up in your results, right-click the firefox entries which have a greenish box next to them and select "Mark for complete removal", then when they are marked, click the big "apply" botton at the top of the synaptic program.

- while you do the right-click thing it will probably freak out and say that you have dependencies and that the world will melt-just go through with it, even if it involves removing other apps. I can't think of any critical components that need firefox so you should be fine.

After that is done, use synaptic to reinstall firefox using the same search-for-firefox-and-right-click-firefox-3 method, except mark for installation and click the big apply button. 

And then tell us where we are from there.

---

### Post by scorp123 on 2008-12-24
> **Defrector said:**
> With all due respect scorp, let's keep it constructive. Oh, you think I wasn't? :D

OK, fine .... something else nobody seems to have thought of so far: Are we really sure there is a working Internet connection and that the system upgrade really did work?

What are the results of these commands (copy & paste please ... see below):
```
route
```
```
netstat -r
``` (... the two above should produce almost the same output ... that's OK)
```
cat /etc/resolv.conf
``` ... that should tell us if you have any DNS server configured ... 
```
ping -c5 www.google.com
``` ... a successful ping here would suggest you really have a working Internet connection ... but maybe there are other problems?
```
cat /etc/lsb-release
``` ... that would give us the Ubuntu release you're working on.
```
uname -a
``` ... that would give us the version of your currently running kernel

I want to make sure there is an internet connection ... because if there isn't then all attempts at installing any package will fail.

Above I mentioned "copy & paste" ... obviously if there is no working Internet connection and no browser then this is a bit difficult to achieve ... but not impossible. I'd suggest to redirect the output of any command into a text file, e.g. like this:
```
command >> output.txt
``` ... so you'd run each command above and make sure you use the double chevrons to attach the output that was generated to that file. The text file should end up in your home folder. So maybe you have a USB stick or something and can then move the text file onto the USB stick, and then with the stick go to an OS (you have a dual-boot with Windows maybe? Or a 2nd computer?) where Internet works, and then post the stuff from there.

Due to the difference between how DOS/Windows and UNIX/Linux mark the end of a line it could be that the text file looks misformatted on Windows. Stupid editors such as "Notepad" won't be able to display text files that were created on UNIX/Linux right, you'd have to use a better program such as "Notepad Plus", "UltraEdit", "gvim for Windows", "Lemmy32" or something like that. Opening the "output.txt" file directly with a web browser might work too and show the text contents correctly.

---

### Post by cabbiinc on 2008-12-24
> **Defrector said:**
> Yes, use synaptic package manager, do a search for firefox in synaptic, when firefox3 (or any firefox for that matter) shows up in your results, right-click the firefox entries which have a greenish box next to them and select "Mark for complete removal", then when they are marked, click the big "apply" botton at the top of the synaptic program.

- while you do the right-click thing it will probably freak out and say that you have dependencies and that the world will melt-just go through with it, even if it involves removing other apps. I can't think of any critical components that need firefox so you should be fine.

After that is done, use synaptic to reinstall firefox using the same search-for-firefox-and-right-click-firefox-3 method, except mark for installation and click the big apply button. 

And then tell us where we are from there.

Ok, I marked Firefox for complete removal and synaptic threw in a bunch of other stuff too, I assumed it was all the dependant stuff. It uninstalled, I then reinstalled. But it's the same error message as before.

---

### Post by Defrector on 2008-12-24
scorp: That's better.:)

---

### Post by Defrector on 2008-12-24
ok. Next attempt: when you go to the terminal and enter the command "firefox" what happens? Does it give the same error?

I'm wondering if we have a bad link in the programs menu.

---

### Post by scorp123 on 2008-12-24
> **cabbiinc said:**
>  I understand that Linux is not windows but you can't tell me that it's user friendly  It is. I use Linux since 1996. Let go of your Windows thinking.

> **cabbiinc said:**
>  I seamingly cant reinstall it because it's already installed but I can't uninstall it because it's not really installed.  Do you get an error message from the package manager? Can you post that one please? Knowing the exact error message can help a great deal.

> **cabbiinc said:**
>  If it were Windows I'd be done. I doubt it, especially if you have to install from scratch. I just recently had the "pleasure" of having to install Windows for a client ... it's a royal pain in the a**, especially given the fact that you have to reboot ... sometimes for just moving the mouse it seems? On Linux I can download 200+ packages and I only have to reboot _once_ ... If the OS kernel wasn't touched I even don't have to reboot at all, I can just continue to work.

You perceive Windows being "easy" either because you got it preinstalled on your computer and/or because you've been using it for decades and are therefore accustumed to how it does things; you perceive the many illogic things it does as being "normal".

See the link above. familiar = "easy". And that's why you perceive Linux as being "hard".

---

### Post by scorp123 on 2008-12-24
> **cabbiinc said:**
> But it's the same error message as before. Sorry ... I seem to have missed that one.... Which error message exactly?

---

### Post by outcesticide on 2008-12-24
wow i agree with scorp linux has just kicked a** for me, it was hard adjusting because my mind was installed with vista(lolz) for so long but eventually i became a novice at using it and im still learning new things about it everyday but if you want my opinion find someone who can install ubuntu on a computer from scratch and look at the way he/she did it and learn(you must unlearn what you have learned-yoda)

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> Oh, you think I wasn't? :D

OK, fine .... something else nobody seems to have thought of so far: Are we really sure there is a working Internet connection and that the system upgrade really did work?

What are the results of these commands (copy & paste please ... see below):
```
route
```
```
netstat -r
``` (... the two above should produce almost the same output ... that's OK)
```
cat /etc/resolv.conf
``` ... that should tell us if you have any DNS server configured ... 
```
ping -c5 www.google.com
``` ... a successful ping here would suggest you really have a working Internet connection ... but maybe there are other problems?
```
cat /etc/lsb-release
``` ... that would give us the Ubuntu release you're working on.
```
uname -a
``` ... that would give us the version of your currently running kernel

I want to make sure there is an internet connection ... because if there isn't then all attempts at installing any package will fail.

Above I mentioned "copy & paste" ... obviously if there is no working Internet connection and no browser then this is a bit difficult to achieve ... but not impossible. I'd suggest to redirect the output of any command into a text file, e.g. like this:
```
command >> output.txt
``` ... so you'd run each command above and make sure you use the double chevrons to attach the output that was generated to that file. The text file should end up in your home folder. So maybe you have a USB stick or something and can then move the text file onto the USB stick, and then with the stick go to an OS (you have a dual-boot with Windows maybe? Or a 2nd computer?) where Internet works, and then post the stuff from there.

Due to the difference between how DOS/Windows and UNIX/Linux mark the end of a line it could be that the text file looks misformatted on Windows. Stupid editors such as "Notepad" won't be able to display text files that were created on UNIX/Linux right, you'd have to use a better program such as "Notepad Plus", "UltraEdit", "gvim for Windows", "Lemmy32" or something like that. Opening the "output.txt" file directly with a web browser might work too and show the text contents correctly.

Wordpad seams to work. Heres what resulted.

sabryna@sabrynascomputer:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
default         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
sabryna@sabrynascomputer:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.0.0     *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.2     0.0.0.0         UG        0 0          0 eth0
sabryna@sabrynascomputer:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search domain.actdsltmp


nameserver 192.168.0.1
nameserver 205.171.3.25


nameserver 192.168.0.3
sabryna@sabrynascomputer:~$ ping -c5 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.171.147) 56(84) bytes of data.
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=1 ttl=243 time=49.5 ms
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=2 ttl=243 time=59.7 ms
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=3 ttl=243 time=59.8 ms
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=4 ttl=243 time=49.8 ms
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=5 ttl=243 time=59.8 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20411ms
rtt min/avg/max/mdev = 49.541/55.767/59.833/4.958 ms
sabryna@sabrynascomputer:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
sabryna@sabrynascomputer:~$ uname -a
Linux sabrynascomputer 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

---

### Post by cabbiinc on 2008-12-24
> **Defrector said:**
> ok. Next attempt: when you go to the terminal and enter the command "firefox" what happens? Does it give the same error?

I'm wondering if we have a bad link in the programs menu.

Typing firefox into terminal gives
The program 'firefox' is currently not installed. You can install it by typing: sudo apt-get install firefox-3.0 bash: firefox: command not found

---

### Post by Defrector on 2008-12-24
And it's a pretty safe bet that following those 'sudo apt-get' instructions will just run us in a circle, right?

Just to be safe, try those instructions, though it is starting to look like something is wacky with your package manager. A full reinstall from disc might be an easier route if things don't resolve soon.

---

### Post by scorp123 on 2008-12-24
> **cabbiinc said:**
> Wordpad seams to work.  Yup. So yes, you have Internet and you have 8.04 running. So far so good.

So what's the error message you mentioned a few postings further up? Can you copy & paste that one here as well?

You said that you get a complaint that Firefox kinda is installed and kinda isn't .... But what does it say precisely? What do you get if you enter this into a terminal:

(this is just to refresh the repos):
```
sudo apt-get update
```

I'd need the precise message you get from this:
```
sudo apt-get install firefox-3.0
```

And just because I'm paranoid I'd like to have the output of this one:
```
dpkg -l firefox*
```

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> It is. I use Linux since 1996. Let go of your Windows thinking.

 Do you get an error message from the package manager? Can you post that one please? Knowing the exact error message can help a great deal.

 I doubt it, especially if you have to install from scratch. I just recently had the "pleasure" of having to install Windows for a client ... it's a royal pain in the a**, especially given the fact that you have to reboot ... sometimes for just moving the mouse it seems? On Linux I can download 200+ packages and I only have to reboot _once_ ... If the OS kernel wasn't touched I even don't have to reboot at all, I can just continue to work.

You perceive Windows being "easy" either because you got it preinstalled on your computer and/or because you've been using it for decades and are therefore accustumed to how it does things; you perceive the many illogic things it does as being "normal".

See the link above. familiar = "easy". And that's why you perceive Linux as being "hard".

Yeah I am very comfortable with Windows and at the same time tired of having to pay for the next generation OS just because M$ wants to make a buck. I know it's not really like that but hey, it's jsut and opinion.

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> Yup. So yes, you have Internet and you have 8.04 running. So far so good.

So what's the error message you mentioned a few postings further up? Can you copy & paste that one here as well?

You said that you get a complaint that Firefox kinda is installed and kinda isn't .... But what does it say precisely? What do you get if you enter this into a terminal:

(this is just to refresh the repos):
```
sudo apt-get update
```

I'd need the precise message you get from this:
```
sudo apt-get install firefox-3.0
```

And just because I'm paranoid I'd like to have the output of this one:
```
dpkg -l firefox*
```

Here's what that gave me:

sabryna@sabrynascomputer:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/main Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release.gpg                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Packages
Reading package lists... Done

sabryna@sabrynascomputer:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libotr2 xulrunner-1.9-gnome-support libntfs-3g16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sabryna@sabrynascomputer:~$ dpkg -l firefox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  firefox        3.0.5+nobinonl meta package for the popular mozilla web bro
un  firefox-2      <none>         (no description available)
ii  firefox-3.0    3.0.5+nobinonl safe and easy web browser from Mozilla
pn  firefox-3.0-gn <none>         (no description available)
pn  firefox-gnome- <none>         (no description available)
un  firefox-granpa <none>         (no description available)
un  firefox-granpa <none>         (no description available)
un  firefox-libtha <none>         (no description available)
un  firefox-trunk  <none>         (no description available)
un  firefox-trunk- <none>         (no description available)

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> Sorry ... I seem to have missed that one.... Which error message exactly?

When I click on FF it gives me the error:
Could not launch application
Failed to execute child process "firefox" (No such file or directory)

---

### Post by Defrector on 2008-12-24
What happens when you enter this in the terminal:

```
cd /usr/bin

ls -A | grep "firefox"
```


if you get results listing 'firefox' try:
```

exec /usr/bin/firefox
```

and/or

```
exec /usr/bin/firefox-3.0
```

and share the output if there is any, or if the line with "grep" doesn't return anything.

---

### Post by cabbiinc on 2008-12-24
> **Defrector said:**
> What happens when you enter this in the terminal:

```
cd /usr/bin

ls -A | grep "firefox"
```


if you get results listing 'firefox' try:
```

exec /usr/bin/firefox
```

and/or

```
exec /usr/bin/firefox-3.0
```

and share the output if there is any, or if the line with "grep" doesn't return anything.

sabryna@sabrynascomputer:~$ cd /usr/bin
sabryna@sabrynascomputer:/usr/bin$ 
sabryna@sabrynascomputer:/usr/bin$ ls -A | grep "firefox"
firefox
firefox-3.0
firefox.ubuntu
sabryna@sabrynascomputer:/usr/bin$ cd /usr/bin
sabryna@sabrynascomputer:/usr/bin$ 
sabryna@sabrynascomputer:/usr/bin$ exec /usr/bin/firefox
bash: /usr/bin/firefox: No such file or directory
bash: exec: /usr/bin/firefox: cannot execute: No such file or directory 
sabryna@sabrynascomputer:/usr/bin$ exec /usr/bin/firefox-3.0
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

And it's apparently still going. But the good news is that last command made my monitor flash and Firefox fired up. The bad news is that when I click the icon, it still gives the error code from before 
Failed to execute child process "firefox" (No such file or directory)

But I am typing from firefox in Ubuntu. Unfortunately I have to get some sleep. It's 3 am and the wife wont be none too pleased.

If you post anything else to try I will do it when I wake up.

---

### Post by Defrector on 2008-12-24
Great!:KS

What it is looking like is the program menu is trying to run 'firefox' but 'firefox-3.0' is the one we want to run apparently. I had a similar problem some months ago. Not sure where it comes from but it isn't fun when you're new.

If you're using gnome (you probably are), right-click on "Applications", select "edit menus", find the firefox program in there, edit that program so that it runs "firefox-3.0" in place of where it currently says "firefox" and hopefully you should be good.

I am a kubuntu user so my knowledge of gnome is limited, maybe scorp can help you from there on.

---

### Post by scorp123 on 2008-12-24
> **Defrector said:**
> but 'firefox-3' is the one we want to run apparently. And I bet it's "firefox-3.0" :D

BTW, is the package "firefox-3.0-gnome-support" installed? From the "dpkg -l" output it doesn't look like it. Can you install that one too please?
```
sudo apt-get install firefox-3.0-gnome-support
``` That too might take care of a few things.

---

### Post by Defrector on 2008-12-24
Edited, thanks

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> And I bet it's "firefox-3.0" :D

BTW, is the package "firefox-3.0-gnome-support" installed? From the "dpkg -l" output it doesn't look like it. Can you install that one too please?
```
sudo apt-get install firefox-3.0-gnome-support
``` That too might take care of a few things.

Ok here's what I got:
sabryna@sabrynascomputer:~$ sudo apt-get install firefox-3.0-gnome-support
[sudo] password for sabryna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libotr2 libntfs-3g16
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  firefox-3.0-gnome-support
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After this operation, 172kB of additional disk space will be used.
Selecting previously deselected package firefox-3.0-gnome-support.
(Reading database ... 132428 files and directories currently installed.)
Unpacking firefox-3.0-gnome-support (from .../firefox-3.0-gnome-support_3.0.5+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Setting up firefox-3.0-gnome-support (3.0.5+nobinonly-0ubuntu0.8.04.1) ...

The icon from the applications menu still gives me that error.
Failed to execute child process "firefox" (No such file or directory)

---

### Post by cabbiinc on 2008-12-24
> **Defrector said:**
> Great!:KS

What it is looking like is the program menu is trying to run 'firefox' but 'firefox-3.0' is the one we want to run apparently. I had a similar problem some months ago. Not sure where it comes from but it isn't fun when you're new.

If you're using gnome (you probably are), right-click on "Applications", select "edit menus", find the firefox program in there, edit that program so that it runs "firefox-3.0" in place of where it currently says "firefox" and hopefully you should be good.

I am a kubuntu user so my knowledge of gnome is limited, maybe scorp can help you from there on.

Defrector: Yes I'm using gnome (the agiled toed one).

So I did as you said and it's working. I guess we can call this one solved. But to be honest I still don't know how to install something. You guys had me doing so many commands I don't know which way is up. I guess that's just the nature of the beast.

---

### Post by scorp123 on 2008-12-24
> **cabbiinc said:**
>  The icon from the applications menu still gives me that error. Failed to execute child process "firefox" (No such file or directory) Can you please open a terminal and give me the output of these commands: ```
echo $PATH
```
```
which firefox
``` 

... If I had to guess I'd say there's something wrong with your $PATH settings, your "profile" or maybe file permissions. Since we already installed Firefox again I'd say we should slowly start to consider excluding it as being the reason for the problems here ... But I am confused though. :confused:

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> Can you please open a terminal and give me the output of these commands: ```
echo $PATH
```
```
which firefox
``` 

... If I had to guess I'd say there's something wrong with your $PATH settings, your "profile" or maybe file permissions. Since we already installed Firefox again I'd say we should slowly start to consider excluding it as being the reason for the problems here ... But I am confused though. :confused:

I did as Defrector asked and it worked. I had to remove the icon from the panel, then make the changes in the Apps panel, then re-insert to panel, but it worked and is working as it should.

But I'll humor you since you've stuck with me this far.

```
sabryna@sabrynascomputer:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
sabryna@sabrynascomputer:~$ which firefox

```
just gave me another line to put code on so I tried 
[HTML]sabryna@sabrynascomputer:~$ echo $PATH which firefox
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games which firefox
[/HTML]

Not sure if I'm doing it right.

---

### Post by scorp123 on 2008-12-24
> **cabbiinc said:**
>  echo $PATH which firefox That's two separate lines. "$PATH" is a system variable that defines in which location the system should search for a program when you specify its name as command. "echo" is a standard command that will print stuff, e.g. with 'echo $PATH' you tell your system to print that variable to the console so you can see the current value. Here on my system I get: ```
> echo $PATH
/home/sysadm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
```

The other command "which" asks the system which binary it would try to execute if you entered that name as command. An empty response means that there is no such program:```
 > which foo
``` ... will likely return nothing. So there is no such program with the name "foo" here.

Using valid names however should return the location of the program that would get executed if you had entered its name as command. e.g. "which firefox" should return the valid location of where the program is located:  ```
> which firefox
/usr/bin/firefox 
```

Just to explain a little what I tried here.

But glad it works now for you. And now try to get such support from Microsoft .... :D

---

### Post by cabbiinc on 2008-12-24
> **scorp123 said:**
> 

But glad it works now for you. And now try to get such support from Microsof .... :D

YEAH RIGHT!! HA HA HAA HAAAAAA :lolflag:

---

### Post by german640 on 2008-12-24
Just a bit of knowledge about how Linux in general works for curious people who want to know what all the previous commands where trying to acomplish:


In Linux everything is a terminal command. The menu items are "links" that just execute a terminal command.
There's a special environment variable called PATH, wich is just a list of directories where all your programs are stored, all the commands that you can type in a terminal are programs inside the directories of your PATH. If a program is not in your PATH, you need to specify the full directory name in order to execute it.

So, for your problem with the menu item "firefox" there could be two main reasons it didn't work: it was trying to run a non-existent program, or it was trying to run a program not in your PATH.
The command "echo $PATH" displays the list of directories where your programs are stored, and the most common one is "/usr/bin". So you just needed to search in the directory "/usr/bin" for all the programs with "firefox" in its name, and the command to list files is this one:

```
ls -al /usr/bin/*firefox*
```

The command "ls" means list, the option "a" means all the files including hidden ones, and the option "l" display the names in a vertical list, and most importantly, display the link targets. The asterisks around the name firefox display all the programs with firefox in its name.
For instance, here's the output of that command in my Ubuntu box:

```
root@aiur:~# ls -al /usr/bin/*firefox*
lrwxrwxrwx 1 root root 11 2008-12-23 22:15 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 31 2008-12-23 22:15 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.5/firefox.sh
root@aiur:~# 
```

As you can see, the program "firefox" is just a symbolic link to the program "firefox-3.0", and this one is another symbolic link pointing to the real program: ../lib/firefox-3.0.5/firefox.sh, or with the full path: /usr/lib/firefox-3.0.5/firefox.sh.
Please note that "/usr/lib/firefox-3.0.5" is NOT in the PATH.

So, the problem you experienced about a "command not found" even when you saw the program "firefox" installed was probably just a broken link, pointing to a non-existent program. 
You solved the problem by changing the command the menu item executes from "firefox" to "firefox-3.0", but if another programs use the command "firefox" they won't work. So, the elegant solution here would be to make the program "firefox" a symbolic link to "firefox-3.0", and you can do it with these commands:

```
cd /usr/bin
ln -s firefox-3.0 firefox
```

The first one is for positiong in the directory "/usr/bin", and the second one makes the actual link (ln for link), the option "s" meaning symbolic.

Please note that when you install programs from the Add/Remove menu item, from Synaptic package manager or from the terminal using "apt-get", the system makes all of these links and updates automatically, but when you install using "tar.gz" archives you must do it manually.

I hope this was helpul to understand problems about "installed but not installed".

:KS

---

### Post by cabbiinc on 2008-12-26
> **german640 said:**
> Just a bit of knowledge about how Linux in general works for curious people who want to know what all the previous commands where trying to acomplish:


In Linux everything is a terminal command. The menu items are "links" that just execute a terminal command.
There's a special environment variable called PATH, wich is just a list of directories where all your programs are stored, all the commands that you can type in a terminal are programs inside the directories of your PATH. If a program is not in your PATH, you need to specify the full directory name in order to execute it.

So, for your problem with the menu item "firefox" there could be two main reasons it didn't work: it was trying to run a non-existent program, or it was trying to run a program not in your PATH.
The command "echo $PATH" displays the list of directories where your programs are stored, and the most common one is "/usr/bin". So you just needed to search in the directory "/usr/bin" for all the programs with "firefox" in its name, and the command to list files is this one:

```
ls -al /usr/bin/*firefox*
```

The command "ls" means list, the option "a" means all the files including hidden ones, and the option "l" display the names in a vertical list, and most importantly, display the link targets. The asterisks around the name firefox display all the programs with firefox in its name.
For instance, here's the output of that command in my Ubuntu box:

```
root@aiur:~# ls -al /usr/bin/*firefox*
lrwxrwxrwx 1 root root 11 2008-12-23 22:15 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 31 2008-12-23 22:15 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.5/firefox.sh
root@aiur:~# 
```

As you can see, the program "firefox" is just a symbolic link to the program "firefox-3.0", and this one is another symbolic link pointing to the real program: ../lib/firefox-3.0.5/firefox.sh, or with the full path: /usr/lib/firefox-3.0.5/firefox.sh.
Please note that "/usr/lib/firefox-3.0.5" is NOT in the PATH.

So, the problem you experienced about a "command not found" even when you saw the program "firefox" installed was probably just a broken link, pointing to a non-existent program. 
You solved the problem by changing the command the menu item executes from "firefox" to "firefox-3.0", but if another programs use the command "firefox" they won't work. So, the elegant solution here would be to make the program "firefox" a symbolic link to "firefox-3.0", and you can do it with these commands:

```
cd /usr/bin
ln -s firefox-3.0 firefox
```

The first one is for positiong in the directory "/usr/bin", and the second one makes the actual link (ln for link), the option "s" meaning symbolic.

Please note that when you install programs from the Add/Remove menu item, from Synaptic package manager or from the terminal using "apt-get", the system makes all of these links and updates automatically, but when you install using "tar.gz" archives you must do it manually.

I hope this was helpul to understand problems about "installed but not installed".

:KS

Actually it was extremely helpful. Thanks. :)

---

