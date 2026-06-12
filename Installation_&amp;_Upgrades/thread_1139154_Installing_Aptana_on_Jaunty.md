---
title: "Installing Aptana on Jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by vhenry on 2009-04-26
Hi,

Upgraded from Intrepid to Jaunty, with no issues. But trying to install Aptana for my web development and not having any luck. I've tried options suggested here (for Intrepid) and on other forums, but still unable to run. I'm getting this error:

Hello,

I've followed all the instructions here (downloaded java, xulrunner 1.8x) and still unable to launch Aptana.
Error: An error has occurred. See the log file
/home/dreamdeep/Aptana Studio/.metadata/.log.

Bash file I use to launch Aptana:
#!/bin/sh
MOZILLA_FIVE_HOME=/usr/lib/xulrunner-1.8.1.3
if [ $LD_LIBRARY_PATH ]; then
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH
else
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME
fi
export MOZILLA_FIVE_HOME LD_LIBRARY_PATH
/home/dreamdeep/aptana/AptanaStudio -vm /usr/lib/jvm/java-6-sun/bin/java

When executing bash file in terminal, this info appears:
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

Any ideas?

---

### Post by afecelis on 2009-05-07
Follow this tutorial:
[http://forums.aptana.com/viewtopic.php?f=37&t=7147](http://forums.aptana.com/viewtopic.php?f=37&t=7147)

It did the trick for me on Ubuntu 9.04 64bit.  ;)

---

### Post by okenobu on 2009-05-28
I can confirm the tutorial works. This is what i did on jaunty x64:

1. Unpack [_aptana zip file_]("http://studio-download.aptana.com/linux-zip/Aptana_Studio_Setup_Linux_1.2.7.zip") to ~/.sys/lib/aptana
2. Unpack [_xulrunner 1.8.1.3 zip file_]("http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.1.3/contrib/linux-i686/xulrunner-1.8.1.3.en-US.linux-i686-20080128.tar.gz") to ~/.sys/lib/xulrunner.
3. Installed java32 bit runtime: apt-get install ia32-sun-java6-bin
4. Created a script ~/.sys/bin/aptana with the following code:

```
#!/bin/sh
MOZILLA_FIVE_HOME=/home/bla/.sys/lib/xulrunner
if [ $LD_LIBRARY_PATH ]; then
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH
else
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME
fi
export MOZILLA_FIVE_HOME LD_LIBRARY_PATH
~/.sys/lib/aptana/AptanaStudio -vm /usr/lib/jvm/ia32-java-6-sun/bin/java
```

It seems to be working OK.

---

### Post by sistarbliss on 2009-06-15
I am also attempting to run/install aptana.  I have a few questions.  The path ~/.sys/lib/aptana?  I'm wondering if /sys would be the same, as it does not have a dot in front of it.  Also, the sys folder does not have a lib folder contained within it.  Also, how do I create a proper script?  I followed the turorial from the forum, but wasn't quite sure how to make an executable file.  I just pasted the text into an editor, saved it as aptana and then right clicked on it and checked the executable box.  (? lol!)

I have the  ia32-sun-java6-bin installed.  

I do have a win vm, and could install it there most likely, but would rather not run it unless I absolutely have to.  Any help would be appreciated.  I apologize for being a newb. 

I'm running 64 bit jaunty.

This is the begining paragraph of what appears to be the last entry in the log.  I do have eclipse installed.

!ENTRY org.eclipse.osgi 2 0 2009-06-15 00:54:20.337
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-06-15 00:54:20.337
!MESSAGE Bundle [EMAIL="update@plugins/com.aptana.ide.xul_1.2.7.024774.jar"]update@plugins/com.aptana.ide.xul_1.2.7.024774.jar[/EMAIL] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2009-06-15 00:54:20.337
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

---

### Post by buddhaZA on 2009-07-01
Hey there guys/gals,

Im also trying to get Aptana installed on 32bit Jaunty, 

[quote=okenobu]I can confirm the tutorial works. This is what i did on jaunty x64:

1. Unpack [_aptana zip file_]("http://studio-download.aptana.com/linux-zip/Aptana_Studio_Setup_Linux_1.2.7.zip") to ~/.sys/lib/aptana
2. Unpack [_xulrunner 1.8.1.3 zip file_]("http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.1.3/contrib/linux-i686/xulrunner-1.8.1.3.en-US.linux-i686-20080128.tar.gz") to ~/.sys/lib/xulrunner.
3. Installed java32 bit runtime: apt-get install ia32-sun-java6-bin
4. Created a script ~/.sys/bin/aptana with the following code:
[/quote]

sistarbliss and I seem to have the same issue. Im not to sure how to get into ~/.sys/lib to create the aptana folder :-/ Can someone point me in the right direction? 

I tried browsing using /sys/ but there is no lib folder? So I dont take it we just create one? :P

Thanks for any help or pointers, because if I can get Aptana to work its really the last thing keeping me on windows ;)

---

### Post by utannheim on 2009-07-02
> **buddhaZA said:**
> 

Im not to sure how to get into ~/.sys/lib to create the aptana folder :-/ Can someone point me in the right direction? 

I tried browsing using /sys/ but there is no lib folder? So I dont take it we just create one? :P



~/ is tilde character and equates to $HOME e.g. /home/yourusername

The suggestion is to create a hidden directory (hence the leading dot) in your home dir. To be honest I think you can just put this anywhere, for example I tried it out by replacing ~/.sys/lib with /opt/devel

---

### Post by buddhaZA on 2009-07-02
thanks for the reply utannheim, that clears it up a bit :P

I will give that a try this evening when i get back home.

---

### Post by keyboardslave on 2009-07-06
hmm im having the same problem with the big error..

As to the above post to "install aptana", go alt+f2 type nautilus , then go Ctrl + H (shows hidden) , now just create the folders if there not there (right click) , if u put a . in front of a file name its hidden.
Ya you can put these files (urlrunner/aptana) anywere just make sure to edit the script you make to point to the right place and make sure to give the script execute permission. Best keep the script in bin though.
...

EDIT:
i Got it working with a tutorial here, but its for eclipse... still works.
[http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration#Eclipse_3.4_Instructions](http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration#Eclipse_3.4_Instructions)

---

### Post by buddhaZA on 2009-07-06
Well i managed to get it working in Jaunty following this tutorial: [http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23](http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23) even tho its for intrepid it worked 1st time 100%

:D

---

### Post by Charybdisz on 2009-07-19
Aptana 1.5 is out. All the tutorials on installing Aptana on Linux are now outdated, just follow these steps:

1. Download Aptana 1.5 for Linux as standalone version
2. Extract it
3. Run it

---

### Post by Luca_turicci on 2009-08-01
Hi there, i just downloaded the latest version of aptana, extracted it and ran it, it works perfect, but i still don't know how to put it in the menu bar. hopefully in a little while i'll get it running perfect

---

### Post by syed.rakib.al.hasan on 2010-08-29
i have been trying to install the latest aptana3.0 beta on Ubuntu10.04 Lucid Lynx........ 
i hava sun-java6-jdk installed in the system. 

i have just downloaded it......... extracted it.......... then how do i run it????
when i double click the file AptanaStudio3 from nautilus........ it says error, 

"Could not display "/usr/local/aptana/AptanaStudio3".
There is no application installed for executable files"

[IMG]http://i37.tinypic.com/2dqoxzm.jpg[/IMG]

---

### Post by syed.rakib.al.hasan on 2010-08-29
[SIZE=3]Alright,
[/SIZE][SIZE=3]_**[SIZE=4]i found the [/SIZE][SIZE=4]solution[/SIZE]**_ from another problem thread........ so dumb of me I didn't look it up in that thread at first.......

thanks to user: [WakkiTabakki]("http://ubuntuforums.org/member.php?u=701")

[/SIZE][[SIZE=3]**Re: There is no application installed for executable files**[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1366252")
[SIZE=3]The problem is that when you downloaded the file, it didn't get saved with executable permissions (which is by-design)... 
The somewhat cryptic message you get means that, since it's not allowed  to run the executable file, it doesn't know how to open it.

Give it exe-permissions:
1. Right-click the file and choose Properties
2. Click on the Permissions-tab
3. Mark the "Allow executing file as program" and then close 
4. Double-click the file again

Walaa!!!!!!


[/SIZE]

---

