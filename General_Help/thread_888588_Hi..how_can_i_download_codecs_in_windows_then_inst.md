---
title: "Hi..how can i download codecs in windows then install them in ubuntu"
date: 2008-08-13
forum: General Help
---

### Post by taaheel on 2008-08-13
i don't have internet connection in ubuntu but ihave one in other computer works on windows ;so how can i download any application (gstream codec)for example in windows then copy it to ubuntu then install it .](*,)]:confused:

---

### Post by overdrank on 2008-08-13
> **taaheel said:**
> i don't have internet connection in ubuntu but ihave one in other computer works on windows ;so how can i download any application (gstream codec)for example in windows then copy it to ubuntu then install it .](*,)]:confused:

Hi and welcome, you may look here
[http://aptoncd.sourceforge.net/doc.html](http://aptoncd.sourceforge.net/doc.html)

---

### Post by Mgiacchetti on 2008-08-13
I suppose you could pop in the live cd for ubuntu, then from there, go to synaptic, select what you want on the other pc, then when you click apply, choose "download packages only"

then you can use any type of media to transfer them (cd, flash drive, etc.)

---

### Post by taaheel on 2008-08-13
thanks for the links

---

### Post by taaheel on 2008-08-13
> **Mgiacchetti said:**
> I suppose you could pop in the live cd for ubuntu, then from there, go to synaptic, select what you want on the other pc, then when you click apply, choose "download packages only"

then you can use any type of media to transfer them (cd, flash drive, etc.)

thank you alot i will try that .:)

---

### Post by colobix on 2008-08-13
A pc without internet sounds borring.
I really suggest you to check if there are any wireless networks in your local area, but that's your business.
Btw, that idea with a live CD i great. I suggest you to download the newest DVD live CD because it already includes most of the codecs.
Then run it on your windows pc with internet access and download the rest of the codecs, move them to a floppy disk or a memory stick or whatever, and then put them on your linux pc.

---

### Post by ajgreeny on 2008-08-13
If you only have one CD/DVD drive you will have to transfer the files by flash or usb drive as you can not eject the live CD and still run the system, but otherwise this is a good idea.

You could even install aptoncd in the live system, then add the codecs etc, and then run aptoncd to make an iso file of the downloaded packages, which you transfer to usb drive.  Keep the aptoncd package separate, so you can run that first on your ubuntu install to add aptoncd to that. Now you can use the iso file on the usb drive as a source for the packages for your instaled ubuntu.

---

### Post by fsmithred on 2008-08-13
Download the packages you need, transfer them to ubuntu with a usb stick, and install them with dpkg. If you're not using hardy, select the version you are using.
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

---

### Post by taaheel on 2008-08-25
> **ajgreeny said:**
> If you only have one CD/DVD drive you will have to transfer the files by flash or usb drive as you can not eject the live CD and still run the system, but otherwise this is a good idea.

You could even install aptoncd in the live system, then add the codecs etc, and then run aptoncd to make an iso file of the downloaded packages, which you transfer to usb drive.  Keep the aptoncd package separate, so you can run that first on your ubuntu install to add aptoncd to that. Now you can use the iso file on the usb drive as a source for the packages for your instaled ubuntu.

Thank you and everybody with your help i managed to install my codecs and all i needed.

---

