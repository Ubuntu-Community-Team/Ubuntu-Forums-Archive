---
title: "more recent version of HPLIP required for HP Deskjet F370?"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by zakatlas on 2007-02-07
I recently bought a HP Deskjet F370 (printer/scanner/copier). My PC runs Kubuntu 6.06 with HPLIP package 0.9.7-4 preinstalled. However, according to the Supported Devices page on the HPLIP site, at least version 0.9.9 is required for the F370.
I've managed to add it as a printer using the 0.9.7-4 version with a ppd file I got from the OpenPrinting site.
I haven't been able to get it to work as a scanner though. sane seems unable to find a functioning scanner (sane-find-scanner gives me "found USB scanner (vendor=0x03f0, product=0x5511) at libusb:001:002" but scanimage -L says "No scanners were identified").

So I suspect I'll have to install a more recent version of HPLIP (unless someone has a better idea). I do have some questions/worries about this:
Which packages do I uninstall before I do this? None (just install over it), just hplip or hplip + related packages (hplip-data, hplip-ppds, hpijs, foomatic-db-hpijs, others?)?
Do I need to stop certain services first? Are there other precautions I should take or things that I should watch out for?

Thanks in advance for your help.

---

### Post by zakatlas on 2007-02-08
No one? I really could use some help with this.

---

### Post by gozzerd on 2007-02-09
google hplip and go to the sourceforge hplip site. they have a nifty  installer you can download that works for ubuntu. It will install hplip1.7.1. I didn't check, but your printer is probably supported.  The installer will do all the work for you, uninstalling previous versions, downloading and installing dependencies, etc. You need universe and multiverse enbled in synaptic.  It will install a  gui that makes setting up and running the various functions of your machine easy.  

Be sure to put the installer in the folder where you want the extracted hp folder to remain. It will extract to wherever it is sitting when you run it.  For this one, the './file'  must be preceded by sh so it's 

sh ./hplip1.7.1.run

hope that helps.

---

### Post by Larry B on 2007-02-09
Zak

I'm a newbie but i just went through this with a new HP D4160.

Do like Gozzerd says, and if you get error message at the end - when the installer launches HP-setup you can (kind of?) ignore them, the setup will run in spite of them.

However, i ran into three problems, two of them now resolved.

First Problem: One any second print job, the printer would hang and the lights would flash - called the christmas tree effect - there is a patch for this available here: [http://sourceforge.net/mailarchive/forum.php?thread_id=31571521&forum_id=48102](http://sourceforge.net/mailarchive/forum.php?thread_id=31571521&forum_id=48102)

However, i think the patch file has to be placed in the same folder as hplip-1.7.1 to work and after runing the auto installer that floder is locked and i don't know how to get permissions to add a file to it. So, i downloaded the tar.ball and did a manual install. Then installed the patch to the folder i did the manual install from as it was not locked.

Finally, the instructions for installing that patch are kind of not so good for newbies. The line splitting in the intsruction is unclear. I won't waste forum space on it now since this problem may not effect your printer. But if it does, post back and i'll tel you what worked for me.

Second problem: When running HP Device Manager after the install to change your print quality it asks you for a username and password to establish the new settings.  Entering mine did not work - it just asked for the name/password combo again and again. I haven't yet found a solution to this one.  But at least i can print at the "normal" quality and resolution.


Anyway, none of this may apply to your printer. If not, just ignore this post.  :)

Happy Ubuntuing.  :)

---

