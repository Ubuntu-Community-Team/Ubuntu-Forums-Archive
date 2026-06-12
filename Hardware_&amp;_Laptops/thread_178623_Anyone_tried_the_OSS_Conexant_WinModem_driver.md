---
title: "Anyone tried the OSS Conexant WinModem driver?"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2006-05-18
Hello,

I'm considering buying a Dell B120 or B130 laptop, which comes with a Conexant HSF softmodem.  As you might know, this is the worst supported modem in the Linux world.  There's nothing really wrong with the Conexant modem, the company just doesn't care about Linux at all.  I absolutely refuse to spend money on LinuxAnt drivers- that's just wrong to be forced to spend money to get a driver for a device you already own.  I'd love to protest Dell and Conexant's lack of interest in Linux by not buying their products, but unfortunately I can't afford to do that.  Dell has **by far** the best deals on high quality new laptops, and I just have to take what I can get.

So my only possible option before going back to Windows for good is in this poorly written paragraph at (k)ubuntu wiki: [https://wiki.kubuntu.org/DialupModemHowto](https://wiki.kubuntu.org/DialupModemHowto)
> 
Update (2005-Sept-22):
      Recently, Rafael Espíndola ported the latest open source version to 2.6.x kernels. AlexandreOttoStrube packaged it to Ubuntu Breezy using kernel 2.6.12-8 The source code, as well as the binary package for breezy, is found at [WWW] [WWW] [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/) A mirror can be found at [FTP] [WWW] [ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/) courtesy AndyRabagliati

Quick Steps for setup of Conexant HSF driver

      Note: this is not the same driver as above. The above one is free, not limited in speed and specific to only one modem model (pci id 14f1:2f00). Assuming you know everything there is to know about your setup, all you need to do is: 

Has anyone tried the free drivers that are found at the above links?  Do they work at all, and if so, how well?  More importantly, will they work with upcoming versions of Ubuntu, or will they be neglected?  I don't have the laptop yet, so I can't test any of these myself.  I'd love to hear anyone's experiences with these drivers.  If they really do work, they should be included by default with the Ubuntu CD, because it is exceedingly difficult to download modem drivers over a modem for which you are trying to download the drivers. 

Thanks for your help!

---

### Post by sb73542 on 2006-05-19
Anyone?

---

### Post by Matchless on 2006-05-22
Hi,
     Yes it works! I am on it now. I am busy drawing up a howto and will post soon. If you are in a hurry let me have a pm and will send to you. By the way speed is normal and not 14400!

---

### Post by sb73542 on 2006-06-16
OK, I now own a B130.  It looks like I'm wrong.  According to Windows, the modem is a Conexant HDA D110 MDC V.92 Modem.  Do you think this will work with the free HSF drivers?  I've read bits and pieces that it might be supported by ALSA, of all things, with the driver snd-hda-intel.  Anyone know?  Thanks!

---

### Post by sb73542 on 2006-06-18
[QUOTE=sb73542]OK, I now own a B130.  It looks like I'm wrong.  According to Windows, the modem is a Conexant HDA D110 MDC V.92 Modem.  Do you think this will work with the free HSF drivers?  I've read bits and pieces that it might be supported by ALSA, of all things, with the driver snd-hda-intel.  Anyone know?  Thanks![/QUOTE]

OK, I managed to get the daemon to start with "slmodemd -a -c b5 hw:0", and it creates /dev/ttySL0 and wvdial picks it up.  I added the "Carrier Check = off" and "Stupid Mode = on" options to my wvdial.conf, but unfortunately it won't dial, it just says "ATMD5551212" and immediately after "No carrier", and it infinitely loops through that sequence until I kill it.  I picked up my phone while it was dialing, and listen for tones, and it's not even trying to dial.  I just heard a solid dialtone.

Any ideas here?  I am really opposed to spending $20 for the LinuxAnt drivers, although they do work.

Thanks!

---

### Post by sb73542 on 2006-06-23
Anyone here have a suggestion?  Thanks!

---

