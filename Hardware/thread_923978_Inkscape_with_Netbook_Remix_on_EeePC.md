---
title: "Inkscape with Netbook Remix on EeePC"
date: 2008-09-19
forum: Hardware
---

### Post by roncrump on 2008-09-19
Hi,

I have Ubuntu 8.04.1 installed on my EeePC 901, with [Adamm's custom kernel]("http://www.array.org/ubuntu"), scripts to help with acpi issues and the Netbook Remix.

With the Netbook Remix, the Maximus package attempts to start any application in maximised mode, thereby helping use the screen real estate better.

This does not seem to work in Inkscape, which starts small and offset. I cannot get it to maximise once it has started so it is pretty much unusable in this environment.

I think this may be due to Inkscape storing window size parameters for the default document somewhere in .inkscape/preferences.xml, but I'm not sure what to change.

Anybody got any suggestions? Either as to the change to make in the Inkscape preferences or alternative fixes.

Cheers,
Ron.

---

### Post by Aearenda on 2008-09-19
Inkscape starts all right on my system running NBR, but my screen is conventional (1024x768 ) so maybe that is why.

Inkscape has window geometry preferences available if you can get to the file menu.

You could try just renaming the .inkscape folder in your home directory so that it creates a new default one, and see what happens. You can delete that and rename the original back again after the test if you have customised it heavily.

Also, there is an exclusion key for Maximus in gconf-editor - so that it will ignore awkward programs. I use this with Vym. Look in apps->Maximus, and try adding Inkscape to the exclude list.

---

### Post by sloggerkhan on 2008-09-19
I have an aspire 1 and similar issues. I think a bug needs to be filed with inkscape project. What I think is happening is that the left hand tool pallete is too tall for the screen and can not be positioned different, so it always starts out standard size and too big yet too narrow.

---

### Post by Aearenda on 2008-09-19
I have just tried unmaximising it and then resizing the window. It refuses to go smaller than the size of the left-hand toolbar, unless that toolbar is undocked. I have just tried it on my Aspire One, and it does maximise properly when that toolbar is undocked. I then unmaximised it, resized the window so that it will fit on the screen, leaving a space to the left for the undocked toolbar, and it seems happy. You can prevent Maximus from maximising it as I described in post #2.

EDIT: Unfortunately Inkscape doesn't remember that the toolbar was undocked, so it has to be undocked each time the program is started, after which the window can be resized.

EDIT2: It's bugged in Launchpad already. See [https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/213140](https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/213140)

EDIT3: See also bugs #208079, #168648 and #221676.

---

