---
title: "Creating a bootable image"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Goggeli on 2009-11-06
Hello!

I am sick and tired of installing all my applications like compiz, avant, VLC and so on after I do my fresh installs. It made me wonder, is it possible to create a image of my fresh system with all my apps installed, and boot and install from that? It would be to huge help!

Thanks all!

---

### Post by Lars Noodén on 2009-11-06
There are a lot of ways to get a similar effect.  I'm sure to have left some out. 

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

[http://www.howtoforge.com/installing_puppet_on_ubuntu](http://www.howtoforge.com/installing_puppet_on_ubuntu)

[http://rsug.itd.umich.edu/software/radmind/linux.html](http://rsug.itd.umich.edu/software/radmind/linux.html)

You can also make a list of the package names (as shown in apt or dpkg) and keep that in a file, one per line.  Then when you do a new installation, you can run apt and use the list for input.  You can keep a copy on your web site and get it with wget during the CD installation or a usb stick.  For example, two packages only:

[INDENT][FONT="Courier New"]
tidy
curl
[/FONT][/INDENT]

If I put that list of two packages in /home/goggeli/packages.txt then this will install them:

[INDENT][FONT="Courier New"]sudo apt-get install `cat /home/goggeli/packages.txt`[/FONT][/INDENT]

---

### Post by fishyf on 2009-11-06
From a terminal run the following command:

    dpkg --get-selections > apps.txt


This will store a list of every application that is currently installed to a file called apps.txt. If you are wanting to re-install your OS, then save this file to a USB stick.

Once you are ready to install all your applications again:

    dpkg --set-selections < apps.txt
    dselect update
    apt-get dselect-upgrade show

Now after a lot of downloading and installing, you will once have all of your applications installed again. It may be an idea before you re-install your OS to back up the /etc/apt/sources.list file, so that you are able to download the applications that you may have got else where.

---

### Post by Goggeli on 2009-11-06
Thanks you all have been to great help! I fund what I needed at [***this one***]("http://http://ubuntuforums.org/showthread.php?t=688872")

Marking tread as solved:D

---

