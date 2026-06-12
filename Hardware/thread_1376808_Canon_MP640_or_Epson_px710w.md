---
title: "Canon MP640 or Epson px710w"
date: 2010-01-09
forum: Hardware
---

### Post by ike on 2010-01-09
Hi,

I am going to buy me a printer in a few days. I thought I had settled upon an Epson Stylus px710w, but then I came across the Canon Pixma MP640 which seemed a tiny bit better and also cheaper.

Since these printers are quite similar I decided I will buy the printer that has the best Linux/Ubuntu support.

I have found a few stories about fully functional Canon MP640's under Linux, but not so much about the Epson printer.

They both get the score 2/3 ("Works mostly") on Openprinting.org:
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_PX710W](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_PX710W)
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP640](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP640)

Does anybody have any experience with these printers?

It seems there are official drivers for the Canon printer, and also the commercial [TurboPrint drivers]("http://www.turboprint.info/").
There are also official Linux drivers for the Epson printer, but I am not sure about the quality of any of the drivers.

It would be great if anyone could recommend any of these two printers (or another one perhaps?) from a Linux perspective.

---

### Post by geepeegee on 2010-01-19
As there have not been any replies to this posting yet I wondered if you had bought your printer yet?. I am also considering the Epson PX170W as well and was  wondering how it faired under Ubuntu (if you decided on the Epson that is...)

---

### Post by ike on 2010-01-22
> **geepeegee said:**
> As there have not been any replies to this posting yet I wondered if you had bought your printer yet?. I am also considering the Epson PX170W as well and was  wondering how it faired under Ubuntu (if you decided on the Epson that is...)

I have bought the Epson px710w, but I have not yet had the time to play with it. I have installed the drivers, which was not very complicated (though it involved downloading an old Ubuntu package from a previous release (hardy i think) - I wish I could give you the details but I just don't remember the package name).

The printing works, but i have not tried photo printing or scanning yet.

---

### Post by tcchris on 2010-01-22
Canon , in the past , was very lacking in linux support , I personally moved to brother .
Has that changed? Does canon provide linux drivers ?

---

### Post by geepeegee on 2010-01-27
> **ike said:**
> I have bought the Epson px710w, but I have not yet had the time to play with it. I have installed the drivers, which was not very complicated (though it involved downloading an old Ubuntu package from a previous release (hardy i think) - I wish I could give you the details but I just don't remember the package name).

The printing works, but i have not tried photo printing or scanning yet.

Have you had chance to try out photo printing and  scanning yet?

---

### Post by hhlp on 2010-01-27
definitely hp :

see that :

[https://edge.launchpad.net/hplip]("https://edge.launchpad.net/hplip")

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

just instaling a simple program in synaptic and support for 32 and 64 bits

---

### Post by Lucrus on 2010-02-14
I'm also interested in the PX710W, so I repost the same question: have you had chance to try out photo printing and scanning yet? 

Thanks,
Lucio.

---

### Post by kookenhaken on 2010-02-17
i have a px710w and while it works super in windows i just cant seem to get it installed in ubuntu, i've downloaded the relevent drivers from avasys but when i try and install them using the package installer i get this error 'Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)'

For the record i've downloaded pipslite_1.4.0-5_i386.deb
iscan-network-nt_1.1.0-2_i386.deb
Epson-Stylus_Photo_PX710W-pipslite-en.ppd

any help from those in the know would be greatly appreciated.

---

### Post by toogooda on 2010-03-16
> **kookenhaken said:**
> i have a px710w and while it works super in windows i just cant seem to get it installed in ubuntu, i've downloaded the relevent drivers from avasys but when i try and install them using the package installer i get this error 'Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)'

For the record i've downloaded pipslite_1.4.0-5_i386.deb
iscan-network-nt_1.1.0-2_i386.deb
Epson-Stylus_Photo_PX710W-pipslite-en.ppd

any help from those in the know would be greatly appreciated.

I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php]("http://avasys.jp/eng/linux_driver/faq/id000613.php")

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/en/hardy/i386/libltdl3/download")

64-Bit = [http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download]("http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download")

All working in xsane for me now, hope it helps

AT

---

