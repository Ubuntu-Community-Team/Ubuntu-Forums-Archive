---
title: "Application does not auto start even though its in Startup Programs"
date: 2008-07-21
forum: General Help
---

### Post by Dixit on 2008-07-21
I installed IM-History application.  Now it automatically created a startup program in sessions, however it never runs.  I always have to manually use terminal to run "imh-tray-auto" command.  It just doesnt seem to run even though its listed and enabled in Startup Programs in Sessions.  What am I or this application doing wrong?

Upon further inspection this imh-tray-auto seems to be a script that runs the main application of imh-tray.  Here is the imh-tray-auto when I view it
```
#!/bin/bash

sleep 30

ps ax | grep -v grep | grep imh-tray || imh-tray&

```

Ive also tried to change the startup program to just call "imh-tray&" instead of the "imh-tray-auto" and still no go.  It just seems odd to me that I can simply open a terminal and just type "imh-tray&" and it runs just fine, I see the IM-History application go into my panel, right next to Pidgin.

And lastly IM-History install puts these executables/scripts in my ~/bin directory.

Thanks for any help here.
Dixit

---

### Post by sdennie on 2008-07-21
The "~" isn't interpreted for startup programs (at least not in the dialog you enter the command) so you'll have to explicitly say, /home/your_username/bin/name_of_the_script.

---

### Post by Dixit on 2008-07-21
Right, the command in the startup program is listed as you mentioned of "/home/username/bin/imh-tray-auto"

I was just meaning to say that the files are basically sitting in my /home/username/bin directory (~/bin).

Dixit

---

### Post by iaculallad on 2008-07-21
Or maybe, you missed giving the file an executable attribute:

```
sudo chmod +x /location/or/scripfile/here
```

---

### Post by Dixit on 2008-07-21
IM-History had a script to install the application, it created the /bin directory in my home directory and put the files there and also set them all to executable.  They all have -rwxr-xr-x, they are all chown to my username as well.  

If they were not set to executable, the technically I would not be able to run it from terminal just by entering say "imh-tray" without the quotes, no?

Dixit

---

