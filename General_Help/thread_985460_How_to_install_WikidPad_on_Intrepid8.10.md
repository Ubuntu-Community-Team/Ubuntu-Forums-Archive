---
title: "How to install WikidPad on Intrepid/8.10"
date: 2008-11-17
forum: General Help
---

### Post by SteveDee on 2008-11-17
I've been using WikidPad on Windows for about 18 months to keep track of projects, especially ones which get put to one side to be picked up at a later date.
I like WikidPad because its quick & easy to add text & web links, and it saves wiki data to a single file.
I also use Christian Ziemski's "ToDo" extension ([http://www.ziemski.net/wikidpad/todo_extension.html](http://www.ziemski.net/wikidpad/todo_extension.html)).

Although primarily designed for Windows, I'm happy to say it also works on Intrepid (just as well, as both my home computers are now exclusively Linux).

Method:-
Download the V1.9 source from here: [http://wikidpad.sourceforge.net/](http://wikidpad.sourceforge.net/)
(Don't use the V1.8 source as there is a "copy & Paste" problem when running this on Linux).

Unzip and save all files & folders to a suitable location (e.g. /home/steve/wikidpad)

Open a terminal window & type:-
	CD /home/steve/wikidpad
	python WikidPad.py

If you get a "no module named wx" error, use Synaptic to install python-wxgtk2.8 (and accept any dependancies).

Back in the terminal window, type:-
	python WikidPad.py

Hopefully WikidPad should now run OK.

Close WikidPad and create a script in your text editor:-
	#!/bin/bash
	cd /home/steve/wikidpad
	python WikidPad.py

Save script (into wikidpad folder) as RunWiki and make the file executable (e.g. in Nautilus right click, Properties > Permissions > Execute). You can now create a application launcher to run RunWiki.

The "ToDo" extension is added by simply downloading Christian's python script and adding this to a new folder (user_extensions) as described on his web page.

---

