---
title: "problems converting rpm to deb"
date: 2008-11-16
forum: General Help
---

### Post by bilijoe on 2008-11-16
> **Convert .rpm to .deb**             
                                                                1. Alien Installation

Alien is available in the normal Debian repositories, so we can install it like this:

**sudo apt-get install alien**

 
2. Converting .rpm To .deb

Next we download the current <file name>.rpm package:

**cd /tmp**

**wget http://www.website.com/downloads/community/1.1/Linux/<file name>.rpm**

To convert it into a .deb package, we simply run

**sudo alien <file name>.rpm**

Note: use the --scripts parameter to include the scripts.

Afterwards, run

**sudo ls -l**

in the /tmp directory, and you'll see that alien has created the file <file name>.deb. You'll also notice that alien has counted up the version number, it's now 1.1-2 instead of 1.1-1. If you want to keep the original version number, you must use the -k switch:

**sudo alien -k <file name>.rpm**

will create the file <file name>.deb

To install the new .deb file, we use dpkg -i:

**sudo dpkg -i <file name>.deb**

Now <file name> is installed and fully functional (you still might have to edit its configuration file though).

If you want to save the dpkg -i step, you can have alien install the package. The command

**sudo alien -i <file name>.rpm**

will convert the original rpm package and immediately install it.

You see, converting .rpm files to .deb files is very easy. You can have a look at

**man alien**

to learn about what else you can do with alien.
                                                                                                                                    *                                              Last edited by TrakerJon; February 9th, 2008 at 03:41 AM..                                                           *
I am trying to install the LaCie Lightscribe software, but can only find it as an .rpm file.  I found the post quoted above, and followed it, but I get a long string of errors which read "chown: invalid group: `:wheel'".  I'm sure I've done this exact thing before (installed the LaCie .rpm packages), and had it work, though I might have followed advice from a different post. What's with the group 'wheel'? What am I doung wrong in trying to install an .rpm package?

---

