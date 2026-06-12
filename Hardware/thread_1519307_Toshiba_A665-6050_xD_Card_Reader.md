---
title: "Toshiba A665-6050 xD Card Reader"
date: 2010-06-28
forum: Hardware
---

### Post by bluefoxox on 2010-06-28
Recently purchased a Toshiba A665-6050 and installed 10.04.  The card reader is not reading my xD cards.  In the past when using Ubuntu once xD cards were inserted/removed they were auto mounted/unmounted.

Any help in this matter would be greatly appreciated.

---

### Post by S.R on 2010-06-28
Have you tried to mount them yourself?

If so or not and it doesn't work can you paste the dump from the command lspci

---

### Post by bluefoxox on 2010-06-28
> **S.R said:**
> Have you tried to mount them yourself?

If so or not and it doesn't work can you paste the dump from the command lspci

Here is the output...

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

I see the JMicron xD host controller listed.  I wonder why it is not auto mounted as in the past?

---

### Post by S.R on 2010-06-29
I did some poking around and it seems like this is a on going deal. I guess you tried another card to make sure it was not the source of your problems. 

I saw one post where the person changed the name of the card to sd. A lot of people are fiddling with the fstab ... which I am really green when it comes to working with that.

You could give this thread a shot and see if it helps out. [http://ubuntuforums.org/showthread.php?t=262696](http://ubuntuforums.org/showthread.php?t=262696)

Maybe a fstab guru could help out.

---

### Post by bluefoxox on 2010-06-30
Thanks for the feedback, but after reading it does not seem like anyone really has a straight forward answer yet.  Eventually after an update I will try and it will work, if not there is always Windows.  I never will stray completely away from it for stuff like this.  Thanks again my friend, I will see you around.

---

### Post by Welly Wu on 2010-06-30
Bluefoxox:

I am interested in purchasing the Toshiba A665-S6065 notebook PC and installing Ubuntu 10.04 x64 bit on it. Other than the xD card reader problem, did you run into other technical problems during the installation process? Did you notice any other technical problems while running Ubuntu on your Toshiba A665-S6050 notebook PC?

I would greatly appreciate a reply at your earliest convenience as this is the only thread that I found a fellow Toshiba owner who has a very similar model number.

Thank you.

---

### Post by bluefoxox on 2010-06-30
Welly,

  I used Wubi to do the installation and everything went very smoothly.   Other than the xD card issue I have not noticed any problems, I like the notebook very much.  Where are you getting yours from Best Buy?  I found the best price there.

Patrick

---

### Post by Welly Wu on 2010-06-30
Bluefoxox:

I am going to buy my Toshiba A665-S6065 from Costco because my father is a member. Here is the link:

[http://www.costco.com/Browse/Product.aspx?Prodid=11538911&whse=BC&Ne=5000001+4000000&eCat=BC|84|56670&N=4017745%204294966821&Mo=5&No=1&Nr=P_CatalogName:BC&Ns=P_Price|1||P_SignDesc1&lang=en-US&Sp=C&topnav=](http://www.costco.com/Browse/Product.aspx?Prodid=11538911&whse=BC&Ne=5000001+4000000&eCat=BC|84|56670&N=4017745%204294966821&Mo=5&No=1&Nr=P_CatalogName:BC&Ns=P_Price|1||P_SignDesc1&lang=en-US&Sp=C&topnav=)

They are selling it for $949.99 USD excluding New Jersey tax. Other retailers are selling the exact same model for $999.99 USD plus shipping, handling, and taxes (if applicable).

Costco has a 90 day no questions asked full refund policy with a receipt. They also offer an extended two year warranty on the purchase of computers which includes the first year of accidental damage coverage and the full two years of technical support which is based in the United States plus concierge service for setting up the computer.

I have a long history with Toshiba products and I currently own a Toshiba NB205-N310/BN net book PC with Microsoft Windows XP Home SP-3 and Ubuntu 10.04 x32 bit installed. Toshiba computers have never failed me and they have a 16% malfunction rate within the first 3 years of ownership just like ASUSTek computers. Toshiba has excellent technical support and they have a long history of official support for various GNU/Linux distributions including Ubuntu and Red Hat for their various products.

Thank you for your quick reply. I am looking forward to getting my Toshiba A665-S6065 in early September 2010.

---

### Post by S.R on 2010-07-03
I wonder if WUBI is messing it up. I am using a Toshiba A305 and booting Ubuntu from an external HDD with no problems using the card reader. Food for thought....

---

### Post by Welly Wu on 2010-07-03
I am not going to install Ubuntu using WUBI. I plan on downloading and burning a copy of Ubuntu 10.04 x64 bit edition and installing it on my future Toshiba A665-S6065 notebook PC.

---

### Post by bluefoxox on 2010-07-03
I like Wubi.  If something gets jacked up it is very simple to start over :^)

I just installed the 2.6.34 kernel, works nice.  Before it the screen brightness adjustment did not work.  Works fine now.  Are  you going to keep your system a dual boot?

---

### Post by S.R on 2010-07-04
Yeah ... if my external is plugged in it goes to the GRUB menu to select OS otherwise it boots right Windows.

---

### Post by bluefoxox on 2010-07-04
I never thought of using an external to install Ubuntu.  Great idea!

---

### Post by bluefoxox on 2010-09-05
I am back at trying to get this xD card reader to work.  At the moment I do not know if it is recognized, and I am looking up how to mount it ect.  Is there is anyone who can lend a hand it will be greatly appreciated.  Thanks!

---

### Post by bluefoxox on 2010-09-05
> **S.R said:**
> Have you tried to mount them yourself?

If so or not and it doesn't work can you paste the dump from the command lspci

Would you be able to walk me through mounting an xD card?  I can not seem to be able to figure it out.

---

### Post by bluefoxox on 2010-09-05
I found a bug written in Spanish (I used Google's built in translator to read it).

[https://answers.launchpad.net/ubuntu/+question/111393](https://answers.launchpad.net/ubuntu/+question/111393)

There is a file recommended to make the xD card reader work.  Being the eternal nOoB I do not want to proceed without some guidance.  So, if someone has the time, please lend a hand :^)

---

### Post by bluefoxox on 2010-09-06
As I talk to myself on the forum...
Progress!  Contacted JMicron and was sent a file (it is attached).  I can now mount and access files on an xD card via my notebook!

Here are the steps to getting your xD reader to work.  Go to the Ubuntu Software Center and search using the word mount.  Install MountManager.  Insert your xD card and go to System/Administration/MountManger

Do you see your xD card?  If yes you do not need to perform the next step.  If no, continue.

Download the file attached jmb38x.tar.gz

Open the directory and unpack the file (I used Nautilus and dragged the folder jmb38x to the folder Downloads).  If you are a command line junkie, do it your way.
Open up a terminal:  Applications/Accessories/Terminal
Go to the jmb38x directory: type cd /Downloads/jmb38x
Next Prep for install: type sudo make (enter your password when prompted)
Then Install: sudo make install
Reboot 

Insert your xD card (if you did not leave it in)  and go to System/Administration/MountManger

You should now see your xD card.  You can simply go to Places upper left hand corner and you should be able to click on your xD cards mount point, FSpot may even ask you if you would like to import pictures if you have them on the card at this point (which is good).  I have not figured out how to get the xD card to automount and show up on the desktop (as it has on older notebooks I have owned), yet.  I am closing this post as solved, but feel free to contact me if you have any questions [email]bluefoxox@gmail.com[/email] 

Regards

---

### Post by gelonis on 2010-10-28
Ubuntu 10.10 Lenovo ThinkPad-SL510


> oleg@oleg-ThinkPad-SL510:/media/Data/lenovo/cardreader/jmb38x$ sudo make
[sudo] password for oleg: 
echo /media/Data/lenovo/cardreader/jmb38x
/media/Data/lenovo/cardreader/jmb38x
make -C /lib/modules/2.6.35-22-generic/build M=/media/Data/lenovo/cardreader/jmb38x
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /media/Data/lenovo/cardreader/jmb38x/built-in.o
  CC [M]  /media/Data/lenovo/cardreader/jmb38x/memstick.o
/media/Data/lenovo/cardreader/jmb38x/memstick.c:23: fatal error: linux/ver.h: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
compilation terminated.
make[2]: *** [/media/Data/lenovo/cardreader/jmb38x/memstick.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: *** [_module_/media/Data/lenovo/cardreader/jmb38x] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2


---

### Post by bluefoxox on 2010-10-28
Disregard the files in my earlier post, this is more up to date.  Try this one, and follow the same directions.

---

### Post by gelonis on 2010-10-29
Again the error no file linux/ver.h

> oleg@oleg-ThinkPad-SL510:/media/Data/lenovo/cardreader/jmb38x$ sudo make
[sudo] password for oleg: 
echo /media/Data/lenovo/cardreader/jmb38x
/media/Data/lenovo/cardreader/jmb38x
make -C /lib/modules/2.6.35-22-generic/build M=/media/Data/lenovo/cardreader/jmb38x
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /media/Data/lenovo/cardreader/jmb38x/built-in.o
  CC [M]  /media/Data/lenovo/cardreader/jmb38x/memstick.o
/media/Data/lenovo/cardreader/jmb38x/memstick.c:23: fatal error: linux/ver.h: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
compilation terminated.
make[2]: *** [/media/Data/lenovo/cardreader/jmb38x/memstick.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: *** [_module_/media/Data/lenovo/cardreader/jmb38x] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
oleg@oleg-ThinkPad-SL510:/media/Data/lenovo/cardreader/jmb38x$ 

---

### Post by ernestmogg on 2010-11-02
I had the same problem with linux/ver.h

Did you see this post:
[http://art.ubuntuforums.org/showthread.php?t=1344297](http://art.ubuntuforums.org/showthread.php?t=1344297)

Basically go into BIOS /System Configuration and disable the Card Reader Power Saving. Worked for me on HP Pavilion 3101sa. Perhaps the Tosh has the same option.

---

### Post by gelonis on 2010-11-03
[COLOR=#000000]Unfortunately, I have no such menu in BIOS :(
[/COLOR]

---

### Post by bluefoxox on 2010-11-03
Have you tried contacting JMicron directly with your notebook model number and the exact model number of your card reader?  [http://www.jmicron.com/Contact.htm](http://www.jmicron.com/Contact.htm)  You can also send an email to me and I will forward the file that was sent to me from them if you like to: [email]bluefoxox@gmail.com[/email] (in case I have made a mistake in conveying it here somehow).  You are also going to want to remove what you already installed by doing something similar to sudo make uninstall "location of file directory here" before attempting a new install.  Fun yeah I know.

---

### Post by gelonis on 2010-11-04
> **bluefoxox said:**
> Have you tried contacting JMicron directly with your notebook model number and the exact model number of your card reader?  [http://www.jmicron.com/Contact.htm](http://www.jmicron.com/Contact.htm)  You can also send an email to me and I will forward the file that was sent to me from them if you like to: [EMAIL="bluefoxox@gmail.com"]bluefoxox@gmail.com[/EMAIL] (in case I have made a mistake in conveying it here somehow).  You are also going to want to remove what you already installed by doing something similar to sudo make uninstall "location of file directory here" before attempting a new install.  Fun yeah I know.

I send yuo letter.

---

### Post by bluefoxox on 2010-11-04
> **gelonis said:**
> I send yuo letter.

Please try again.  I did not show up.

---

### Post by Ramon444 on 2011-04-03
The latest driver for 2.6.22~2.6.37 kernel you can find [here]("http://ubuntuforums.org/showthread.php?t=1718934").

---

### Post by TruSurroundSoundXT on 2012-07-23
This did not work for me either.

Is there really no way to get this to work?

It works fine on Windows!

Poor show Ubuntu community:(

---

