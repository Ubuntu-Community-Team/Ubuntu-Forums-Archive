---
title: "how to install gnome on server from desktop-cd?"
date: 2008-07-12
forum: General Help
---

### Post by morgonhed on 2008-07-12
Hi,

can someone please explain how to add gnome to a 8.04 server-installation?

As I have a bad internet-connection I want to do it from the 8.04 desktop-cd if possible.

This is the first time I use ubuntu (or debian) so I don't know a lot about deb-package-admin...

I have already tried (using the desktop-cd) a "sudo apt-cdrom add" followed by "sudo apt-get install ubuntu-desktop" but it cannot find the package on the desktop-cd (and I cannot find anything gnome-related grep-ing through the Packages-files on the  cd - so I really don't understand how that works...

I also have made some experiments with aptitude but to no avail.

So could someone please explain to me how to do that?

(Installing gnome from the internet via apt-get seems to be easy - is is NOT my question !!! - I want to do it from the desktop-cd   (I have a bad/expensive internet-connection via UMTS).

Many thanks!

---

### Post by bodhi.zazen on 2008-07-12
sudo apt-get install ubuntu-desktop

---

### Post by rsambuca on 2008-07-12
I think you will need the alternate CD for this.

---

### Post by SkonesMickLoud on 2008-07-12
^^ Yes.  The desktop CD for whatever reason, doesn't come with a full GNOME image.  The Alternate CD does.

---

### Post by rsambuca on 2008-07-13
That is because the desktop cd has the unpacked files for use on the live CD. The alternate CD has the prepackaged files and unpacks them to your hard drive during installation.

---

### Post by morgonhed on 2008-07-13
So bottom line is: Not possible with desktop-cd.

Can someone confirm that it will work with the alternate cd?

Would it be possible to install the desktop cd first and than add apache, mysql etc from the server-cd?

---

### Post by aysiu on 2008-07-13
I can confirm the Alternate CD works, but I can't confirm that you can add server packages from the Server CD.

Can I ask, just out of curiosity, why you would want to run a server if you "have a bad internet-connection"?

---

### Post by morgonhed on 2008-07-13
I have now installed the desktop-cd and then added apache, mysql etc from the server-cd. That works without any problem.

@aysiu: I simply want a LAMP-stack on my laptop so I can try things out (I work as a freelance programmer) and at the same time I want a proper desktop - am I really the only one with that need?

---

