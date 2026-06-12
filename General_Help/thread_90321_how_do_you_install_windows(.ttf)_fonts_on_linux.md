---
title: "how do you install windows(.ttf) fonts on linux?"
date: 2005-11-14
forum: General Help
---

### Post by Nicktu on 2005-11-14
im haveing trouble installing the tahoma font on to unbuntu, i need it to run a game,  will someone please give me a better easier process of how to do this task! :KS

---

### Post by matthewv on 2005-11-14
You can install the msttcorefonts package:
```
sudo apt-get install msttcorefonts
```

---

### Post by Nicktu on 2005-11-14
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

this is what is saying when i type that in the terminal, any suggestions?

---

### Post by matthewv on 2005-11-14
[QUOTE=Nicktu]Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

this is what is saying when i type that in the terminal, any suggestions?[/QUOTE]
Do you have the extra repositories enabled?? msttcorefonts is not in the main, but in the multiverse repository

---

### Post by Nicktu on 2005-11-14
sorry im new at this, im not sure about the extra repositories can you please guide me where can i find it?

---

### Post by matthewv on 2005-11-14
[QUOTE=Nicktu]sorry im new at this, im not sure about the extra repositories can you please guide me where can i find it?[/QUOTE]
Here's what I think is the easiest way to do it. 
Start Synaptic: System --> Administration --> Synaptic Package Manager
Enter your password when required
Once in Synaptic, go to Settings --> Repositories
Click on the block labelled Ubuntu 5.10 "Breezy Badger" (Binary) 
Press the Add button. Select all the check boxes and select Ubuntu 5.10 "Breezy Badger" from the drop down box. Press OK and then OK again. Then press Reload in Synaptic.

---

### Post by Nicktu on 2005-11-14
i just did what you told me, and i got the same message when i put the code you just gave me into the command, im just trying to install one font, tahoma.ttf for steam 

this is what the directions from the site told me

"Steam requires the tahoma.ttf font. It is included in the Microsoft core fonts package.
The package name depends on the distribution.
Alternatively google for tahoma.ttf, download it and put it into your X Server fonts directory. (usually /usr/X11/lib/X11/fonts/truetype)"

---

### Post by matthewv on 2005-11-14
[QUOTE=Nicktu]i just did what you told me, and i got the same message when i put the code you just gave me into the command, im just trying to install one font, tahoma.ttf for steam 

this is what the directions from the site told me

"Steam requires the tahoma.ttf font. It is included in the Microsoft core fonts package.
The package name depends on the distribution.
Alternatively google for tahoma.ttf, download it and put it into your X Server fonts directory. (usually /usr/X11/lib/X11/fonts/truetype)"[/QUOTE]
You could keep trying to install the msttcorefonts package. Could you post the contents of your /etc/apt/sources.list file here??

EDIT: btw, I'm not sure that tahoma is even in the msttcorefonts package. You might be better off just googling for tahoma.ttf, and then copying it into /usr/share/fonts/truetype/

Alternatively, just follow the second part of the instructions from steam.

---

### Post by Nicktu on 2005-11-14
still not working....do you have aim? if so message me dvez43
please i think it would be more porductive

---

### Post by matthewv on 2005-11-14
sry.. i don't. I get what you mean though...
and, being in australia, its now 7.40, so I have to leave soon...

but, back to your problem...
I think it would help if you would just outline exactly what you have done so far...

What did you do, and what error messages you received... what exactly is still not working...

---

### Post by Jacky_J on 2005-11-14
you have to put tahoma.ttf in ~/.wine/drive_c/windows/fonts

enjoy

---

### Post by matthewv on 2005-11-14
[QUOTE=Jacky_J]you have to put tahoma.ttf in ~/.wine/drive_c/windows/fonts

enjoy[/QUOTE]
Aren't fonts in your wine directory just for programs running under wine... 
Or is steam running under wine (sry, got no experience with gaming)

---

### Post by sergiolib on 2005-11-14
EASY PEOPLE!!
I discovered this yesterday:
Go to terminal: nautilus fonts://

Just drag and drop your ttf's and Gnome works for you!!

Now you can enjoy...:rolleyes:

---

### Post by robenroute on 2005-11-14
[QUOTE=sergiolib]EASY PEOPLE!!
I discovered this yesterday:
Go to terminal: nautilus fonts://

Just drag and drop your ttf's and Gnome works for you!!

Now you can enjoy...:rolleyes:[/QUOTE]

Hmmm, when I type this in a terminal, I get an error message. However, when typing "nautilus fonts:///" (without the quotes, that is) "all" goes well, apart from the fonts actually getting installed! I've tried doing this as a normal users, as well as root (through "sudo nautilus..."). Both methods remain without the desired results.

Perhaps I'm overlooking something essential???

Rob

---

### Post by thechitowncubs on 2005-11-14
type fonts:// in the location field in nautilus

ctrl+l

---

### Post by sergiolib on 2005-11-15
[QUOTE=robenroute]Hmmm, when I type this in a terminal, I get an error message. However, when typing "nautilus fonts:///" (without the quotes, that is) "all" goes well, apart from the fonts actually getting installed! I've tried doing this as a normal users, as well as root (through "sudo nautilus..."). Both methods remain without the desired results.

Perhaps I'm overlooking something essential???

Rob[/QUOTE]
As gnome always tries to be a simple but powerful grafical eviroment, doesn't include this in any manual or tutorial, or maybe it does, I don't know:
in internet, two slashes means a protocol, as well as none (example fonts: == fonts://) but in gnome some of you will have to add another one (its not my case) because another one will mean root of that protocol.
{{correct me if i am wrong}}
Keep enjoying...

---

### Post by ksenos on 2005-11-17
OK, I am having the same problem here. In general it seems that most of the multiverse packages... are not there :confused: .

My /etc/apt/sources.list is the following:
```
ksenos@raziel:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://gr.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gr.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://gr.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://gr.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Thanks in advance

----------------------------------------------

Oops... I am a little confused with debian-like distros. It seems that I don't have multiverse on my config. I added the ' deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-backports main multiverse' line in the sources.list file and everything is good :D.

---

