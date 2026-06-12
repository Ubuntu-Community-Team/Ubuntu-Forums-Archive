---
title: "Can't get IES4Linux to install"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by jereece on 2009-01-04
I followed the instructions on [this web site]("http://www.psychocats.net/ubuntu/ies4linux") to install wine and then download and install ies4linux.  Everything goes fine except IES4Linux install screen disappears before I get the "install is complete" screen.  I also don't see a launcher icon on my desktop.  I also don't see it anywhere in Applications. So it's like it terminates the install prematurely.  There are no messages.  The screen just disappears about half way through the install process.  

I appreciate any suggestions.

Jim

---

### Post by arvevans on 2009-01-04
Try this:
[INDENT][http://www.psychocats.net/ubuntu/ies4linux]("http://www.psychocats.net/ubuntu/ies4linux")[/INDENT]

When you install Windows executable programs using WINE, you should be able to find a ".wine" directory in your home directory "/home/user_name".  If you cannot see hiden files in your file browser try hitting CTRL-H to turn on "show-hidden".

In the .wine directory you should find a file called "c-drive".  In that directory you should find familiar windows things like "Program Files", and so on.  

When you install .exe files using wine, they usually end up in "/home/user_name/.wine/c-directory/Program Files".  If they do not get automatically entered in the Applications menu on Linux, you can add then by going to System-Preferences-Main Menu and using the menu editor function to add them to your Linux menu.  Remember that you need to prefix the executable line in the menue definition with "wine", (i.e. "wine notepad.exe").

---

### Post by fubbleskag on 2009-01-04
> **jereece said:**
> I followed the instructions on [this web site]("http://www.psychocats.net/ubuntu/ies4linux") to install wine and then download and install ies4linux.  Everything goes fine except IES4Linux install screen disappears before I get the "install is complete" screen.  I also don't see a launcher icon on my desktop.  I also don't see it anywhere in Applications. So it's like it terminates the install prematurely.  There are no messages.  The screen just disappears about half way through the install process.  

I appreciate any suggestions.

Jim
have you tried the --no-gui option? last time i installed ies4 there was a problem with the gui libraries and this fixed it.

> **arvevans said:**
> Try this:
[INDENT][http://www.psychocats.net/ubuntu/ies4linux]("http://www.psychocats.net/ubuntu/ies4linux")[/INDENT]

that was the link he provided in his own post :P

---

### Post by arvevans on 2009-01-04
Yeah, I caught that after I had hit "Submit", but it didn't seem worth the effort for an edit.

Arv
_._

---

### Post by jereece on 2009-01-04
arvevans - I don't have a .Wine directory in "/home/jim".  However Wine is installed  because it's located on my Applications menu.  However, when I click on Applications/Wine/Browse C:\Drive, nothing happens.  Does the folder get created with the first install of a Windows program or should Wine have created this folder when it installed?

fubbleskag - what is the non-GUI option?  Is this some kind of command line installation?  I am still a nubie at Linux, so I will need some help here.

Thanks for the help.
Jim

---

### Post by fubbleskag on 2009-01-05
> **jereece said:**
> fubbleskag - what is the non-GUI option?  Is this some kind of command line installation?  I am still a nubie at Linux, so I will need some help here.

Thanks for the help.
Jim

I'm not sure if this is actually the same issue as I had, but I was unable to install using the gui due to some known bug. the fix was to install from the command line disabling the gui:

```
./ies4linux --no-gui
```

this will install IE6 and flash by default - if you want other versions also installed there are additional command line options you can include - to see them all, try:

```
./ies4linux --full-help
```

hope that helps!

---

### Post by tuxxy on 2009-01-05
Not sure if you really want IE or need it to access a resource maybe but your other option is to install the firefox plugin user agent switcher and change your browsers ID to IE 6

---

### Post by jereece on 2009-01-06
fubbleskag - Thanks for the info.  I will give this a try.  How do I launch a command line.

tuxxy - Thanks for the suggestion.  I need IE to log into my desktop at work.  My company requires IE.  I looked at addons for Firefox like IETab which I use on a Windows machine, however there was no version for Linux.  Can you send me a link to what you are talking about?

The help is much appreciated.

Jim

---

