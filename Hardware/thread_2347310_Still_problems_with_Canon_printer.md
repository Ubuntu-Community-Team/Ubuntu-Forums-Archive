---
title: "Still problems with Canon printer"
date: 2016-12-23
forum: Hardware
---

### Post by mikebellamy2k on 2016-12-23
Hi all, I am frustratingly looking for an easy solution to my Canon Pixima ip4300 not working with Ubuntu. I have recently updated to 16.10 and there is no support that I can find. Previously I had installed Third party drivers such as found here... 
[https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)
However only drivers from as far back as 14.10 or there about are not compatible with up to date Ubuntus. 
It is increasingly annoying as have to mess around everytime I have a new install and now not working at all. The generic drivers for Ubuntu don't work with the right colour profile so basically useless. I have had to use Windows to print and really don't like having to use. I'm not a coder but don't understand why there isn't support for printers and why windows makes it look a doddle in comparison. Any help here please as its driving me potty!

---

### Post by zacktu on 2016-12-25
I couldn't use the generic Ubuntu drivers when I upgraded to 16.04.  I had some notes that I had made when I installed 14.04, and they were what I needed.

My information came from
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/MX850_series](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/MX850_series)

Yes, it's about MX850, but ith information at the website should be helpful for you.  In any event, downloading and installing cups-bjnp gave me the drivers that I needed for my MX850 printer.

---

### Post by mikebellamy2k on 2016-12-26
OK thanks for that. I've not had much luck with unpacking tar.gz files but will give it a go.

---

### Post by mikebellamy2k on 2016-12-26
I have gotten as far as the command 'make' without any errors. When input of 'sudo make install' gives....


make[1]: Entering directory '/home/mike/Downloads/cups-bjnp-2.0'
make[1]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/lib/cups/backend'
  /usr/bin/install -c bjnp '/usr/lib/cups/backend'
make[1]: Leaving directory '/home/mike/Downloads/cups-bjnp-2.0'

used the directions from...

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/MX850_series](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/MX850_series)


mike@mike-Aspire-M3802:~/Downloads/cups-bjnp-2.0$ sudo su
0ddroot@mike-Aspire-M3802:/home/mike/Downloads/cups-bjnp-2.0# make install
make[1]: Entering directory '/home/mike/Downloads/cups-bjnp-2.0'
make[1]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/lib/cups/backend'
  /usr/bin/install -c bjnp '/usr/lib/cups/backend'
make[1]: Leaving directory '/home/mike/Downloads/cups-bjnp-2.0'
root@mike-Aspire-M3802:/home/mike/Downloads/cups-bjnp-2.0# ./bjnp
network bjnp "Unknown" "Canon network printer"
root@mike-Aspire-M3802:/home/mike/Downloads/cups-bjnp-2.0# 


tried to install from synaptics package manager as well but still no hope.

Gonna reboot to see if any good.BRB

---

### Post by zacktu on 2016-12-27
There's a suggestion about installing libcups2 and libcups2-dev.  Have you done that?

---

### Post by mikebellamy2k on 2016-12-27
I think so but have tried so many things so I forget. How would I do that and then what to do after installed?

---

### Post by zacktu on 2016-12-27
sudo apt-get install libcups
sudo apt-get install libcups2-dev
then follow the instructions for installation again

BTW, the email address of the author is on the last line of the README file.

---

### Post by timak001 on 2016-12-28
Hi mikebellamy2k,

I believe this is what you are looking for : 
TurboPrint 2 for Linux
 [http://www.turboprint.info/whatistp.html](http://www.turboprint.info/whatistp.html)

Your printer is supported ( See Supported Printers )  all at a cost though of 30 EUR ( 30 Day trial to see if it's what you are looking for )

---

### Post by mikebellamy2k on 2016-12-28
Well timak001 that seems to get the printer working fine and will see if it continues to after the trial expires, (as i won't be purchasing). Anyone who interested can get some pointers from this post on the .ppd approach to give printer functionality, (without propitiatory software).

[http://www.linuxquestions.org/questions/debian-26/turboprint-294564/](http://www.linuxquestions.org/questions/debian-26/turboprint-294564/)

So for now I hope I may have found the answer and will see how I get on with this solution as it stands and in future updates to Ubuntu. 
Please post here if anyone else uses this solution as will be interesting to know.

Update...no printing after removing the Turbo print and using the .ppd file....

---

