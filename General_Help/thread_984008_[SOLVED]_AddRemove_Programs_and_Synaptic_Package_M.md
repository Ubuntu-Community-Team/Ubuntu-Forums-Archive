---
title: "[SOLVED] Add/Remove Programs and Synaptic Package Manager"
date: 2008-11-16
forum: General Help
---

### Post by Trevness on 2008-11-16
Hey well ive used the search button and i didnt see anything about what i have so..Here

I go to Applications and i open Add/Remove Programs..it gives me this error


```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

Please tell me Step by Step instructions like...Click Applications--->Add/Remove Programs--> Blah blah blah And my other Error

When i open Synaptic Package Manager..this error comes up
i go to System---->Administration---->Synaptic Package Manager

```
E: Type 'For' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

Please Step by Step instructions Thank you           And if you guys wouldn't mind helping me to install Java Thanks Remember Step by Step instructions

---

### Post by drs305 on 2008-11-16
Open a terminal. Backup and open sources.list for editing:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit +56 /etc/apt/sources.list

```
This will take you to line 56. Place a # symbol at the start of the line or simply delete the line if you understand the error in the line. It could be a line with a single entry "For", in which case just delete the line. Save the file and close it.

If you are unsure what to do, post the sources.list contents here and we can look at it.

---

### Post by Trevness on 2008-11-16
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

For Ubuntu Hardy (8.04):
```

I dont know what to do now lol



Hey umm when i created a new Terminal..im trying to install Java right now i get this in my Terminal
> 
trevor@trevor-desktop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for trevor: 
E: Type 'For' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
trevor@trevor-desktop:~$ sudo apt-get install sun-java6-plugin
E: Type 'For' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
trevor@trevor-desktop:~$ sudo apt-get install sun-java6-plugin
E: Type 'For' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ sudo apt-get install sun-java6-plugin
E: Type 'For' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
trevor@trevor-desktop:~$

---

### Post by Peter09 on 2008-11-16
The last line in this file is wrong. 
> 
For Ubuntu Hardy (8.04):

edit the file and put a # infront of the line and try synaptic again.

---

### Post by Trevness on 2008-11-16
Thank you~!! You fixed my Synaptic Package Manager!!!! AND MY ADD/REMOVE PROGRAMSSS WOOOOT

Oh wait...When i open a Launcher i made..an Application Terminal

like it says

sudo trevor password: (i cant type anything here but its blinking)
(so i type my password here)
(i press enter quickly and it closes the terminal)

Wdf is wrong with that?

---

### Post by drs305 on 2008-11-16
> **Trevness said:**
> 
sudo trevor password: (i cant type anything here but its blinking)
(so i type my password here)
(i press enter quickly and it closes the terminal)

Wdf is wrong with that?

Ok, one problem solved. Now on to the next. What is the app you are trying to run and what is the command you entered in the command box in the launcher? If it is an app that runs inside a terminal, did you select "Application in terminal" in the 'Type' box?  If it runs outside a terminal, is the 'Type' showing "Application"?

As far as not seeing your password as you type it in for running sudo, that is a security feature.

---

### Post by Trevness on 2008-11-16
Alright..Well i right clicked my desktop----> Clicked create a launcher---->Clicked application in terminal---->Put the code sudo apt-get install sun-java6-plugin---->Clicked ok---->Opened it--->I clicked Open New Terminal and i put the code above in and its either i dont see my password being typed or its just not being typed at all...

And when it says sudo trevor password: (I hit enter here)
(Type my password quickly) (Hit enter again quickly)
(And it Closes)

And i got another problem...i was stuck in synaptic package manager downloading this Java...stuff..and i turned off my computer..turned it back on i was out of it..but now when i open Synaptic Package Manager..it says this

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


And if you could...tell me how i can install Wine..do i just use Add/Remove Programs?

---

### Post by Marius Derekus on 2008-11-16
Well i don't know about the other problems but i do know when you use the sudo command, you are required to type you password BUT you will not see it typing. Just make sure you don't make any mistakes when typing the password.

---

### Post by Marius Derekus on 2008-11-16
as for installing wine, you could either type "wine" in the synaptic pakage manager search then find the program and install it, or type```
 sudo apt-get install wine
``` 

but if synaptic isn't running, then this won't work.

---

### Post by Peter09 on 2008-11-16
Trevness - do not use the application launcher, its best to open a terminal

Applications->Accessories->terminal

type your command in there.

As for your error - the answer is in the error message

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

type
```
sudo dpkg --configure -a
```

in the terminal

---

### Post by Trevness on 2008-11-16
There is no Terminal in my Applications...
-------------------------------
Nvm found it its n Applications---->Accessories--->Terminal

Thanks..but when i type that sudo code in for Java this is what is in my terminal

> trevor@trevor-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-fonts (6-10-0ubuntu2) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.

Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by Peter09 on 2008-11-16
Re-edited my post to correct the menu description.

It should be Applications->Accessories->terminal

---

### Post by issih on 2008-11-16
I have no idea why you are creating a launcher to try and install a java plugin...that makes no sense to me at all. Launchers should be for things you want to do more than once surely?

Generally, It seems (and I'm sorry if I'm wrong here, and I certainly mean no offence) that you are not that familiar with command line tools.

Given that, I'd recommend using add remove and the synaptic package manager rather than using the terminal commands where possible.

First things first though...Read the error message you got:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

it is actually telling you what to do, open a terminal and copy the command:

```
sudo dpkg --configure -a
```

here you are running the command the error tells you to run, and we prepend the sudo command so that the process is run as the superuser.

You will be prompted for your password, DO NOT hit enter, just type your password (there will be no feedback as a security feature) and then hit enter. If you get it wrong it will say so and ask again (up to 3 times). If you get it wrong three times in a row just rerun the whole command and try again.

Running that command should get your system back into working order.

Now simply open synaptic package manager and search for java, then tick next to the appropriate packages and hit apply. Even easier just open add/remove and search for wine and tick next to that and hit apply.

If you want to know how use the terminal, open a terminal window.

In there you type something like this:

```
sudo apt-get install packagename
``` 

and enter your password as before.

to remove something its:

```
sudo apt-get remove packagename
```

hope that helps

---

### Post by Trevness on 2008-11-16
Edited my post Above^

When i try to install Wine..This is what is in my Terminal

> trevor@trevor-desktop:~$  sudo apt-get install wine
[sudo] password for trevor: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
trevor@trevor-desktop:~$ 



Also now when i did the other error...Where it told me to manually do it here is what is in my Terminal

> trevor@trevor-desktop:~$ sudo dpkg --configure -a
[sudo] password for trevor: 
dpkg: status database area is locked by another process
trevor@trevor-desktop:~$

---

### Post by Peter09 on 2008-11-16
Thats because you have an apt-get process still running, you can only run one apt-get (synaptic) at any one time. I guess you still have your previous terminal session open.

---

### Post by Trevness on 2008-11-16
Yeah my synaptic package manager was running and it was just sitting there i was installing all the Java stuff and it came to stop and i was sitting there for like 20 mins 

So i turned off my computer while it was still running and i turned it back on...Anyway i can fix this?

---

### Post by Peter09 on 2008-11-16
No you misunderstand - I suspect that when you tried the latest command, you still had the previous dpkg command active in a terminal. 

You need to finish that session before you start the new one. Close all your terminal apps and start with a new one.

---

### Post by Marius Derekus on 2008-11-16
If you were really desperate, you could go to packages.ubuntu.com for Wine. Just make sure you get all the dependencies.

---

### Post by Trevness on 2008-11-16
This is weird...I tried to install Wine  ..this popped up Look at the bottom

> trevor@trevor-desktop:~$ sudo apt-get install wine
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
trevor@trevor-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
trevor@trevor-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ 
trevor@trevor-desktop:~$ sudo dpkg --configure -a
Setting up wine-gecko (0.1.0-0ubuntu1) ...
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


---

### Post by Trevness on 2008-11-16
Java pops up? im guessing i did something wrong while installing in Synaptic Package Manager cause i was installing a bunch of Java things and when i try to Install something in a Terminal the Java stuff at the bottom pops up..and interrupts it

---

### Post by Peter09 on 2008-11-16
I would abort by typing ```
no
```

---

### Post by Trevness on 2008-11-16
Oh ok thanks!! im trying to get to play Runescape..so i tried to install a bunch of java stuff

---

### Post by Trevness on 2008-11-16
How do i..uhhh make this thread Solved?

---

### Post by Peter09 on 2008-11-16
Thread Tools, top right of thread.

---

### Post by Trevness on 2008-11-16
Thank you SOLVED

---

