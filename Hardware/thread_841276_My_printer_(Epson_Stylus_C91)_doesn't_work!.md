---
title: "My printer (Epson Stylus C91) doesn't work!"
date: 2008-06-26
forum: Hardware
---

### Post by She's My Man on 2008-06-26
Hi everyone :popcorn:
I have bought a new printer today (an Epson Stylus C91) which doesn't seem to work on Ubuntu 8.04? In the automatic driver search they make when you install a new printer I think it stopped in C89, so I tried to print with that and the printer put out a blank page while test printing! (Yes, there is ink, and the printer works correctly on Windows) so I tried again with "Stylus" (apparently a generic driver) from the list which resulted in the same thing. Then I tried to install the correct printer from [http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do)[Avasys]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do"), but the installation failed and I got this error:
[IMG]http://img255.imageshack.us/img255/3121/screenshotuq6.png[/IMG]

Any advice is appreciated! 
TIA :KS

---

### Post by Claus7 on 2008-06-26
Hello,

maybe someone who has the same printer should help you more, yet some thoughts.

Have you downloaded the right version for your machine?
Maybe the source package to be more ideal, if you see also in the configure file what you have to do, in order to install it specificaly for your machine.
As I have seen you have to download a file. After you unzip, in order to install the driver, it prompts you to do it as root. Have you typed :
sudo ./"name of script file"
in order to install the driver?

These are my thoughts,
Regards!

---

### Post by She's My Man on 2008-06-26
Oh, it results in exactly the same error!

---

### Post by Claus7 on 2008-06-27
Hello,

does this link helps you?
[http://ubuntuforums.org/archive/index.php/t-439589.html](http://ubuntuforums.org/archive/index.php/t-439589.html)
It has to do with the configuration of ekpd.
Before you do anything try also the DX4050 driver from the Applications/settings/printing dialog box. I found it by googling and it worked in someone's case. It might work for you as well. Just test it. 

Regards!

---

### Post by She's My Man on 2008-06-27
Wow. I chose DX4050 and now it works. Thanks guys!

---

