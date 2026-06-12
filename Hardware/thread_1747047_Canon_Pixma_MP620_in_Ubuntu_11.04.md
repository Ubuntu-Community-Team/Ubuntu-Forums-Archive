---
title: "Canon Pixma MP620 in Ubuntu 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by LordNodens on 2011-05-02
Before upgrading to version 11.04 from 10.10, I had successfully setup my printer, Canon MP620, using the instructions in the following link: [http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/](http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/)
After the upgrade the printer no longer works. When I send a test page, the printer accepts the command (the printer's LCD shows printing page) but nothing happens. I tried to install it again using the previous instructions, but the same problem happens. Any ideas?

---

### Post by rghv65c on 2011-05-03
@LordNodens How are you.  Thank you for using the original printer script that wrote.  I am happy it helped.  I have rewritten the script to now support 11.04 check it out here.

64BIt 
[http://bkintegration.com/2011/05/canon-mp620-or-mp630-printer-for-ubuntu-11-04-x64/](http://bkintegration.com/2011/05/canon-mp620-or-mp630-printer-for-ubuntu-11-04-x64/)

32Bit
[http://bkintegration.com/2011/05/canon_mp620-630_printer_for_ubuntu_1104/](http://bkintegration.com/2011/05/canon_mp620-630_printer_for_ubuntu_1104/)

---

### Post by LordNodens on 2011-05-03
Well I tested it but unfortunately it doesn't work. When the Printer Configuration window opens (step 8), I turn on the printer (USB connection, not LAN), select it after being seen at the USB path and the printer is recognized as Generic (recommended). If I install it as Generic nothing works of course. If I choose to select Canon Driver and then select MP630 (ver3) the printer is installed but the print page doesn't work. Am I doing something wrong?

---

### Post by LordNodens on 2011-05-04
OK, so here are the new results:

1. I run dpkg --configure -a
2. Then I followed again your guide
3. Did a restart
4. Tried to print a test page 
5. and voila! everything works perfectly! My printer works again! Thanks a lot! You are a genius! Thanks again for your help!!!

---

### Post by Trig007 on 2011-05-10
> **rghv65c said:**
> @LordNodens How are you. Thank you for using the original printer script that wrote. I am happy it helped. I have rewritten the script to now support 11.04 check it out here.
 
64BIt 
[http://bkintegration.com/2011/05/canon-mp620-or-mp630-printer-for-ubuntu-11-04-x64/](http://bkintegration.com/2011/05/canon-mp620-or-mp630-printer-for-ubuntu-11-04-x64/)
 
32Bit
[http://bkintegration.com/2011/05/canon_mp620-630_printer_for_ubuntu_1104/](http://bkintegration.com/2011/05/canon_mp620-630_printer_for_ubuntu_1104/)
 
Hi guys hoping someone can help, total newbie here
 
experimenting with 11.04 on my netbook using the new install within windows feature, before I take the plunge with a full install. Ive followed the instructions on the link, but when it asks me to enter my password to continue, my keyboard locks up with only the enter key working, so I can't go any further.
 
can anyone help, love the system so far but this is bugging me
 
thanks in advance

---

### Post by Trig007 on 2011-05-10
problem solved

---

### Post by ontwowheels on 2011-05-20
Do you think this will work for a Canon MP560?

I have had this printer installed and working on previous 64 bit versions of Ubuntu, MM, but can not get it to install on 11.04 64 bit.

Execution command = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.20-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 157124 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.20-1 (using .../cnijfilter-common_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

---

### Post by ontwowheels on 2011-05-20
I tried to do the wget...

Connecting to downloads.bkintegration.com|173.236.146.94|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-05-20 16:15:35 ERROR 404: Not Found.

---

### Post by Heeter on 2011-08-06
Thanks for that link,rghv65c

Got my MP620 up and running,,


Thanks again

Heeter

---

### Post by petrus66 on 2011-10-19
BKIntegration has it universal now.

I recommend to input the printer ip when the installation script is asking for it in the terminal.

That way I managed to get wireless scanning working for the first time ever :D

---

### Post by mörgæs on 2011-10-19
Moved to Hardware and Laptops.

---

### Post by cyncicle on 2011-10-21
Installed this yesterday in 11.10.  Worked flawlessly.  Thanks, rhgv65c/BK Integration for making this process so much easier than it used to be![]("http://ubuntuforums.org/member.php?u=1017903")

---

### Post by f00dl3 on 2013-04-11
I'm attempting to install the MP620B in Ubuntu 12.10 x64 and having issues. Followed the link and manually entered the IP during setup, when going to the Printers configuration screen and clicking Add there is no Canon protocol option. When entering "bjnp://(IP address):8611" manually, and directing it to the PPD file in the MP620-630-Linux-Printer/PPD folder, it spits out the following error:  There was an error during the CUPS operation: 'client-error-not-possible'.

---

### Post by pdc on 2013-04-13
here is a 4yr old guide to installing this printer; current Canon printers all have linux support; not all did in 2009;

[http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)

the basis is installing an MP610 driver from Canon and then pointing this to a ppd file that is called MP620; when one looks at a ppd file in a text editor such as gedit, it is very simple to replace MP610 with MP620 

eg this page from Canon Asia

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux)

has the debian packages for the MP610: one installs two packages: COMMON first and then the MP610

things are more complicated using a 64bit system for drivers that were only provided in 32bit format: (as 64bit was uncommon in 2009);

if you have only just installed ubuntu, you might consider adding a 32bit partition of Ubuntu;

(and as the new 13.04 is to be released in a week, you could consider installing a 32bit partition of this new Ubuntu ..)

---

### Post by f00dl3 on 2013-04-18
Seriously - you are advising me to downgrade to 32 bit and live 10 years in the past so it "works"? Seems like Linux is still stuck in the mid 2000s - especially with Wine supporting only DirectX 9!

The instructions didn't work at all - the drivers pointed to in that document were so outdated that Ubuntu made me do a partial distribution upgrade just to get back to "today." I got a feeling that the Canon MP620b is never going to work in Ubuntu 12.10 and I may as well just give up, and print everything in Windows XP.

At least Skyrim works. Using DX9 "emulators."

---

### Post by mörgæs on 2013-04-19
> **f00dl3 said:**
> Seems like Linux is still stuck in the mid 2000s

If there is a driver problem you should direct excess anger towards Canon. They choose which drivers to publish and maintain. 'Linux', whomever you refer to with that title, can not do much.

---

