---
title: "Modem Driver for Winmodem (Agere Systems)"
date: 2008-09-12
forum: Hardware
---

### Post by therian on 2008-09-12
I am looking for two things:

1.  Ubuntu/Linux modem driver for a Winmodem:  Agere Systems PCI Soft Modem.  (May also be Lucent/Trendnet).

2.  If there exists such a beastie, how would I install it?

Modem$ cat scanout.02:09.0
CLASS=0780
NAME="Communication controller: Agere Systems Unknown device 0620"
PCIDEV=11c1:0620
SUBSYS=11c1:0620
IRQ=10
HDA=
CodecDiagnosed=
slamrTest=
CodecClass=
IDENT=SV2P
SLMODEMD_DEVICE=
OPTS=
Driver=agrmodem+agrserial
DRIVER=agrmodem+agrserial



Thanks,

Wayno

---

### Post by cariboo on 2008-09-12
> Driver=agrmodem+agrserial
DRIVER=agrmodem+agrserial


From your post it tells you what drivers it is using. Have you tried wvdial?

Jim

---

### Post by therian on 2008-09-15
so the drivers are installed?  Hmmm.  No I am new to Ubuntu.  I have about 2+ years of SuSE experience though.  I will check and report back -- thanks.

Wayno

---

### Post by therian on 2008-09-15
when I tried wvdial I got

/dev/modem : no such file or directory

I also tried wvdial /etc/wvdial.conf

made no difference -- now what?

Wayno

---

### Post by therian on 2008-09-16
Reality check --

I did an lsmod | grep agr

and nothing showed up -- I guess that's the drivers scanmodem recommends - NOT what is installed -- where do I find the drivers agrmodem and agrserial, and how do I install them?  I've never done that before.

Wayno

---

### Post by therian on 2008-09-25
Hmm --

I still have no idea where to find or how to install the agr drivers for Ubuntu.

Would someone be so kind to let me know?

Thanks,

Wayno

---

### Post by thomas228 on 2008-10-04
> **therian said:**
> I am looking for two things:

1.  Ubuntu/Linux modem driver for a Winmodem:  Agere Systems PCI Soft Modem.  (May also be Lucent/Trendnet).

2.  If there exists such a beastie, how would I install it?

Modem$ cat scanout.02:09.0
CLASS=0780
NAME="Communication controller: Agere Systems Unknown device 0620"
PCIDEV=11c1:0620
SUBSYS=11c1:0620
IRQ=10
HDA=
CodecDiagnosed=
slamrTest=
CodecClass=
IDENT=SV2P
SLMODEMD_DEVICE=
OPTS=
Driver=agrmodem+agrserial
DRIVER=agrmodem+agrserial



Thanks,

Wayno


I too am a newbie to ubuntu and linux but here's what I did.
Download scanModem.gz from [http://132.68.73.235/linmodems/index.html#scanmodem](http://132.68.73.235/linmodems/index.html#scanmodem)
In terminal sudo gunzip scanmodem.gz (I think)
cd into scanmodem folder
sudo ./scanmodem
you will have a new folder "modem"
You should find ModemData.txt in that folder as well as a number of other files in the doc folder. Hopefully there will be enough info to find your drivers If not send the modemData file as instructed in the file. I had to go to the ubuntu depositories to find the deb file for my drivers.
It took me 2 months to get a landline modem working but sucess today.
Hope this is enough to get you going.
Tom

See the following post for where I found the deb I needed. I googled to find it in the first place

Tom

---

### Post by thomas228 on 2008-10-04
> **therian said:**
> Hmm --

I still have no idea where to find or how to install the agr drivers for Ubuntu.

Would someone be so kind to let me know?

Thanks,

Wayno

You can find a deb at [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)

look for agrsm-ubuntu8.04.1-2.6.24-19-generic.tar.gz

Make sure its the right one by running scanmodem first 

(see post above)

These programs reguire a lot of reading but end up being worth it

Good luck.

Tom

---

### Post by cariboo on 2008-10-04
Have you looked here?

[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)

Download agere_modem.tar.gz and see if it works for you. Make sure you read the readme file first.

Jim

---

### Post by spiritfox on 2008-11-15
I have the same modem chipset, but I'm running intrepid with kernel 2.6.27, so the ubuntu-specific one doesn't work for me, and the instructions on the page specify a file at /usr/src/linux/.../hda_codec.c that isn't there.  Where do I find it or how else can I install this driver?

---

### Post by Psychoscorpic on 2008-11-17
Sitting in the same boat here. Upgraded to 8.10 and now no modem.
The whole compile thing is trapped behind a mental block for me. (Probably quite easy once I learn how)

If anyone (surely there aren't just 5 of us using this!) has already compiled the driver for 8.10, please post it back to the [http://linmodems.technion.ac.il/pack...odem/11c11040/](http://linmodems.technion.ac.il/pack...odem/11c11040/) site for the rest of us!
I would if I could.

---

### Post by krtica on 2008-11-18
I have the same problem. :(
I tried to compile drivers following ["HOWTO"]("http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html") instructions, but I'm unable to do it.
Errors, errors, and more errors. :(
Is there anyone experienced enough to tell us what to do? :confused:

---

### Post by spiritfox on 2008-11-21
I tried following the readme and using `make module` to build the driver for the 8.10 kernel before using `make install,` but make module threw an error about a function "kill_proc()" being implicitly declared.  I think this means there's a problem with the driver itself, but I'm not sure.
@psychoscorpic:When you compile something from source, you're converting it from the code it was written in into the binary that the computer understands.  normally (for applications and stuff), you use ./configure first after unzipping the source file, which makes sure your computer can run the software and generates the makefile, which is used by the make command when it compiles all the text into binary.  make install sets up the application on your system.  To compile things from source in ubuntu you have to install the "build-essential" package from the internet or from your live CD.

---

### Post by krtica on 2008-11-26
Posted by mistake. :(

Another modem problem on: [http://ubuntuforums.org/showthread.php?p=6282769#post6282769](http://ubuntuforums.org/showthread.php?p=6282769#post6282769)

---

