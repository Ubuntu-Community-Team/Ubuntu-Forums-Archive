---
title: "Where does Upstart log the boot?"
date: 2008-09-15
forum: General Help
---

### Post by HousieMousie2 on 2008-09-15
I started looking for the bootlog via Google, Kubuntu and Ubuntu forums at about 11:30pm, it is now 4:35am... and I am no closer to finding the answer than I was when I started except that I now know it is supposedly handled by Upstart, instead of sysvinit.


From the Upstart README.Debian:

"[I]Where are the boot messages logged?
-----------------------------------

Messages output by the rc scripts can be found in /var/log/boot, if
you have the upstart-logd package installed.[/I]"

Adept Manager assures me that upstart, upstart-logd and upstart-compat-sysv are all installed, and yet the file 'boot' remains empty (there is not a 'boot.log' in /var/log/.)

Again, from the README.Debian:

"[I]Upstart does nothing, what's wrong?
-----------------------------------

You probably don't have the upstart-compat-sysv or system-services
packages installed, likely because you've accidentally removed
ubuntu-minimal in the past.

Here's a quick guide to rescuing your system:

 1. Edit the kernel command-line, remove "quiet" and "splash",
    add "init=/bin/bash".

    The machine will boot into a root shell.

 2. Run "/etc/init.d/rcS"

    The machine will set up the basic necessities such as hardware
    and networking.

 3. Run "aptitude update"

    The machine will update the package lists against the Ubuntu archive.

 4. Run "aptitude install ubuntu-minimal"

    The machine will now install the missing packages.

 5. Check that there are now files in /etc/event.d

 6. Run "reboot -f"

    The machine will now reboot.

Hopefully your machine should now boot normally.[/I]"

Adept Manager also assures me that 'system-services' and 'ubuntu-minimal' are also installed.  In addition, step 5 seems to imply that prior to doing the listed steps, /etc/event.d would be empty.  My /etc/event.d directory contains 19 files and yet I still do not have data in the /var/log/boot file.

What gives?  I am seeing flashes of red screaming by when I boot up and my system has gotten noticeably slower (I have not made changes/installs/uninstalls lately, just the updates that Hardy cheerfully informs me a ready.)

dmesg and the others of it's ilk do NOT show the boot errors that scroll across the screen.  (Trying to PageUp to see the red text is not an option, it ignores it... uh... brain dead... using ?Ctrl+Alt+F-something?  I can't recall now.)

Any assistance would be greatly appreciated!

---

### Post by editrix on 2008-09-15
Since I'd like a boot log myself, I searched for it on Uboontu [http://www.uboontu.com](http://www.uboontu.com) (last link in my sig). I found several answers, none of which I've tried yet.

Uboontu is wonderful--most efficient search engine I've found for this sort of thing.

---

### Post by HousieMousie2 on 2008-09-15
> **editrix said:**
> Since I'd like a boot log myself, I searched for it on Uboontu [http://www.uboontu.com](http://www.uboontu.com) (last link in my sig). I found several answers, none of which I've tried yet.

Uboontu is wonderful--most efficient search engine I've found for this sort of thing.

Thanks for the resource!  Any new tool is very welcomed!  I will check it out ASAP.

---

