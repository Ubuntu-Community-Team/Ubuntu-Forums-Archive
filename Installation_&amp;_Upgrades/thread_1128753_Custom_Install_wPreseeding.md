---
title: "Custom Install w/Preseeding"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by jiggythegeek on 2009-04-17
First off I apologize if this is already posted somewhere but I could not find an answer in my searches.

I am trying to build a customized installation disc which is mostly silent and only asks questions such as setting timezone and creating a user account. I would also like this installation to have a customized desktop with icons for firefox and thunderbird on the taskbar as well as on the desktop, for instance. I have spent several hours trying to do this one using multiple methods and I have had the following successes/failures.

With the alternate CD I am able to insert a preseed.cfg file into the initrd.gz file to get the installation to occur the way I would like without asking so many questions. With this method I can't see any way of customizing the desktop...I can install files but I can't change the default layout of the desktop. This would be my preferred method if someone could tell me how to customize the installed desktop with this method.

With the LiveCD I have been able to customize the desktop booting a livecd in VirtualBox, customizing the desktop, and copying the home folder to insert into /etc/skel of the live cd. Then after creating the new livecd the customized desktop is there which is great but when I have placed the preseed.cfg file in the root directory of the initrd.gz file it is not read by the livecd installer both after booting to the livecd and starting the installer or starting the installer from the bootsplash menu. I would accept the livecd installation as an alternative method to accomplish what I'm looking for if I could use preseed but it does not seem to want to work for me in the livecd installer.

I have also tried the Ubuntu Customization Kit (UCK) but it doesn't seem like it's purpose is to help with preseeding the installer.

Any help with this would be greatly appreciated and I hope I was clear enough on what I was looking for. Thanks!

Jiggy

---

### Post by relay23 on 2009-09-04
Hi, I think this would be done by changing what you'd want in /etc/skel so that the new users' config files are created with such settings.. if you copy your key config files like .gconf and .mozilla and whatever else you're interested in setting by default in your initrd folders and zipping them back up. I'll be interested to hear if this is the way to go..

---

