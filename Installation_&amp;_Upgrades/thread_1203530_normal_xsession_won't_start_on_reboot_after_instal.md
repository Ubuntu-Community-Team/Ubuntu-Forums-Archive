---
title: "normal xsession won't start on reboot after installing updates"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by rpkopreski on 2009-07-03
I have been very pleased with 9.04 overall...

As noted in the title. I received an automatic update and performed the install.  (I have all possible repos. checked-off).  It asked for a restart and then I got an error when logging in.  I can only log-in with GNOME failsafe now.  All of my settings seem to be saved, but I'm concerned for the overall stability.

The error (summarized):

"cannot open shared object file. No such file or directory."
libc.so.6 (makes ref. to /etc/gdm/Xsession)
librt.so.1 (makes ref. to /etc/gdm/Xsession)
libdl.so.2 (makes ref. to /usr/bin/perl)

I checked these files and they are symbolic links to installed libraries.  The libc script seems to run and the link works okay.  Not sure how to fix.

Still looking for some help on this..

---

### Post by rpkopreski on 2009-07-03
I guess I am most concerned with my system's stability.  A few days ago I was following the INSTALL instructions for a 3D Molecular Builder I wanted to test and somehow my GNOME desktop ended up printing only squares in place of text.  

I think I adversely manipulated the libraries.  I had to reinstall from CD and this time I partitioned my drive further so that the root filesystem was separate from /home, /usr and /opt.  

Should I just do another install?  I already lost a day re-installing all my chemical software.  Since I've separated /usr and /opt that shouldn't have to be done again right?

Thanks for any advice.

---

### Post by rpkopreski on 2009-07-04
Still looking for a solution...does anyone have advice?  What bugs me the most is that it is not do to anything I did....with the exception of updating the system....is this common?

Thanks, rpk

---

### Post by Brandon Williams on 2009-07-05
When you say that you have all possible repos repos checked-off, do you mean that you have jaunty-security, jaunty-updates, jaunty-proposed, and jaunty-backports? Or do you only have jaunty-security and jaunty-updates with all four of main, restricted, universe, and multiverse?

If it's the former, with jaunty-proposed and jaunty-backports, then this could be your problem. The packages in jaunty-propsed and jaunty-backports are unstable and should be considered unreliable, since they have not undergone the same degree of testing that packages in jaunty-security and jaunty-updates get. If you have these repos enabled and you apply automatic updates from them, then you should expect to occasionally screw up your system and have to put some effort into debugging and correcting problems like this. I'm not certain that this is the issue, and I don't have any ideas about fixing it (other than reinstallation, which is what I would do).

If you don't have those two enabled, then I don't have anything helpful to suggest. These types of major system stability problems have never happened to me when I am only installing updates from the *-updates and *-security repos.

---

### Post by rpkopreski on 2009-07-06
Thank you Brandon for your reply.  You make a good point.  However, like you I am quite sure I only have the official ubuntu packages selected for updates, although I will double check at school tomorrow.  

I guess I was only referring to the universe, multiverse repos.  I think a reinstall is likely the best bet as well.  I myself broke the OS just a week + ago by messing up some glibs so I really hope this is the last install for a least a month or I may, reluctantly, switch back to xp for my dissertation so I can press on....I got mouths to feed!!

Thanks.

---

