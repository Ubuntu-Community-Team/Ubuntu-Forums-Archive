---
title: "Random screen freeze with 9.10 and older Intel graphics chip"
date: 2010-07-04
forum: Hardware
---

### Post by ubusr on 2010-07-04
I seem to have hit the issue described in bug #502055 running 9.10 on a Dell 2400 with integrated Intel graphics chip 82845G/GL[Brookdale-G].  Intermittently, probably once an hour or two, the screen would freeze, with no pointer or keyboard response.  Usually the problem was precipitated by use of firefox.  ssh to the box did work.  Restarting X or gdm did not work.  I tried several of the workarounds listed in wiki.ubuntu.com/X/Bugs/Lucidi9xxFreezes with no joy.

I'm not sure this has been fixed in 10.4, but the following appears to have worked around the problem, at least I have not experienced it for the past few weeks.  Others with older hardware using integrated Intel graphics chips and experiencing random screen freeze might find it helpful.

I pasted this, and only this, in the /etc/X11/xorg.conf file:

Section "ServerFlags"
                   Option      "AllowEmptyInput" "false"
EndSection

and rebooted.  This was done based on a thread found here:

[http://www.linux-solved.com/post/solved-Xorg-freezes-with-Intel-Corporation-82845G-GL-50231.html](http://www.linux-solved.com/post/solved-Xorg-freezes-with-Intel-Corporation-82845G-GL-50231.html)

---

### Post by jim9 on 2010-07-17
Hi ubusr,

I am currently running ubuntu 9.10 with integrated Intel graphics chip 82845G/GL[Brookdale-G]. 

I have tried to enter /etc/X11/xorg.conf but I could not not find the file. Please see the attached screenshot that explain what I have seen.

Please advice me what to do.

Thanks

---

### Post by ubusr on 2010-08-13
Hi Jim9,

The /etc/X11/xorg.conf file may not be in the default distribution.  You can create it with the contents from the previous post using your favorite text editor.  You need to be superuser to create a file in that subdirectory.

If you don't know about text editors and superuser, the following steps might create it for you.

- open a terminal window:  Applications > Accessories > Terminal
- type these commands in the terminal window:

[SIZE=5][SIZE=4]sudo -i
cd /etc/X11
touch xorg.conf
echo 'Section "ServerFlags" ' >> xorg.conf
echo '    Option "AllowEmptyInput" "false" ' >> xorg.conf
echo 'EndSection' >> xorg.conf
exit[/SIZE]
[/SIZE]
- the "sudo -i"  command will prompt you for the superuser password, 
  typically your own password.  So don't cut/paste all of these 
  commands into the terminal window in one shot.  Do them one line 
  at a time.
- You can verify that the file looks correct with this command:
   [SIZE=4]cat /etc/X11/xorg.conf[/SIZE]

- if all looks good, reboot.

---

