---
title: "32/64 bit problem"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by aosgd on 2009-11-06
Well...

I'm having a problem trying to install 32 bit.  This isn't your average problem I don't believe and it goes a little something like this -

I'm installing ubuntu 9.10 through wubi, and I've downloaded the 32 bit client software 3 times off from the ubuntu website, and twice from a torrent.  Both times it pulls 64 bit software.  I haven't bothered trying to burn the .iso to a DVD and install it that way because I have always done it inside of windows.

Is anyone else having this problem?

Thanks for any help,
- Aaron

---

### Post by BQAggie2006 on 2009-11-06
Do you mean this is occurring when you download the 32-bit ISO and manually point Wubi at it?

---

### Post by aosgd on 2009-11-06
I'll tell you exactly what I do.

Step 1: Download the .iso either from a torrent or the ubuntu website.

Step 2: Use WinRAR to extract the .iso

Step 3: Run the wubi that is inside of the .iso

Step 4: Wonder why it's grabbing 64 bit files instead of 32 bit.

That's what's going on.

---

### Post by BQAggie2006 on 2009-11-06
Don't extract the ISO, leave it intact. Download the Wubi executable from [http://wubi-installer.org/](http://wubi-installer.org/), then when you run the installer, point it towards the ISO file, and it should install the 32-bit OS.

---

### Post by aosgd on 2009-11-06
Alrighty, thanks.

---

### Post by aosgd on 2009-11-06
This did not work.  The installer did not ask me to locate any files at all and it went ahead and started downloading the 64 bit files again.  I'll give you a little more insight..

I run the installer, it asks me for the size I would like to make the partition and my username/password credentials, so I enter them and hit "Install", then it starts downloading the files for it.

Downloading ubuntu-9.10-desktop-amd64.iso.torrent is what it says above the progress bar.

---

