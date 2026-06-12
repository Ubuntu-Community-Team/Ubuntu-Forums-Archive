---
title: "[SOLVED] Print Functionality for Epson CX8400"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by sfink16 on 2008-01-29
Hi all,

Two days ago I successfully installed Ubuntu 7.10.  The two major problems I have are "no sound" and "printing".

I began by attacking the printing problem by reviewing this  link:

[http://ubuntuforums.org/showthread.php?t=568268](http://ubuntuforums.org/showthread.php?t=568268)

It ended with a "rastertopips failed" error message.  This led me to try CX7800 CUPS driver instead of CX8400.  It seems to have worked for internet printing!

The problem is that I can't seem to print from any other software such as text files or image files using GIMP.

I found this page describing my printer as being supported for GIMP Print:

[http://gutenprint.sourceforge.net/p_Supported_Printers.php3](http://gutenprint.sourceforge.net/p_Supported_Printers.php3)

Using this thread:

[http://ubuntuforums.org/showthread.php?t=557483](http://ubuntuforums.org/showthread.php?t=557483)

and assuming that I'm successful in installing GIMP Print, is there any other software/drivers that I need to install to print from other software such as Open Office or text editors?

Thanks in advance for any help that may be provided!

Steve

---

### Post by sfink16 on 2008-01-30
I finally got everything to work by deleting all printers and starting over using the CUPS [http://local:631](http://local:631) printer setup.  From there I selected "Find new Printers".  In the setup I used CX7800 driver.  As a result, I can print from the internet, GIMP, or any text editor.  Am I losing anything using the older driver, I don't know.

---

### Post by oldsoundguy on 2008-01-30
It may be a little slower, but full functionality is the issue, and you seem to have solved that.  I recently added an Epson R1800 to my networking printer mix .. and have to have it on a Windows machine as the cups drivers are nowhere near ready for that unit.

As to your sound issue .. finding the right package for it will solve that .. usually the Alsa package is the universal one.  That is in your installer package.

The compatibility list is a big help when it comes to hardware.  I spent time researching what worked well and what did not before assembling my Linux boxes.  Thus, had little or NO problems in getting them up and running .. to include wireless!

---

### Post by sfink16 on 2008-01-30
Thanks OSG!  

I'll have to be a little more patient in waiting for the Compatibility list to come up it seems.  I got tired of waiting (not sure why it was taking so long) and went on to something else.  Hopefully when I return to the sound issue I'll be able to take your advise and review the list to figure out the answer.

---

