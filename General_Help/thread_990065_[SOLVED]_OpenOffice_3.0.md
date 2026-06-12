---
title: "[SOLVED] OpenOffice 3.0 ?"
date: 2008-11-22
forum: General Help
---

### Post by johann_p on 2008-11-22
What is the easiest way to get OpenOffice 3 for Ubuntu/Kubuntu 8.10 without messing up things? I have not seen that version in the synaptic repositories.

---

### Post by ugm6hr on 2008-11-22
This is useful: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

If you want to install from Synaptic, an Ubuntu Intrepid PPA repo has been created (see comment by "jack" on November 17th, 2008 at 6:21 pm at bottom).

Obviously, installing from any unofficial repo is at your own risk.

---

### Post by 73ckn797 on 2008-11-22
Try this, it worked for me with Ubuntu 8.10.
> 
Follow this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever.

Extracted files using File Roller (default Gnome compression utility) to the created directory. 

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered ```
sudo dpkg -i *.deb
``` The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command ```
sudo dpkg -i *.deb
```. This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.from this thread:
[http://ubuntuforums.org/showthread.php?p=6090196#post6090196](http://ubuntuforums.org/showthread.php?p=6090196#post6090196)

---

### Post by SteveMcQwark on 2008-11-22
Anyone have any idea when this is going into the default repository?

---

### Post by astoltz on 2008-11-22
It won't be in Intrepid.  For the "official" OpenOffice 3.0 you'll have to wait for Jaunty (9.04).

---

### Post by exploder on 2008-11-22
I used the same guide that ugm6hr posted. This worked perfectly and I have removed the old version. The advantage of using the official Sun packages is that OpenOffice will auto update.

---

### Post by johann_p on 2008-11-22
> **ugm6hr said:**
> 
If you want to install from Synaptic, an Ubuntu Intrepid PPA repo has been created

I tried this and it seems that worked just fine - thank you!

---

### Post by Sef on 2008-11-22
> It won't be in Intrepid.  For the "official" OpenOffice 3.0 you'll have to wait for Jaunty (9.04).


You would have to enable the backports in software sources. (under System > Administration)

---

