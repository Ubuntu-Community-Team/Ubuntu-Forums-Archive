---
title: "910x86_64:: Hardware:: Multifunction:: Epson 650FN"
date: 2010-03-01
forum: Hardware
---

### Post by xerman on 2010-03-01
Hello there, all:

Scenario:
Wired and Wireless LAN
Ubuntu 910 64bit on a Sony Vaio Laptop

Just bought a Epson ME Office 650FN, which is supported by linux as stated in many forums. Device is connected to an Ethernet Switch, on a LAN.

Ubuntu recognizes the device on the network with no issues. Adding the printer is straight forward through the printer setup Administration. Xsane recognizes the scanner also.

But can not Print, and can scan.
(The scan was possible using Xsane, or using "Image Scan!" for linux also found in the address stated below).

Searched the web for this device drivers for linux and found this:
[http://avasys.jp/eng/]("http://avasys.jp/eng/")

There have the drivers for the printer, the scanner, both in 64bit .deb packages. But there is another CUPS plugin needed that there is only available for 32bit. There is also source package but does not compile. The "pipslite-wrapper" needed for CUPS to use the PPD provided by AVASYS.

So now I am stucked. The PPD file needs the "pipslite-wrapper" which is not installable. Is there a way to install the 32bit "pipslite-wrapper" on the 64 bit system and make it usable by CUPS?

Should I go back to 32bit?

For all of thouse who wonder if going to 32 bit or going to 64 bit, the best way, for now, is still 32 bit. 64 bit is still not widely supported, not even by main distros, as far as i've experienced in these couple of years i've been using 64 bit only.

Any help and or coments would be really appreciated.

Thanks a lot.
Best regards.

Xermán

---

### Post by xerman on 2010-03-02
Hello there:

Finally i was able to print using the network and the Epson 650FN, following the instructions provided in:

[http://avasys.jp/eng/linux_driver/faq/id000608.php]("http://avasys.jp/eng/linux_driver/faq/id000608.php")

Using the PPD provided by AVASYS also. I had to make a .deb package for 64 bit ubuntu 910, which i did not know how to do before.

Once installed the "pipslite" package for 64 bit i can use the printer and the scanner. Did not try the fax.

I did not mark [SOLVED] this thread as once installed the "pipslite" package i lost all printer configuration options, and now the only options left are:
- page size (A4, A4borderless, 10x15, 10x15 borderless, 13x18, 13x18 borderless)
- quality (plain paper-normal | plain paper-quality | epson paper-normal (for 4 types of epson paper)
- color (color or monochrome)

So this means the issue is partly solved, but not really solved. And still can not send FAX.

After all these tweeks, searching the web,using synaptic to install dependencies, trying to install through CLI, building 64 bit package, I can say without a doubt, that is better to buy an HP device than canon, epson or other.

If I ever happen to find out how to use the printer as it is supposed to I will post, but most likely is that i will stay as is, and later buy a good HP one. 

Best regards.
Xermán

---

