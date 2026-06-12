---
title: "How to install 9.04 w/o all the extra apps."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by qwavel on 2009-04-25
When I've installed Ubuntu Desktop in the past it has given me lots of extra software that I didn't want, eg. OpenOffice.  There was no option or mode available by which I could request a minimal install.  Has that changed with 9.04?  Let me explain what I mean

I want to install 9.04 both for use as a normal desktop OS and as a virtual OS within VirtualBox.  All I need beyond the basic desktop is firefox with plug-ins, and netbeans or eclipse: I don't want to install any extra applications because I want to keep the whole thing as small as possible.  This isn't about CPU power or RAM, so I am happy to keep using the heavy desktops (Gnome or KDE) - this is about disk space.  Size is particularly important in regard to my virtual disk images - standard Ubuntu desktop results in very big image files. 

From my (minimal) experience with Ubuntu so far, I would say that the netbook remix edition of Ubuntu is too different from the main Ubuntu - it fits my goal of taking less disk space but it is otherwise unsuitable.

I seem to remember that the server version of Ubuntu gives me greater control over the applications that get installed, so this is probably my best bet.  I will proceed with the server version (even though I will not be using this as a server at all) unless someone suggests otherwise.

One other comment.  I'm open to switching from Ubuntu to Kbunutu if it is better in this regard.

Thanks for any guidance.

---

### Post by Therion on 2009-04-25
Minimal Install CD perhaps?  

I'm not sure what will happen if you try to prevent it from going online and downloading additional packages, but the CD itself should be enough of an install to boot you into a stable system.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by cariboo on 2009-04-25
You need to go online in order to do the minimal installation, as the minimal iso image is only 9Mb. A minimal cli install is about 600Mb

---

### Post by snowpine on 2009-04-25
The minimal install CD (mini.iso) is cool if you have internet access. You can also do a minimal CLI install without internet access by using the Alternate Install CD. Press one of the Fn keys (F4? F6? can't remember) at the first screen and you will see the CLI option.

The package "gnome-core" (sounds dirty!) will give you a basic Gnome desktop without the extra apps like Openoffice.

---

### Post by qwavel on 2009-04-26
> **Therion said:**
> Minimal Install CD perhaps?  

I'm not sure what will happen if you try to prevent it from going online and downloading additional packages, but the CD itself should be enough of an install to boot you into a stable system.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

OK, I tried this, but it did not work for me.

I went through the installation process, until I came to the screen with all of the options for what to install.  It appeared to me that, if I didn't check any of the boxes, then I wouldn't get any GUI or desktop at all, so I selected the ubuntu desktop option.

When it finished I discovered that I had all of the utilties, games, and other applications that I would if I had done a normal install.

Was I supposed to not select any of the options and then install the desktop/GUI manually?  Are there instructions somewhere for how to install the desktop/GUI manually?

I was hoping that there would be an easy way do this - I would have thought that a lot of people would want an installation without all the extraneous apps.  I would understand this situation if Canonical was being paid for including these apps, as happens on Windows, but I doubt that is the case.

---

### Post by R.Bucky on 2009-04-26
It is my understanding that Open-Office and other included apps satisfy dependency requirements for other core programs. If you want minimal, a couple of options come to mind. 

I have installed the Server edition and built on from there. Don't install any of the server software, then add-on gnome-core and whatever else you want. 

Not saying this is the best way to accomplish a minimal install, but it is a way.

---

### Post by snowpine on 2009-04-26
> **qwavel said:**
> OK, I tried this, but it did not work for me.

I went through the installation process, until I came to the screen with all of the options for what to install.  It appeared to me that, if I didn't check any of the boxes, then I wouldn't get any GUI or desktop at all, so I selected the ubuntu desktop option.

When it finished I discovered that I had all of the utilties, games, and other applications that I would if I had done a normal install.

Was I supposed to not select any of the options and then install the desktop/GUI manually?  Are there instructions somewhere for how to install the desktop/GUI manually?

I was hoping that there would be an easy way do this - I would have thought that a lot of people would want an installation without all the extraneous apps.  I would understand this situation if Canonical was being paid for including these apps, as happens on Windows, but I doubt that is the case.

You should not select Ubuntu Desktop if you want a minimal install. Ubuntu Desktop is equivalent to installing full Ubuntu through the regular method.

---

### Post by qwavel on 2009-04-26
> **R.Bucky said:**
> It is my understanding that Open-Office and other included apps satisfy dependency requirements for other core programs.

This seems unlikely to me (and undesirable).

I note, however, your mention of 'gnome-core'.  Perhaps that is the key.  I could do a minamal CLI install and then manually  add gnome-core, followed by the few other apps that I want.

I'll give that a try.

---

