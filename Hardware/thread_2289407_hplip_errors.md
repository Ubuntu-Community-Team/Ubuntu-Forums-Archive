---
title: "hplip errors"
date: 2015-08-03
forum: Hardware
---

### Post by dcroxton on 2015-08-03
I have a wireless HP Envy 120 which works sporadically.  It always prints a test page, but often won't simply print what I want it to.

Yesterday I learned of hplip and hplip-gui and found I was able to print consistently from hp-toolbox even if I couldn't print from within a program.  Great.  But I got greedy and thought, well, if this works, it seems like there ought to be a way to make it work through a cups printer.  Seeing that the Ubuntu version of hplip was not the latest, I tried downloading from HP and installing their hplip.

This failed to build but it did manage to screw up the hplip that I did have.  Now when I run hp-toolbox I get the following:
```
error: Unable to locate models.dat file

```
as well as a number of .png files.

"hp-setup" has never worked.  It complains about the same lack of models.dat, lists the version of HP Linux Imaging and Printing System as 0.0.0 (not necessarily a problem, but it doesn't sound good), and then says no device selected that supports this functionality after looking only at usb connections, whereas I've seen screenshots where it looks for networked printers as well.  I guess without models.dat it really isn't going to find anything.

Another symptom is that /etc/hp is empty, and when installing hplip it complains
```
Can't open /etc/hp/hplip.conf: No such file or directory.
```
Which seems kind of odd, because you would think it would create it.

I have been frantically trying to clean out everything that could possibly be left over from my failed hplip installation.  My package database seems clean and I remove everything hp related before re-installing, but I keep getting this error, so I don't know how it ever worked in the first place.

I would be so grateful if anyone could offer any suggestions.

UPDATE:  I went to the folder where hplip-3.15.7 unpacked itself in its unsuccessful installation and found its models.dat file, then copied it into the same relative directory in /usr/share/hplip and gave it liberal permissions (pretty much the same as all the other files there, 755 owned by root:root).  It is still complaining about not being able to find models.data.

UPDATE 2:  I also copied the hplip.conf file into /etc/hp, and lo, it works!  I'm still having a few issues, but normal ones.  Why oh why did it not install models.dat and hplip.conf when I installed the packages??

---

### Post by tgalati4 on 2015-08-04
It looks like either a packaging error or a post-installation script error.  There are log files in /var/log/dpkg.log and /var/log/dpkg.log.1 .  See if there are any obvious errors.  I'm running 3.14.3, so perhaps something changed with the newer version.  Check the changelog for 3.15.7 and see if there are configuration file location changes.  

Because you downloaded *hplip* directly from HP, you can see the changes needed to get it to work with Ubuntu--these are typical issues when dealing with 3rd-party software.

Is your printer not recognized or not supported in 3.14.3?

---

### Post by dcroxton on 2015-08-05
> **tgalati4 said:**
> It looks like either a packaging error or a post-installation script error.  There are log files in /var/log/dpkg.log and /var/log/dpkg.log.1 .  See if there are any obvious errors.  I'm running 3.14.3, so perhaps something changed with the newer version.  Check the changelog for 3.15.7 and see if there are configuration file location changes.  

Because you downloaded *hplip* directly from HP, you can see the changes needed to get it to work with Ubuntu--these are typical issues when dealing with 3rd-party software.

Is your printer not recognized or not supported in 3.14.3?

I don't see any errors in the logs.  The printer was recognized, but printed sporadically.  I got greedy and wanted it to work all the time.  But it seems to be working now with the slightly older hplip configured properly.

---

