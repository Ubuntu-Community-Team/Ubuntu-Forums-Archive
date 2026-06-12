---
title: "Anyone tried gClip?"
date: 2008-09-17
forum: General Help
---

### Post by JemW on 2008-09-17
Just tried this: [http://gclip.uhvo.org/](http://gclip.uhvo.org/) It will install on Hardy (with a struggle) but once there it's very nice. Trouble is: no keyboard shortcuts and I can't get hold of the developer to make suggestions. I believe his name is 'raimo' and is based in Finland.

Any thoughts or idea who this guy is?

Thanks

---

### Post by mb_webguy on 2008-09-17
I just use the glipper applet.  It's simple to use, it does just about everything I expect from a clipboard manager, and it's in the repositories, so there is no struggle involved in installing it.

---

### Post by JemW on 2008-09-17
> **mb_webguy said:**
> I just use the glipper applet.  It's simple to use, it does just about everything I expect from a clipboard manager, and it's in the repositories, so there is no struggle involved in installing it.

Except that glipper crashes on startup on a frequent basis, and glipper is no longer maintained. I've been through that loop, which is the reason I've looked at alternatives. I'm not the only one with glipper problems btw - search around for startup crashes...

---

### Post by mb_webguy on 2008-09-17
Glipper crashes because it tries to start before some of its dependencies, and it's an easy fix.  Open a terminal and type "sudo gedit /usr/lib/glipper/glipper" and add the following two lines at the beginning of the file, after the comments:```
#!/usr/bin/env python

# Glipper - Clipboardmanager for GNOME
# Copyright (C) 2007 Glipper Team
#
# blah, blah, blah...
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.
#

import time # <-- This line is new
time.sleep(8) # <-- This line is new.  Increase to 20 or 30 if 8 doesn't help

import gobject
gobject.threads_init()

```

And glipper has been maintained more recently than the gClip you linked to.  Glipper was last updated in August of 2007, while gClip was last updated in January of 2007.

---

### Post by JemW on 2008-09-17
> **mb_webguy said:**
> Glipper crashes because it tries to start before some of its dependencies, and it's an easy fix.  Open a terminal and type "sudo gedit /usr/lib/glipper/glipper" and add the following two lines at the beginning of the file, after the comments:```
#!/usr/bin/env python

# Glipper - Clipboardmanager for GNOME
# Copyright (C) 2007 Glipper Team
#
# blah, blah, blah...
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.
#

import time # <-- This line is new
time.sleep(8) # <-- This line is new.  Increase to 20 or 30 if 8 doesn't help

import gobject
gobject.threads_init()

```

And glipper has been maintained more recently than the gClip you linked to.  Glipper was last updated in August of 2007, while gClip was last updated in January of 2007.

Hey! Thank you very much! It does indeed work. Where were you when I was struggling with this? ;)

Having a similar issue with Pidgin in that it insists on autostarting with the contact list maximized. I'm making it sleep (which addresses the problem) by using a small script at startup instead of the executable itself. Can we do something as simple with Pidgin as with glipper rather than using a script?

P.S Contents of script:

#!/bin/bash
sleep 10
pidgin

---

### Post by mb_webguy on 2008-09-17
Try doing this...  In the terminal, type "sudo apt-get install pidgin-extprefs", then open Pidgin and go to Tools->Plugins, check the Extended Preferences plugin, click the Configure Plugin button, and check "Hide buddy list at startup".

Otherwise, you might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=639287").  Or [this one]("http://ubuntuforums.org/showthread.php?t=762956").

---

### Post by JemW on 2008-09-17
> **mb_webguy said:**
> Try doing this...  In the terminal, type "sudo apt-get install pidgin-extprefs", then open Pidgin and go to Tools->Plugins, check the Extended Preferences plugin, click the Configure Plugin button, and check "Hide buddy list at startup".

Otherwise, you might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=639287").  Or [this one]("http://ubuntuforums.org/showthread.php?t=762956").

Tried the extprefs before and tried them again now - no effect.
Unfortunately, neither did the suggestions at the two threads... :(

P.S The delay string: **sleep 10 && pidgin** works from the terminal but not as a command in the Sessions startup entry...

---

### Post by Oreo on 2008-10-27
Isn't someone going to update glipper?

I'm using Intrepid now (early). I realize I could modify the file (/usr/lib/glipper/glipper) where one can determine how long glipper will wait before starting. 
This doesn't seem to be working in Intrepid.

I have also used Data Desktop Manager in the past. It doesn't do what I want either.
I like how glipper will clean what I copy of formatting.

Surely if neither glipper or gclip is still being maintained, isn't someone going to do something else for Ubuntu?
Seems like a major shortcoming of Ubuntu.

Phil

---

### Post by ggerri on 2009-04-24
try parcellite :guitar: [http://parcellite.sourceforge.net]("http://parcellite.sourceforge.net")- also available in synaptic...

Regards
Gerald

---

### Post by raimo on 2009-07-14
> **JemW said:**
> Just tried this: [http://gclip.uhvo.org/](http://gclip.uhvo.org/) It will install on Hardy (with a struggle) but once there it's very nice. Trouble is: no keyboard shortcuts and I can't get hold of the developer to make suggestions. I believe his name is 'raimo' and is based in Finland.

Any thoughts or idea who this guy is?

Thanks

Hi JemW and all others!
I have many thoughts and one big idea who this guy is ):P

Yes I'm planning keyboard shortcuts all the time.
I think that keys will be there later of this year or
at least very early 2010. 
In that website is now email if You need something else.

br. THAT odd raimo ;) from Finland

[http://gclip.uhvo.org](http://gclip.uhvo.org)
gclip.mail(AT)gmail.com

---

### Post by Johann-1.0 on 2009-09-12
Thank you for the post. It works just fine. Does anyone know if there is another clipboard manager, but having "multiple" clipboards, like jedit (not gedit), that has a feature where i was able to manage multiple clipboards and select which one of them to use when I paste anything. It is very useful because I could use one clipboard, for example, with one word, and the others with other words and paste without looking for them in a list. I think I didn't made myself clear, but if you don't understand, please let me know it.
Regards.:)

---

