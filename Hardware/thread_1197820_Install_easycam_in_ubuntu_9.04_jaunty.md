---
title: "Install easycam in ubuntu 9.04 jaunty"
date: 2009-06-26
forum: Hardware
---

### Post by pateu on 2009-06-26
First of all i'm sorry if i chose the wrong category to post this thread...
I don't know if this has been posted before, but i managed to install my webcam in jaunty using easycam.
Since the easycam creator's blog moved, the address where you can get the .deb is [http://blog.jbtheou.fr/?attachment_id=334]("http://blog.jbtheou.fr/?attachment_id=334") - click on the link below the date (juin 25th 2009)
This is just a beta version, so it might not work for everyone. The program installed without complaining about the python dependencies. While installing the driver for the webcam, a lot of errors appeared in the terminal which opened when running easycam. Also, when i pressed the Test button, the program crashed. But, the webcam works in skype, which is good enough for me :D
So good luck everyone, hope this helps
Cheers

PS: if it matters, my webcam is A4Tech PK-835, but easycam identified it as ViMicro something...

---

### Post by matrixblue on 2009-07-05
Is there by chance an english version of the software? This is in french.

---

### Post by ken5 on 2009-07-11
I am also hoping that there is an English version of this. I have the same model a4tech pk-835...

I tried to click on test on skype after trying the easycam installation(not sure if I did the installation correctly). I only get green, blurry image. 

My webcam has a good display in cheese. I am not sure if this is a skype issue or not. 

Any advice on this?

Thanks in advance.

---

### Post by jas007 on 2009-10-25
> Is there by chance an english version of the software? This is in french.

Hi Just downloaded the easycam2.deb package and installed it. I had to translate the French to English. So here is the translation (No need for more than one person to do this).


**First Window: *Bienvenue dans 'assistant Easycam! Vous souhaitez?* > Welcome Wizard EasyCam! You want?**
*Installer votre webcam* > Install your webcam
*Tester* > Test
*Installer v4l-dvb* > Install v4l-dvb 
*Depanner apres installation *> Troubleshoot after installation 
*Question* > Question
*Quit* > Quit


**Selecting *Installer v4l-dvb* **

*Par l'archive (fourni par EasyCam)* > For the archive (provided by EasyCam)
*Par internet (Derniere version)* > By Internet (latest version)

**Selecting *Par internet (Derniere version)***

**New Window: *Assistant d'EasyCam* > Wizard of Easycam**

*Installation terminee! J'espere que cette mise a jour vous permet d'utliser votre webcam * > Installation complete! I hope that this update enable you to use your webcam

My webcam is now 100% working, on 9.04 64 bit.:P

---

### Post by jas007 on 2009-10-25
Sorry to double post but I should have mentioned. That I get the error

An error occurred while loading or saving configuration information for gui.py. Some of your configuration settings may not work properly.

when loading easycam. I also cannot get the tester function in the easycam gui to work. But the camera is detected and working with cheese and skype 2.1 beta.

Jason

---

### Post by unteer on 2010-07-20
Just an FYI to anyone who stumbles upon this thread:

if you attempt to install the EasyCam2 packages on Ubuntu 10.04 just in a vain attempt to get your webcame working, you will come across the package dependency for python-xml.  The python-xml package has been deprecated for use in Ubuntu and is thus not available in the repositories for 10.04.  I hope that saves some people some minutes.  Cheers!

---

