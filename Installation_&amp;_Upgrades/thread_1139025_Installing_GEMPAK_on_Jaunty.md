---
title: "Installing GEMPAK on Jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by WeatherMan85 on 2009-04-26
Hoping that I can get some help here, I've used linux environments before in my work as a Meteorologist but this is my first time switching over to it on my own rig. I've got a clean install of 9.04 on a dual boot system (2 hard drives), and am looking to get GEMPAK (a meteorological display package) installed. From my experience putting on another package (GrADS) the easiest way should be to do the binary installation and not have to bother compiling from source.

The instructions (here: [link]("http://www.unidata.ucar.edu/software/gempak/GEMPAK/Install_GEMPAK.html")) seem to be fairly straightforward.  

After downloading the binary file I created the /home/gempak directory and used tar -xvzf to unpack the contents of the binary there... seems to be sucessful.

Next (scrolling down to the bottom and skipping the from source install guide) is to create the symbolic link with the ln -s command... again, done and looks to be there correctly.

Lastly it calls for this step where I believe I'm stuck:
> users can configure their .cshrc/.profile entries to source the /home/gempak/NAWIPS/Gemenviron[.profile] files without being modified when a new distribution is installed.I believe (correct me if wrong) that Ubuntu is bash based, so I'd be editing the .profile file to source the /home/gempak/NAWIPS/Gemenviron.profile file, after which I should be able to run the program. My question is how do I do this, and from which directory (/home/user ?)?

I attempted to do this in my home/user directory by adding the line:
> source /home/gempak/NAWIPS/Gemenviron.profileto the end of the .profile file, but doing this seems to have no effect - entering any of the commands to launch GEMPAK programs (e.g. gdplot3, gdinfo) are not effectual (return command not found) - so something isn't quite right. I hope that was detailed and clear and that somebody out there can help me to fix this.

---

