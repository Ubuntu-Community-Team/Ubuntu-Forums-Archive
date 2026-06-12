---
title: "Change Language in login"
date: 2008-11-23
forum: General Help
---

### Post by Fearnley on 2008-11-23
Hey

I got a problem, please give me a hand. 

I am a norwegian user, so I got ubuntu set for norwegain language. 
So here is my problem:
I got a password with norwegian characters, like æ and å.
I know that weren't that smart, for now I can't login.
Because on the logon screen I can't tape æ and å, it's set on english
language. So all I get it's characters like ' and [] like that. 
It's so irritating. I can't understand how ubuntu can change language. 
Maybe I did it, I don't know. But I need help, please.
How can I choose norwegian language in the login. Which document or code(in Terminal) can I change to fix this problem?
Any solution to my problem?

---

### Post by geirha on 2008-11-23
I believe you need to set the correct keyboard setting in /etc/X11/xorg.conf, but it's hard to explain how to change it without seeing how the xorg.conf looks now.

So, another option is to set a different password. In the console run ```
passwd
``` to set a new password for your user, with only ascii characters.

---

### Post by Fearnley on 2008-11-23
the xorg.conf file:


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by geirha on 2008-11-23
Right, try changing ```
Option "XkbLayout" "us"
``` to ```
Option "XkbLayout" "no"
```. Then restart the login screen with ```
sudo /etc/init.d/gdm restart
```

---

### Post by Fearnley on 2008-11-23
Thank you. Now every things perfect. You saved my day.

---

### Post by IBTB on 2009-01-06
I can't seem to find this "xorg.conf" file.
Using a Ubuntu 8.10 server install and missing the letters æ, ø and å (norwegian letters).

I've been searching for some time without finding out how to change the language without the "visual ubuntu".

If anyone could give me a tip as well. It would be helpful :)

My problem is: I don't really know what language setting my computer has. And when running programs that uses norwegian letters I end up with coded replacements.

---

### Post by geirha on 2009-01-26
xorg.conf is located at /etc/X11/xorg.conf. If you are unable to get to it using the GUI, then hit Ctrl+Alt+F1 to get to a console terminal, log in there and type ```
sudo nano /etc/X11/xorg.conf
```

Do the changes and hit ^X to exit (^X means hit Ctrl+X)

Also check that keyboard layout «Norway» is set to default under System -> Preferences -> Keyboard once you are logged in with Gnome.

---

### Post by IBTB on 2009-02-11
The thing is, I'm not using any GUI.
This computer stands as a server and I only connect trough SSH.

And this is my content in /etc/X11/ :
Xresources  Xsession  Xsession.d  Xsession.options  Xwrapper.config  xkb

No xorg.conf file :confused:

---

### Post by geirha on 2009-02-12
What ssh client are you using?

---

### Post by IBTB on 2009-02-12
PuTTY.

Could that be the problem?

---

### Post by yther on 2009-02-12
> **IBTB said:**
> PuTTY.

Could that be the problem?

Maybe it is, but indirectly.  PuTTY is a terminal program, so I'm guessing you're trying to connect in a text window.  If you can't type those characters then I think you need to change the keyboard layout *on the computer you're trying to connect from*.  Another possibility is that you need to change some option in PuTTY that affects your keyboard.  I haven't used that program in ages and don't have it handy, so that's probably not much help.

Was that any use?

---

### Post by IBTB on 2009-02-12
I've tested my PuTTY on another server now. There everything works fine.

So it's not that.

The wierd is, that when I type my letters "æ ø å" they appear only when I hit the next character, like when using ^, you have to push space or any other button to get it to show.

And another problem, is when I'm using pico to write files, and I use the letters æ, ø or å. It shows as "ï¿½ï¿½" or something (shows as "æ" on the web-page) but only uses the space of one letter. hard to explain, but it makes it hard to re-write anything, because the "ï¿½ï¿½" pushes all the text x "spaces" to the right, but the text itself only contain one. So if I erase something further to the right in the text, I end up erasing something completely else.
This was hard to explain.... :P But if you understand any of if, any suggestions are welcome! ;)

---

### Post by geirha on 2009-02-12
[http://www.linuxquestions.org/questions/linux-general-1/putty-and-character-encoding-problems-281945/](http://www.linuxquestions.org/questions/linux-general-1/putty-and-character-encoding-problems-281945/)

Check that putty is using UTF-8.

---

### Post by IBTB on 2009-02-12
It was not set to UTF-8, but when I changed it, nothing changes. Still the same deal.

I think I need to set the "language" on the server, and since every user is norwegian it ain't no problem. The only problem is that none of us knows how! :P

How to set the norwegian language on the server itself?
Where is the file that keeps that information?

And thanks for your replies! :)

---

### Post by geirha on 2009-02-12
> **IBTB said:**
> It was not set to UTF-8, but when I changed it, nothing changes. Still the same deal.

I think I need to set the "language" on the server, and since every user is norwegian it ain't no problem. The only problem is that none of us knows how! :P

How to set the norwegian language on the server itself?
Where is the file that keeps that information?

And thanks for your replies! :)

I don't think the server's language is a problem, but typing "locale" should list the locale variables currently set. LANG would be the most important one. "locale -a" will list all locales available.

"export LANG=nb_NO.utf8", if that locale is available, should set the language to norwegian bokmål in the current shell (not permanently). If it happens to work, you'll want to edit /etc/environment to make it permanent.

EDIT: Btw, I did a little testing just now. If I set my gnome-terminal's character encoding to ISO-8859-1 and type æ, it will not show, but if I type a space, it shows an æ, and if I type another space I get two spaces, which I believe is the same as you described earlier. I really think putty is using the wrong character set. 

You said putty worked against another server. Check what character set that server is using with the locale command.

---

### Post by IBTB on 2009-02-15
When using the export command as you say, I manage now to write æøå in pico atleast. And that's really all I need. So so far, so good!
But when it comes to changing it permanently, I'm stuck again.

This is how my /etc/enviroment file looks like:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"


Do I then add the export command there, or how does this work?

Thanks again,
IBTB

---

### Post by geirha on 2009-02-15
My /etc/environment looks like this:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="nb_NO.UTF-8"
LANGUAGE="nb_NO:nb:no_NO:no:nn_NO:nn:en_GB:en"

```

---

### Post by IBTB on 2009-02-15
Okey, I've added your 2nd and 3rd line. But they won't take effect untill after a reboot I guess. So I'll post back then with results! :)

---

### Post by Harlyman on 2009-03-05
hey

i have the same problem after i installed 8.0.4 on 2 of my servers, i know i had problems with this before, and it was a easy solution but i just can't figure out what it is, have done what all of you here has tested but with no luck, i dont use putty but sshclient as my terminal

any other ideas??

BTW: i can type æøå chars direct into terminal but not if i use an editor, also apache2 does not display this chars typed into files, but all texts from db is all ok

---

