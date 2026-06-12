---
title: "installing netbook remix desktop ?"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by JDPP on 2009-06-26
Hi, 

I have just installed Ubunto Studio 9.04 on my MSI U100 netbook.
I'd like to have the ubuntu studio remix desktop and best fonctionnality added.

I would like to know if I can do it by just adding some packages thru synaptic package manager ?
If so, could you tell me if I need to add some repository, and then wich packages.

I read
[INDENT]go-home-applet: a super-charged 'show-desktop' applet which, in addition to showing the desktop, allows users to drag-and-drop files/folders/[urls]("http://en.wikipedia.org/wiki/Urls") on to it, to create new favorite items in the launcher.
window-picker-applet: a space-conservative window-picker applet, which allows switching and closing windows from the panel.
maximus: a window-management daemon (makes sure windows are maximized etc)
human-netbook-theme: Human with panel themeing
ume-launcher: the desktop-launcher which takes the place of [Nautilus (file manager)]("http://en.wikipedia.org/wiki/Nautilus_%28file_manager%29"). Replicates the functionality of Applications/Places/System, with added support for a user-defined favorites category.
desktop-switcher: Allows easy desktop-mode switching between Netbook mode and Classic mode (Ubuntu 8.04 default set-up)
[/INDENT]here [http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix)
are those all the packages I need ?

Thanks in advance

---

### Post by Brandon Williams on 2009-06-26
For Jaunty, you can simply install ubuntu-netbook-remix, which will pull in the rest of the packages that make up the UNR interface. If you don't want to install all non-UNR apps that this meta-package depends upon, then install the following: go-home-applet, human-netbook-theme, maximus, netbook-launcher, ubuntu-netbook-remix-default-settings, webfav, and window-picker-applet. Everything for UNR is in the standard Jaunty repository. I recommend against using the desktop-switcher (it switches between the UNR and classic desktop interfaces) at this time. A new version should be making it into jaunty-updates from jaunty-proposed in the near future, but until then, avoid it.

---

### Post by JDPP on 2009-06-26
thanks !!!

---

