---
title: "Fingerprint Function Creator"
date: 2009-07-30
forum: Hardware
---

### Post by schmidtbag on 2009-07-30
I proudly present 4 scripts which are what should give your fingerprint reader more functionality than ever made possible before by any OS, with the help of Wolfgang Ullrich's program, [FingerprintGUI]("http://www.pdfserver.net/fingerprint/index.php").  With a few key strokes and the touch a finger, you will be allowed to log into your favorite websites and games, or better yet, run any command or program with one of your fingers.

**What is FFC exactly?**
	FFC (the Fingerprint Function Creator) is a utility that assigns each of your fingerprints to a dummy, or fake account that it also creates.  You cannot log into this account, and it doesn't have any privileges to itself; it is owned by root.  The way fingerprint readers work in Linux is all of your fingerprints are scanned and stored in your home folder.  The data stored contains nothing but fingerprint information and really has no significance to whoever scanned it as long as it was scanned by the same username.
	Although it is convenient to be able to log into your computer using all 10 of your fingers, what is the likelihood of you actually doing that?  FFC moves the fingerprints that you don't prefer to login with into the dummy accounts.  When that particular fingerprint is scanned, the dummy account is then verified.

**How is FFC used?**
	FFC is used by separate "executors".  FFE (the Fingerprint Function Executor) is a very simple but powerful script that will run any program based on whichever finger you assigned the program to be run by.  FAPE (the Fingerprint Account/Password Executor) will log you into just about any program or game by typing out the account and password for you, so you don't have to memorize or type anything.  Both of these scripts are meant to be run from either a launcher or a keyboard shortcut.

**How is GSUA used?**
GSUA (Graphical Super-User Authentication) is a simple extension to KTSUSS, which is a graphical frontend to sudo.  GSUA is used the same way you would use kdesudo or gksu.  It is intended for desktop environments that may not have those programs, but if you have them, you do not need to use this program.

[SIZE="4"]**[Video Tutorial on how to use FFC ]("http://www.youtube.com/watch?v=KkP0J1YHhwI")**[/SIZE]

[SIZE="4"]**[Video demonstration of real life situations where the programs are used]("http://www.youtube.com/watch?v=WSt1t4oxAlY")**[/SIZE]

[SIZE="4"]**[Video Example]("http://www.youtube.com/watch?v=Yk9tdHtmSMU")**[/SIZE]

I welcome all questions and comments.  Please help support my efforts and spread the word about this.

---

### Post by rainwalker on 2009-07-31
This looks really cool, although I haven't tried it yet
Are there any other utilities for using fingerprint scanners in Ubuntu?

---

### Post by schmidtbag on 2009-07-31
fingerprintGUI (something that my stuff relies on) is pretty good - its the only thing that could get my fingerprint reader to actually work at all

---

### Post by rainwalker on 2009-07-31
> **schmidtbag said:**
> fingerprintGUI (something that my stuff relies on) is pretty good - its the only thing that could get my fingerprint reader to actually work at all

I'm actually currently in the search for ways to get my fingerprint scanner to work, though I'm not sure how successful I'll be since I have the AuthenTek 2810 one listed at [http://www.reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810](http://www.reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810)
I guess I'll give FingerprintGUI a try, though unless it provides a driver for pretty new hardware I doubt it will work; fprint seems to be the go-to solution for fingerprint readers in Linux.

---

### Post by rainwalker on 2009-07-31
It looks like FingerprintGUI uses fprint's drivers, so I don't see much point in reinventing the wheel :/

---

### Post by schmidtbag on 2009-07-31
Video now uploaded

---

### Post by schmidtbag on 2009-08-10
another video now uploaded

---

### Post by schmidtbag on 2010-01-13
Version 1.3 now available!  I'll be posting a video soon.  In version 1.3, you can now use FAPE to automatically log you into things.

---

### Post by schmidtbag on 2010-02-21
Version 1.4 now available, as well as a new video.

Version 1.4 fixed a couple of typos, fixes issues current user could encounter, and added GSUA

---

### Post by igor_k821 on 2011-02-20
Hello i have installed the ffc. When i run the ffc command in terminal this massage comes up :

Not all dependencies are satisfied.
Please read Chapter II of the manual.
FFC will now quit.

I'm Running ubuntu 10.10 32bit
The fingerprint reader is Upek eikon 
The Fingerprint GUI Version is 1.00

What am I doing wrong?
Is the Upek eikon compatible with ffc?  

Thanks to all helpers.

---

### Post by schmidtbag on 2011-02-20
i'm not sure, but it should be.  you need fingerprint GUI 0.11, and i think 0.12 might work but i'm not 100% sure.  version 0.13 and up do not work.  it shouldn't be too hard for me to fix this, but 0.11 still works pretty well for my program.

I haven't updated this program (or this post) in a long time, so I'm not sure if I posted the updated code and documentation on these forums.  check this out instead:
[https://sourceforge.net/projects/ffc-ffe-fape/](https://sourceforge.net/projects/ffc-ffe-fape/)


thanks for your interest, please let me know what you think or if you need more help!

---

### Post by igor_k821 on 2011-02-25
i downgraded the fingerprint gui to 0.11. now when i try to open the ffc in the terminal it say :

"Please enroll all of your fingers before you run this program"

and opens the fingerprint gui.

i did enroll **all** my 10 fingers but it still gives me that massage..what should i do?

thanks for the help!

---

### Post by schmidtbag on 2011-02-25
Did you enroll your fingerprints using fingerprint GUI or fprint_demo?  because fprint will not help.  Also, if you ran fingerprint GUI with sudo or su, then the fingerprints will be stored in the root folder.  run it as yourself, and then run ffc as yourself.  Also, in fingerprint GUI, use it's verify tool to see if it managed to scan your fingerprints properly.


Just as a heads up, I haven't used gnome in a very long time, so i'm not sure if the FAPE portion of the program will work.  It doesn't work in KDE 4 because KDE 4 forces control of windows you don't click on, which screws with the way FAPE is designed to work.  FFE will still work though.

---

### Post by igor_k821 on 2011-02-25
I did enroll the fingers in the fingerprint gui and i tried to open the ffc as myself and not as the root.

It gives me the message above.

---

### Post by schmidtbag on 2011-02-25
well did you run fingerprint gui as yourself as well?  FFC will refuse to work until theres a .fingerprints folder in your home folder with enrolled fingerprint files saved.  if you run fingerprint gui as root, it saves the fingerprints in the root home folder, not yours.  check if that folder exists and check its contents for .bir files.

this should work, i've tested it in fedora and debian.  i recently just installed arch and i haven't got to installing it there yet.

---

