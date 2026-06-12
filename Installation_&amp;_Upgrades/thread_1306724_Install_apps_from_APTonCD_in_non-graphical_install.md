---
title: "Install apps from APTonCD in non-graphical install"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by bubbles99 on 2009-10-30
I want to install ubuntu without a GUI (command-line install) as my computer is low spec. At the command line after installation, i want to add a gui as welln as some other packages. The computer will not have internet access, so I looked into APTonCD. How do i restore packages from here withought a GUI? Even with internet access, I wouldn't be able to install from there with my knowledge. the best i could do would be using a command like this:

sudo aptitude install gdm xorg xterm icewm menu mozilla-firefox abiword synaptic


any help much appreciated

---

### Post by mac9416 on 2009-10-30
You can download the software with [Keryx]("http://keryxproject.org"), then use 'sudo dpkg -i /path/to/debs/file.deb' to install each package. Or you could use AptOnCD to create a Cdrom repo from the debs downloaded with Keryx, then run 'sudo apt-cdrom add' on your non-GUI computer. Then you can 'sudo apt-get install' to your heart's content! (as long as the software is on the CD)

Good luck!

---

### Post by bubbles99 on 2009-10-31
thx

---

### Post by bubbles99 on 2009-10-31
is there a way to download ALL the software on the keryx/aptoncd CD in one command?

---

### Post by mac9416 on 2009-10-31
Yes. AptOnCD is very clever. It makes a meta-package (a package depending on all software on the CD) so you can install everything in one stroke. You'd insert the CD, do 'sudo apt-cdrom add', then 'sudo apt-get install aptoncd-metapackage'.

---

