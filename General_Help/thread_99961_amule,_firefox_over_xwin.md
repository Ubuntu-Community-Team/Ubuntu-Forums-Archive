---
title: "amule, firefox over xwin"
date: 2005-12-06
forum: General Help
---

### Post by cotn on 2005-12-06
Hello,

I'm trying to export an amule screen to an X-server like XWIN. A simple JPEG works fine, but when I try apps like Amule, openoffice or Firefox I get an error like: display: no decode delegate for this image format `/usr/bin/openoffice'.

My Xwin configuration: 

Sessions:
Connect Method: XDMCP
Session name: blaat
XDCM mode: Query
Host name: 192.168.0.2 (=windows)
Session Flags: Default
[*] Launch new window

Window:
Window mode: single
Backing store: When Requested

Display: 192.168.0.3 (=ubuntu)
Display numer: 0

Fonts: the standard XWIN Fonts. I guess this could be a possible problem.

Security:
X-Host list: 192.168.0.2
[*] acces control
[*] use XAuth

I call a XWIN instance with putty:
display /usr/bin/openoffice -display 192.168.0.2:0

I hope someone can give me a clue.

Thanks.

---

### Post by johndoe on 2005-12-08
[QUOTE=cotn]
I call a XWIN instance with putty:
display /usr/bin/openoffice -display 192.168.0.2:0

I hope someone can give me a clue.

Thanks.[/QUOTE]

Ok, let's start off with display.. 'man display' tells us that,

```

The  display  program is a member of the ImageMagick(1) suite of tools.
Use it to display an image or image sequence on any X server.

```

So you're asking it to display /usr/bin/openoffice - which is probably a binary executable file (ELF) or a shell script that calls one. Either way, not an image so the display command doesn't know how to handle it.

Try this instead..

```

~$ **export DISPLAY=192.168.0.2:0**
~$ **/usr/bin/openoffice &**

```

or
```

~$ **/usr/bin/openoffice -display 192.168.0.2:0**

```

Additionally, if you're doing this to run Amule as a dedicated server, you might want to take a look at [http://mldonkey.berlios.de/](http://mldonkey.berlios.de/) instead.

---

### Post by cotn on 2005-12-08
Okay this works !

Thanks. 

About the dedicated server, I'm still looking for the best and most flexible way to setup Amule for using it on multiple PC's in my network. I know this is not the most common solution to solve this, but I would like to know how I can export executional files for displaying it on other clients. So the first test object was Amule, because it would be the fastest solution for the already described problem.

For amule I'm certanly going to check the link that you suggested.

---

### Post by johndoe on 2005-12-09
Well, amule doesn't really work like that (IIRC). It's a GUI application and it's bound to the desktop environment/X display - and X doesn't really facilitate running X apps disconnected or moving them across displays.

If this is what you want I'd suggest taking a look at VNC. VNC wraps an X session and allows you to connect to and disconnect from it while persisting the state of the X session.

MLDonkey runs as a server process and allows multiple users to connect to it via GUIs, a web interface, telnet session, etc. Much cleaner solution.

---

### Post by cotn on 2005-12-09
Okay I understand what you mean but I don't think that (u)vnc is the most ideal way to manage AMULE downloads. This because I don't want give other network clients permission to access the Ubuntu desktop. Some reasons; VNC makes other client connections slow, amule eats recources enough, and I don't want others to mess around on the system.

I know, people messing around with Putty is also a possibility, but step 2 was finding a solution to start-up a x-win connection whithout using a command line interface. I was thinking about a batch or whatsoever.

Now I realise that it isn't possible to let one Amule instance serve more network clients, leaving it on the background doing its job. In any case not the way I described in the first place.

Indeed I think that MLDonkey is a more ideal solution.

---

