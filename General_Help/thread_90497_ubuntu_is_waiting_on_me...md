---
title: "ubuntu is waiting on me.."
date: 2005-11-15
forum: General Help
---

### Post by hickoryknot on 2005-11-15
Hello everyone....I installed 5.10 of Ubuntu and when I boot up it asks for my name and password...I do that... then it comes up with this  joseph57@ubuntu:~$
I don't know what it's asking for so I don't know if I really have much of a problem or not....I would appreciate if someone could shed some light on this for me...I tried the live cd first and had no problems there....
Thanks and good morning to everyone....

---

### Post by pickarooney on 2005-11-15
Is the screen asking for your password completely black? Or brown, with the Ubuntu logo?
Once you've logged in, have you a graphical interface (toolbars, desktop etc.) or just a completely black screen?

If you've no GUI, type **startx** and see what happens.
If you have a GUI, what exactly is your question? :)

---

### Post by hickoryknot on 2005-11-15
It's the black screen with white letters........I do log in ....after I put in my password and hit enter and then it comes up with this...
joseph57@ubuntu:~$
It never gets to the stage with the graphical interface

---

### Post by pickarooney on 2005-11-15
Ok, try typing **startx** and see if the GUI starts up.
If not, what kind of errors are you getting?

---

### Post by soonindallas on 2005-11-15
did you try the suggested keyboard entry ?

[QUOTE=pickarooney]
If you've no GUI, type **startx** and see what happens.
[/QUOTE]

---

### Post by hickoryknot on 2005-11-15
I'll try that...... soon have to leave for work but I'll come back to the forum this evening........gonna try that now tho....thanks

---

### Post by hickoryknot on 2005-11-15
I tried startx to no avail......anyone have an idea of my situation?

---

### Post by az on 2005-11-15
type
sudo apt-get install ubuntu-desktop

Your installation is incomplete.  That command will install the needed packages.  If it gives you an error, try

sudo apt-get -f install


or follow its' instructions

---

### Post by hickoryknot on 2005-11-15
I will try that......but I'm not getting any instructions.....it's like a prompt waiting for me to do something......

---

### Post by hickoryknot on 2005-11-15
I tried sudo apt-get -f install..... it didn't help

---

### Post by garba on 2005-11-15
mmm try this:

sudo /etc/init.d/gdm

this is the proper way to start the login manager, let us know what error message you get if any

---

### Post by SickTwist on 2005-11-15
[QUOTE=garba]mmm try this:

sudo /etc/init.d/gdm

this is the proper way to start the login manager, let us know what error message you get if any[/QUOTE]

One must indicate to start or restart gdm:

sudo /etc/init.d/gdm restart

---

### Post by jdong on 2005-11-15
also do a **sudo dpkg-reconfigure xserver-xorg** and reboot.

---

### Post by krye on 2005-11-15
Can you post the output of the **startx** command?

---

### Post by hickoryknot on 2005-11-15
anyone have any ideas what I can do?  The live cd worked fine........

---

### Post by hickoryknot on 2005-11-15
I typed sudo /etc/init-d/gdm     command not found
" "       sudo /etc/init-d/gdm restart       command not found
" "       sudo dpkg-reconfigure xserver-xorg        is not installed

---

### Post by az on 2005-11-15
[QUOTE=azz]type
sudo apt-get install ubuntu-desktop
[/QUOTE]


Do that.

---

### Post by jdong on 2005-11-15
Azz's advice is correct -- your X server (graphical environment) was somehow lost during the upgrade. Installing **ubuntu-desktop** will bring it back.

---

### Post by garba on 2005-11-16
[QUOTE=SickTwist]One must indicate to start or restart gdm:

sudo /etc/init.d/gdm restart[/QUOTE]

yep silly me :rolleyes:

---

### Post by hickoryknot on 2005-11-17
I tried your suggestions and it worked.....for some reason the environment didn't install.....but it's there now....
I certainly thank you for your help.....
I'm really liking what I'm seeing....now I"m trying to figure out how to get online...I use netzero dialup..I went to netzero's website and it shows compatibility with a version called "Lindows" and "Linspire" ....

---

### Post by the_it on 2005-11-17
didn't see page 2, never mind

---

### Post by az on 2005-11-17
[QUOTE=hickoryknot]I tried your suggestions and it worked.....for some reason the environment didn't install.....but it's there now....
I certainly thank you for your help.....
I'm really liking what I'm seeing....now I"m trying to figure out how to get online...I use netzero dialup..I went to netzero's website and it shows compatibility with a version called "Lindows" and "Linspire" ....[/QUOTE]
Linspire is Debian-base like Ubuntu.  This means that whatever gets you onlie with Linspire may work with Ubuntu.  Try it out.

Now, what kind of modem do you have?  If it is a software modem, it will be a headache, since the modem manufacturers and vendors do not care about your freedom to chose an OS.

Software modems are one of the areas that have weak free-libre software support.

---

### Post by jdong on 2005-11-17
[QUOTE=azz]
Software modems are one of the areas that have weak free-libre software support.[/QUOTE]

Not to mention that their stability and performance are so crappy (usually) that it's not worth the effort to deal with them, espeically if dial-up is your primary form of internet access.

---

### Post by az on 2005-11-17
[QUOTE=jdong]Not to mention that their stability and performance are so crappy (usually) that it's not worth the effort to deal with them, espeically if dial-up is your primary form of internet access.[/QUOTE]
Actually, I have an AMR modem that is supposed to be software-upgradeable (it's performance depends on the driver)  There has not been (nor will there ever be) a v.92 version for it in any version of windows, but the linux sl-modem driver runs it at v.92 speeds.

The Lucent drivers are also very good.  I have never seen a lockup happen with it in linux.

Conversely, I had a 3com software modem lockup in windows consistently - and 3Com are the top-notch modem vendors.

It is hard to estimate the CPU consumption in comparison to Windows, but I guess they are about the same.

I was on dialup until last year.

---

### Post by jdong on 2005-11-17
[QUOTE=azz]
The Lucent drivers are also very good.  I have never seen a lockup happen with it in linux.
[/quote]
I agree -- Lucent/Agere Winmodems (1648 series) and the Softmodem series are both excellent in performance and reliability, though there is a 1-second or so system hang whenever the modem goes on-hook or off-hook (at least under Windows). While this may seem like no big deal, there are some activities (burning CD/DVD's for example) that cannot withstand a 1-second complete lockup during critical phases.

> 
Conversely, I had a 3com software modem lockup in windows consistently - and 3Com are the top-notch modem vendors.

3Com/USR nerds (like me) will tell you that ever since the merger of the two, their quality has plummeted. Pre-merge flash revisions are the holy grail of 3Com/USR modems.

Note that modern 3Com WinModems are actually Conexant SoftModems in disguise -- and Conexant modems are the absolute rock-bottom of all 56K's.

> 
I was on dialup until last year.
I used to be a dial-up nerd a few years back... You know, one of those who can identify the brand, model, firmware revision, and rough connect speed just by listening to a handshake?  ;)

---

### Post by hickoryknot on 2005-11-18
Good morning all....
I'm trying to get online in Linux....While in Windows I went to Netzero's website, downloaded and saved the needed software to connect in Linux but when I go to Ubuntu it can't open the file.....First I saved the file on a cd using "Easy CD Creator" ....then I tried to use floppy's but the file is too big...finally I used my thumb drive...I would appreciate it someone has an idea on what I can do...

---

### Post by PsychoTrauma on 2005-11-18
What type of package did you download from netzeros site? Please give the filename and extension.

---

### Post by hickoryknot on 2005-11-18
with netzero you have to install an app in order to get online with them....the one for linux is     netzero.deb

---

### Post by PsychoTrauma on 2005-11-18
Open a terminal and cd into the directory you have the netzero.deb.

then do: 
```
sudo dpkg -i netzero.deb
```

Hopefully you'll get no errors and it will install.

---

### Post by hickoryknot on 2005-11-19
I tried it......It gives me an error and still can't open the file

---

### Post by az on 2005-11-19
Please be more verbose.

What error?

---

### Post by hickoryknot on 2005-11-19
with the netzero.deb icon on my desktop I opened up a terminal and typed...
**sudo dpkg -i netzero.deb**
here is what I got...
[B]dpkg: error processing netzero.deb (--install):
cannot access archive: No such file or directory
errors were encountered while processing: netzero.deb[/B]

---

### Post by AlexMR on 2005-11-19
Hello hickoryknot,

if you&#180;re having the file on the desktop, it&#180;s inside the /home/<youruser>/Desktop-folder.

Open up a console and type

cd Desktop

then try again installing the package with

sudo dpkg -i netzero.deb

Now it should work (if no dependencies required).

Greets,
Alex.

---

### Post by az on 2005-11-19
or
sudo net*.deb in case that is not the exact filename.

---

### Post by hickoryknot on 2005-11-19
ok..I did what Alex suggested....It did install but nothing happened after that....possibly I just don't know what to do next or where to look.....
I did look around and find the "Synaptic Package Manager"
I looked in there and found netzero..
I clicked "properties"
then "Dependencies"
here's what it said..
Depends : libcle (>=2.3.2-1)
Conflicts : lindowsos-dialer-netzero
Replaces : lindowsos-dialer-netzero

I sure appreciate you guys helping me...

---

### Post by az on 2005-11-19
In synaptic, open that properties box and find the list of files in the package.  Are there any files there that start with /usr/bin, or /bin or /usr/sbin or /sbin?  Anything put in those directories would be what you need to run.

Let's say that you fin /usr/bin/netzero-dialer

Then open a terminal and read the manual
man netzero-dialer


If that don't work, try lookin in the list of files for the documentation (/usr/share/doc/netzero....)  Maybe there is something helpful there?


The reason this is a pain is because that application is not open source.

---

### Post by hickoryknot on 2005-11-20
I found those types of files...couldn't get any to work tho....
However when I open the Synaptic Package Manager I get a window that says Problems found..
W: couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/
universe Packages (/var/lib/apt/lists/
archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i 386_packages) -stat (2 No such file or directory)

could this be part of my problem?

---

