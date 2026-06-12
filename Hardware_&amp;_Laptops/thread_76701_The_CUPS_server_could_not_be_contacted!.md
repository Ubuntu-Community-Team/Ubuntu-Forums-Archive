---
title: "The CUPS server could not be contacted!"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by libertyforever on 2005-10-15
Newbie here.  I installed Ubuntu months ago and even got the printer working - no problems and worked great!  (Even got gtkpod running!:D )  But now, out of nowhere, my printer won't print.  :confused:   In the print dialogue, it used to say "photosmart 7150."  Now it says "generic printer" and the drop-down window has no other options.  When I go to System>Administration>Printing, I get the error message "The CUPS server could not be contacted."  I also tried going to localhost:631, but Firefox tells me the following error, "The connection was refused when contacting localhost:631."  I'm very new to the shell commands.  Any thoughts?

---

### Post by pingswept on 2005-10-15
[QUOTE=libertyforever]Newbie here.  I installed Ubuntu months ago and even got the printer working - no problems and worked great!  (Even got gtkpod running!:D )  But now, out of nowhere, my printer won't print.  :confused:   In the print dialogue, it used to say "photosmart 7150."  Now it says "generic printer" and the drop-down window has no other options.  When I go to System>Administration>Printing, I get the error message "The CUPS server could not be contacted."  I also tried going to localhost:631, but Firefox tells me the following error, "The connection was refused when contacting localhost:631."  I'm very new to the shell commands.  Any thoughts?[/QUOTE]

A good shell command to start with would be:

ps -A | grep cupsd

This will list all the processes running on your machine, and then it will search through that list for "cupsd," which is the CUPS server that you are having trouble contacting.

If cupsd is not found among the processes listed, you can start it with (I think):

/etc/init.d/cupsd start

If you are using Breezy (although you mentioned you installed Ubuntu months ago, so maybe not), you could use the Services control panel as well.

---

### Post by libertyforever on 2005-10-15
Thanks for post.  I tried:
[COLOR="Blue"]ps -A | grep cupsd[/COLOR]
Nothing came up.  It just dropped me to another prompt line with no info in between.  I tried under root as well with same result.  So, I tried next suggestion: 
[COLOR="Blue"]/etc/init.d/cupsd start  [/COLOR]
This is what came up:
[COLOR="Blue"]bash: /etc/init.d/cupsd: No such file or directory[/COLOR]
I am running Hoary Hedgehog 5.04.  I manually looked under [COLOR="Blue"]/etc/init.d[/COLOR] and did not see a file named [COLOR="Blue"]cupsd[/COLOR], but found one called [COLOR="Blue"]cupsys[/COLOR].  Does this mean anything?  Thanks for being there!

---

### Post by pingswept on 2005-10-15
So cupsd is not running. (You can try just ps -A to see a list of all the running processes.) Cupsys is what you want. Try:

sudo /etc/init.d/cupsys start

After supplying your password, you should see something like this:

 * Starting Common Unix Printing System: cupsd
   ...done.

---

### Post by libertyforever on 2005-10-15
Well, I tried:
[COLOR="Blue"]ps -A[/COLOR]
I did not see [COLOR="Blue"]cupsd[/COLOR] or [COLOR="Blue"]cupsys[/COLOR] in the list.  I did see [COLOR="Blue"]init[/COLOR] and [COLOR="Blue"]inetd[/COLOR] though (not sure what difference that makes).  Then tried:
[COLOR="Blue"]sudo /etc/init.d/cupsys start[/COLOR]
It dropped me down to another command prompt line with no info between.  Maybe my cupsys file has been corrupted?  Can it be re-installed or updated through Synaptic Package Manager?  Thanks again for help.

---

### Post by libertyforever on 2005-10-17
Am I ever embarrassed!  In the process of trying to solve another problem, I discovered my stupidity.  I had removed xpdf from my computer and when I did this, I somehow took cupsys off my system too (or something like that - I'm certainly not claiming to know what I'm doing!).  Anyway, I reinstalled cupsys through Synaptic and my printer works again.  Pingswept was right, my cupsys wasn't on because it wasn't there!  Thanks for being there to help pingswept.  And thanks to all you out there who are willing to help us newbies!  :)

---

