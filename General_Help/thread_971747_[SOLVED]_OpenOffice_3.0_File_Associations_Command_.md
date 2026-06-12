---
title: "[SOLVED] OpenOffice 3.0 File Associations Command help"
date: 2008-11-05
forum: General Help
---

### Post by dazzlindonna on 2008-11-05
Installed OpenOffice3 but did not uninstall OpenOffice 2.4 because I don't want to uninstall ubuntu-desktop, since I do want to upgrade to 8.10 soon.  So, I needed to create my own file associations.  Took a while but I finally figured out the path to find those was in /opt/openoffice.org3/programs so all is good there.

However, I have a shortcut (not sure that's the right word to us) to one particular spreadsheet in my panel that still opens in OO 2.4 because this is the command used to open it:

 ooffice -calc /home/me/Documents/myfile.ods

So what I need to know is what command to use to get it to open in OpenOffice 3.0 instead.  I imagine i need to change ooffice to something else - I guessed and tried ooffice3 but that wasn't right.  Any ideas?

---

### Post by jdackle on 2008-11-05
```
sudo dpkg -L <openoffice-package-name
``` (or ist it "-l"?) will give you the list of files in that package - look in the bin subfolder...
If you don't know the exact name of the openoffice package, just use:```
sudo dpkg -l office
``` (or is it "-L"... lol) which will display all packages containing "office" in their names.

---

### Post by dazzlindonna on 2008-11-05
Neither of those commands (regardless of upper or lower case L) help.  "No packages found matching office."

Anyone else?

(Oh, i also tried replacing ooffice with soffice but that didn't work

---

### Post by jdackle on 2008-11-05
Weird!...
Actually I remebered after posting you probably installed 3.0 from the OpenOffice.org's site installer, right?...
But then, you'd probably have the 2.4 version from Ubuntu's packages, no?...

Unless, which seems to be the case, none of the two versions come from a .deb package...
In that caee, dpkg won't be aware of them.

But, **IF you can execute OpenOffice.org 3.0** (i.e. w/o it being called to open a given file), THEN you can find the executable!
If you call 3.0 from the GNOME menu, you can look at its location with alacarte (GNOME menu editor). Just run alacarte, browse to wherever in the menu OOo **3.0** is located, right-click, Properties/Edit and you'll see the command-line for it. ;)

If you call 3.0 through some other method, you'll have to dig it somehow as I've told you above to find where the executable is located and what's its name.

If you can't run 3.0, I guess that pretty much leaves you in a dead-end. Sorry...

EDIT: Two directories local installers usually install their files:
/usr/local
/opt

---

### Post by dazzlindonna on 2008-11-05
Yes, I can execute 3.0 with no problem.  In fact, I had to manually edit the GNOME menu, so I already know that it is located in opt/openoffice.org3/program/soffice

But that doesn't help me figure out how to convert this command:
ooffice -calc /home/me/Documents/myfile.ods

to whatever command will successfully run that file in 3.0.

I assumed soffice -calc /home/me/Documents/myfile.ods or soffice -scalc /home/me/Documents/myfile.ods or ooffice -scalc /home/me/Documents/myfile.ods but none of those work.

---

### Post by jdackle on 2008-11-05
Oh, sorry, I misunderstood your question...

Have you tried:
```
/opt/openoffice.org3/program/soffice --help
```
?

OR... I remember calling specific parts of OOo like this in the past:
```
scalc /home/me/Documents/myfile.ods 
```

---

### Post by dazzlindonna on 2008-11-05
Woot! Your last message, while it didn't specifically help, it indirectly helped. 

/opt/openoffice.org3/program/soffice --help only opened up a blank OO3 doc, but that was enough to give me the idea to try this:

> /opt/openoffice.org3/program/soffice -calc /home/me/Documents/myfile.ods

That worked!

P.S. Now I'm thinking there's probably a way to associate "soffice" or "ooffice" with this path: /opt/openoffice.org3/program/soffice (will research)

P.P.S. A friendly openoffice person gave me the solution to associating soffice with the path - type the following in a terminal:

> (test -d ~/bin || mkdir ~/bin; cd ~/bin && ln -s /opt/openoffice.org3/program/soffice && ls -l ~/bin/soffice && which soffice)

So from now on, I can use this format: soffice -calc /home/me/Documents/myfile.ods

---

