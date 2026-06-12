---
title: "Canon PIXMA iP4500 and ddiwrapper"
date: 2009-01-02
forum: Hardware
---

### Post by Bobby Infinity on 2009-01-02
Happy New Year. I have a Canon iP4500 that Ubuntu recognizes immediately upon plugging in but that I can't get to print at its highest resolution (9600 x 2400 dpi). I have tried the 2.80 .deb drivers from the canon site. They installed fine but still only 600 x 600 dpi. I then edited the ppd file adding entries to allow for increasing the resolution via the print dialogue; all the does is cause the print job to fail. I tried the Guetenprint driver and that to only gave me 600 x 600. I tried Turbo Print but I didn't care for that at all and it also failed at higher resolution. 
Through googling, I found a project called ddiwarpper. It's the same premise as ndiswraper in that you can use Windows drivers to get printers to play nice with linux. I found the source code [here]("http://www.linuxprinting.org/download/ddiwrapper/")(linuxprinting.org). My problem is that there is no ./configure file and I can't figure out how to compile without it. Could someone please help?

---

### Post by spotteddog on 2009-05-08
Bobby,

Did you ever get your iP4500 working? I have the same printer and can't get full functionality either.

---

### Post by Bobby Infinity on 2009-05-08
Nope. Just basic functionality.

---

### Post by karesz on 2009-08-08
The same here, but havent tried the ddiwrapper. Any improvement yet?

Edit: ddiwrapper seems to be abandoned :(

Edit2: Nope... it doesn't seem to be working. Not even a single test page made it through. Seems like the job is sent, but nothing happens. Nothing.

It would be really nice, if somebody could help!

---

### Post by holiday on 2010-11-11
> **karesz said:**
> The same here, but havent tried the ddiwrapper. Any improvement yet?

Edit: ddiwrapper seems to be abandoned :(

Edit2: Nope... it doesn't seem to be working. Not even a single test page made it through. Seems like the job is sent, but nothing happens. Nothing.

It would be really nice, if somebody could help!

Has there been any development on this?

---

