---
title: "Execute Script without Prompt"
date: 2008-08-01
forum: General Help
---

### Post by mreynaga on 2008-08-01
I made a script to launch a ripped movie i have on my hard drive in Xine so that i dont have to manually open Xine or launch it from the Terminal however when i run the script i get the prompt asking if i want to "Run in Terminal, Display, Cancel, or Run" and i was wondering if there is a way to just force it to run everytime without asking that. 

the script works regardless of whether i run in terminal or just run so i dont care which option i just dont want it to ask.

thanks

---

### Post by y-lee on 2008-08-01
I think you can make a launcher for it and it should work ok.

or you could open nautilus and in menu edit preferences and then click the behavior tab and check the Run executable files. This would of course run all bash scripts when they were clicked but that may be what you want. I wouldn't like it tho. lol.

or ya could wrap the script in python and run it that way or rewrite it in python or another programming language.

hope this helps and peace.

---

### Post by drs305 on 2008-08-01
You can probably get it to run in with a script/launcher if you use the "xine -p" switch.

For more info, "xine --help" or here is one link:
[http://dvd.sourceforge.net/xine-howto/en_GB/html/howto-4.html]("http://dvd.sourceforge.net/xine-howto/en_GB/html/howto-4.html")

---

