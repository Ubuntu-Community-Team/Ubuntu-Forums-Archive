---
title: "Samsung clx-3170fn"
date: 2009-03-08
forum: Hardware
---

### Post by nvb21 on 2009-03-08
I fail to make Ubuntu 8.10 prints on Samsung's clx-3170fn. I have done few things but none of them works.

** THING #1
I tried to "Add printer" and Ubuntu suggested "Samsung CLX-3160 Foomatic/foo2qpdl [en]". It failed to print anything except an error page. The error message is:

SPL-C ERROR - Please use the proper driver
   POSITION : 0x0 (0)
   SYSTEM   : src/xl_image
   LINE     : 606
   VERSION  : SPL-C 5.35 11-20-2007

According to [OpenPrinting database]("http://www.openprinting.org/show_printer.cgi?recnum=Samsung-CLX-3175FN"), foo2qpdl should work with clx-3175fn (which is the same as clx-3170fn except it's black in color).

** THING #2
I downloaded Unified Linux Driver from Samsung's clx-3170fn support site, unzip and then sudo install.sh. Program fails and the error message is:

Failed to load widget from </home/nvb/cdroot/Linux/i386/install/../../noarch/install/share/ui/WizardTemplate.ui>
QMutex::unlock: unlock from different thread than locker
                was locked by 0, unlock attempt from -1221195584

Note: WizardTemplate.ui is in that folder but not missing.
 
** THING #3
I thought the WizardTemplate.ui was locked by root (0), I enabled root account and then run install.sh as root. Same error message.

** THING #4
I repeated #2 & #3 with Kubuntu, same error message.

** THING #5
I repeated #2 with Puppylinux 2.1.4 and install the driver without any problem. It works perfectly.


CLX-3170fn User Guide says it works with Ubuntu 6.06, ... Anyone try? Any suggestion on how to make it works with Ubuntu 8.10? Thanks in advance for any suggestion.


Cheers, NVB21

---

### Post by yahs on 2009-03-08
hello

when you say 

[COLOR="Red"]I downloaded Unified Linux Driver from Samsung's clx-3170fn support site, unzip and then sudo install.sh. Program fails and the error message is:[/COLOR]

did you type sudo install.sh or sudo ./install.sh

i have just downloaded and installed a similar samsung printer using the same Unified Linux Driver and it worked straight up on Ubuntu 8.10, including scanning in XSane and Gimp (after a reboot).

When I typed sudo install.sh without the full stop and slash I got errors.

This is what worked for me.

I downloaded the file and extracted to the desktop
I changed directory to cdroot/Linux
I typed sudo ./install.sh
I got the following messages

[COLOR="Red"]libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
[/COLOR]

The GUI installer then  appeared

You are asked tick-box questions including the printer model you want.

I selected scx4100 and that's it - a printer that prints and scans as it should

The following is a list of printers I was able to select from

**** Print drivers for the following device models available:
CLP-300splc CLP-310splc CLP-350ps CLP-500splc CLP-510splc CLP-550ps CLP-600splc CLP-610splc CLP-650ps CLP-660ps CLP-770ps CLX-216xsplc CLX-3160splc CLX-3170splc CLX-6200ps CLX-6240ps CLX-8380ps mfp560 mfp750 ML-1450ps ML-1510spl2 ML-1520spl2 ML-1610spl2 ML-1630spl2 ML-1630wspl2 ML-1640spl2 ML-1710spl2 ML-1740spl2 ML-1750spl2 ML-2010spl2 ML-2150ps ML-2150spl2 ML-2240spl2 ML-2245spl2 ML-2250spl2 ML-2510spl2 ML-2550ps ML-2550Sps ML-2550Sspl2 ML-2560ps ML-2570ps ML-2850ps ML-2855ps ML-3050spl2 ML-3470ps ML-3560spl2 ML-4050DMVps ML-4050ps ML-4550ps ML-6060ps ML-7300ps ML-8x00ps scx4100 scx4200 scx4300 scx4500 scx4500w scx4725 scx4x16 scx4x20 scx4x21 scx4x24 scx4x26 scx4x28ps scx5312f scx5635ps scx5835ps scx5x30 scx6x20PCL scx6x20 scx6x20PS scx6x22ps scx6x45ps scx6x55ps sf531p

Hope this is useful

---

### Post by nvb21 on 2009-03-10
Thanks for sharing. I did the same steps, including sudo ./install.sh  Hmmm ... Could you advise what version of Unified Linux Driver you use, and where you download it?  

I download ver 3.00.37 from Samsung Hong Kong [http://www.samsung.com/hk/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlasermultifunctionprintersfaxes&model_nm=CLX-3170FN&disp_nm=CLX-3170FN&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010100&model_cd=CLX-3170FN/XSS&menu=download](http://www.samsung.com/hk/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlasermultifunctionprintersfaxes&model_nm=CLX-3170FN&disp_nm=CLX-3170FN&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010100&model_cd=CLX-3170FN/XSS&menu=download)

---

### Post by yahs on 2009-03-11
I used the same file as you - Samsung Unified Driver ver 3.00.37. downloaded from Samsung .co.uk. I have since tested this download on fresh installations of Ubuntu 8.04.2, Intrepid 8.10. Linux Mint 6 and Jaunty Beta version. All worked without any problems.

---

### Post by nvb21 on 2009-03-14
The problem is fixed after I change the Default Language to English.  I believe there is a bug in UI of Chinese Language support. Many thanks for your input.

I have another2  minor issues:

1) The Add Printer button doesn't invoke the wizard. It doesn't matter because there is a default printer.
2) I try to uninstall the driver by sudo ./uninstall.sh and get following error message:

[I]Failed to load widget from </home/thomas/Download/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>
QMutex::unlock: unlock from different thread than locker
                was locked by 0, unlock attempt from -1221556032[/I]


Thanks again for your input.

---

### Post by LarsSikstrom on 2010-07-22
I have read the messages above with great interest as I have run into a very similar problem with a recently purchased Samsung CLX-3175fn.

I like the looks of this machine. It runs beautifully under Windows7 and Ubuntu 8.04 using the Unified Linux Driver downloaded from Samsung Support. But Ubuntu 10.04 will not accept this driver, and the comments on the terminal are always the same even with an absolutely absolutely clean pristane  Ubuntu 10.04 system. 

Failed to load widget from </home/lars/Hämtningar/cdroot/Linux/i386/install/../../noarch/install/share/ui/WizardTemplate.ui> 
QMutex::unlock: unlock from different thread than locker 
                was locked by 0, unlock attempt from -1216685344

I have searched in vain for a solution on Internet and must now conclude that there is a bug or at least that  Ubuntu 10.04 lacks something that 8.04 has.

Needless to say I would really prefer to use Ubuntu 10.04 for all my work and use of the Internet.

So I would be very grateful for guidance if anybody has a solution.

Thanks for the opportunity to make this request!

Lars

What follows is written about 24 hours later that is on July 23 2010 10:38 pm central European time.

With no guidance forthcoming I continued on my own with the idea that something was missing in the preparation of my Ubuntu 10.04 configuration which is the 32 bit version. I downloaded the 64 bit version, burnt it to a live CD and installed on an available harddisk. And then imidiately installed the Samsung Unified Pilot following the instructions by sudo cdroot/autorun without any difficulty. The machine now can print with good colors, scan, copy and probably works as it should. 

But I want to be able to use the 32 bit version.

So it seems that the 32 bit version of Ubuntu 10.04 needs some preparation before one can hope to install Samsungs Unified Pilot on it. I will try to draw this to Samsungs attention. For knowledgeable programmers it should be easy to come up with a procedure that we all can follow.

Thanks again for your attention

Lars Sikstrom

---

### Post by andvalb on 2010-09-22
[http://unixforum.org/index.php?showtopic=103932](http://unixforum.org/index.php?showtopic=103932)

---

### Post by JensPersson on 2011-07-24
> **nvb21 said:**
> The problem is fixed after I change the Default Language to English.  I believe there is a bug in UI of Chinese Language support. Many thanks for your input.

I have another2  minor issues:

1) The Add Printer button doesn't invoke the wizard. It doesn't matter because there is a default printer.
2) I try to uninstall the driver by sudo ./uninstall.sh and get following error message:

[I]Failed to load widget from </home/thomas/Download/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>
QMutex::unlock: unlock from different thread than locker
                was locked by 0, unlock attempt from -1221556032[/I]


Thanks again for your input.

Been there and solved it by changing my locale language (and foldernames) from Danish to English. I had downloaded Samsungs Folder (including the uninstall script) to 'Downloads' which in Danish is translated into two words. 

I know this is an old thread but someone might google it tomorrow looking for a solution =)

Take care //JPE

---

