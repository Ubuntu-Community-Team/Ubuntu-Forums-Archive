---
title: "Video resolution decreased"
date: 2008-11-16
forum: General Help
---

### Post by philokokus on 2008-11-16
Hi

I hade everything runing fine in my Ubuntu Laptop. Yesterday I tried to update my video card (Radeon 9000 RV250) but something happend because now de resolution decreased to 800*600. Initialy I had 1020*758 resolution. What can I do now to go back to the original driver?

Any Help?
Tks
José

---

### Post by Hangwire on 2008-11-16
I dont think you need to do that.

Cant you just restore the resolution you had from System -> Preferences -> Screen Resolution?

---

### Post by philokokus on 2008-11-16
> **Hangwire said:**
> I dont think you need to do that.

Cant you just restore the resolution you had from System -> Preferences -> Screen Resolution?

No. 1024*758 doesn´t even appear.

---

### Post by Marcus Derekus on 2008-11-16
Open /etc/X11/xorg.conf as root like so:

```

sudo gedit /etc/X11/xorg.conf

```

Then go to the **Sections "screen"** and add the following code:

```

Section "Screen"
	Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        SubSection "Display"
                **Modes      "1020x758"**
        EndSubSection
EndSection

```

If SubSections does not exist create it and add the code exactly as it is
Dont forget to EndSubSection

If it does exist dont change any thing else. Just add the part in bold.

---

