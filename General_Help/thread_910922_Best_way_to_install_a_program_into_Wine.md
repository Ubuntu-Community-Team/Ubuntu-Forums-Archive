---
title: "Best way to install a program into Wine"
date: 2008-09-05
forum: General Help
---

### Post by stat30fbliss on 2008-09-05
Anyone got a good process for installing a program into wine?  I seem be having  some problems.

---

### Post by Lance423 on 2008-09-05
Depends on the app really. Most you can just install to the Wine "drive" the same you would in Windows and run. That's how I've always done it. Also, check the Wine AppDB to see if what you want to install is supported and if so how it runs.

---

### Post by Crafty Kisses on 2008-09-05
Not really, the command line?

---

### Post by stat30fbliss on 2008-09-05
I am having a herd time getting comfortable with the Folder layout with ubuntu, and am thus finding it difficult to neither install a program outside of add/remove under applications, and do not want to improperly lose some files deep in the file system.

---

### Post by Crafty Kisses on 2008-09-05
The filesystem is really easy, I think it's a lot easier than Windows. The package manager and the how it store things work really well together and for the past 3 years, I've been liking it a lot.

---

### Post by jerome1232 on 2008-09-05
Well wine is used to install windows programs.

Are you trying to install a windows program or a linux program?

What program exactly are you trying to install? Knowing that will help us help you. If you downloaded the file a link to the site would be helpful as well.

btw wine installs all of it's programs under ~/.wine  (~ stands for /home/user/)

edit: And I strongly agree with codename, the file hierarchy is very easy once you understand it I thought this was a good link on that subject [http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/](http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/)

---

### Post by stat30fbliss on 2008-09-05
No, it is a Windows Program.  I was trying to say that I have a hard time even installing a program into linux w/o the add/remove under apps, so going through that into wine, just seems over my head right now.  So I was curious if anyone might be able to lay out some way to effectively install say, InframView, or some other example.

---

### Post by jerome1232 on 2008-09-05
Installing windows apps is made very easy under wine.

First I would check [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if your program is one known to actually work with wine

If it on a cd you just pop the cd in, open it up, find setup.exe or autorun.bat, right click it, click open with, select wine. After that's It's just like installing under windows. If it's a downloaded .exe you should be able to just right click it and select open with wine.

As for installing programs outside of add/remove I've only had to do that a few times. If the program in question is just not avaible at all in the repos (add/remove) then try and find a debian package for it, like opera is opera_9.50b2-20080422.6-shared-qt_i386-en.**deb** any .deb is a debian package (installer) you can just double click those.

If the file is a binary you usually just make it executable (right click it, select permisions) then double click it to run it.

If it's source code (.tar.gz) you have to compile it, usually by extracting it, then carefully reading it's INSTALL file and following it's directions. You usually have to install a few development packages (-dev pacakges) and run a few commands it'll be laid out in the INSTALL file
[code]./configure
make
sudo make install[code]

hope I've cleared at least some of the mud for you, I wouldn't try compiling until you feel comfortable with linux and the command line though.

edit: If you do take a crack at installing from source, after installing keep your source folder around, you need it to uninstall the program you compiled. (using make uninstall)

---

### Post by stat30fbliss on 2008-09-05
ok, sure.  That deffinitely helps, for wine.

With Linux, for example, I just downloaded a version of Skype for linux.  So all I have is the skype-debian_2.0.0.72-1_i386.deb file on my desktop.

How do I install it?

---

### Post by Crafty Kisses on 2008-09-05
For Skype you should just be able to double click it, unless you have 64-bit then you have to add some sources.

---

### Post by stat30fbliss on 2008-09-05
It Came Back with

Error: Wrong Architecture 'i386'

---

### Post by jerome1232 on 2008-09-05
That means you have a 64 bit install, now I haven't used skype in awhile but I believe you can force it to install. The -i flag just means install, --force-architecture tells it to ignore the fact it's made for 32bit and install anyways.

```
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```

Just so you know skype is notorious for being a pain in the butt.
It doesn't play well with pulse audio, that's the sound server in Hardy. I've gotten it to work after some fiddling but it would always randomly refuse to work correctly. I've heard people have had better luck with their static oss version.

---

### Post by stat30fbliss on 2008-09-05
Here are my results from your code.

```
stat30fbliss@stat30fbliss-laptop:~$ sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
[sudo] password for stat30fbliss: 
dpkg: error processing skype-debian_2.0.0.72-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-debian_2.0.0.72-1_i386.deb
```


It sucks cause my G/F just moved to Cali, and we always use skype when talking over long distances.  I dont want to go back to windows just to talk(although I will if i have to), and she doesnt want to learn a new program!  :confused:

---

### Post by jerome1232 on 2008-09-05
Either I typo'd the name or you have skype in a different directory where is skype saved to? If it's on your desktop then

```
cd Desktop
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```

try just typing 

sudo dpkg -i --force-architecture skype

then hit tab twice it'll either auto compelete the name, list any .deb's that start with "skype" or do nothing indicating you are in the wrong directory and it can't find anything that starts with "skype"

---

### Post by stat30fbliss on 2008-09-05
That definitely did the trick.  

Thanks a bunch!

:guitar:

---

