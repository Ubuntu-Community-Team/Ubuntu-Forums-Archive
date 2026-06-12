---
title: "Display problems and freezes"
date: 2008-08-01
forum: Hardware
---

### Post by mirchichamu on 2008-08-01
I installed and uninstalled ubuntu many times but my problem remains the same.
My display only 800* 640. My display driver ATI mobility radeon. When I upgrade. My laptop freezes. this is 4th time that I istalled fresh copy of ubuntu. Should I leave up fighting and say good bye to linux or my problem will be solved?

---

### Post by jkhh07 on 2008-08-01
i;m sure your problem will be solved. whats going on?

---

### Post by vk4ebp on 2008-08-01
Certain Radeon cards are notorious for not responding too well to Ubuntu. I have seen work-arounds described here, involving the 'alternative' CD images and installing the restricted ATI drivers from command line. I am sorry I cannot add more details, but this might help you in doing a search trough earlier posts

---

### Post by madarcher on 2008-08-01
are you able to drop into a shell (ctrl+alt+F1) before the system freezes?  If so you may be able to install the fglrx drivers from the command line.

```
sudo apt-cache search fglrx
``` may give you some clues.

John

---

### Post by mirchichamu on 2008-08-01
Thank you all. At the moment I am in low graphics mode, I can use ubuntu. The resolution is 800*640. Very uncomfortable.

---

### Post by mirchichamu on 2008-08-01
> **madarcher said:**
> are you able to drop into a shell (ctrl+alt+F1) before the system freezes?  If so you may be able to install the fglrx drivers from the command line.

```
sudo apt-cache search fglrx
``` may give you some clues.

John

Thanks madarcher. I got this screen.

---

### Post by Growbag on 2008-08-01
A quick note:

Ubuntu isn't ALL of Linux, it is merely somebody's version of it, it is a "Distribution".

Just because Ubuntu is giving you the s**ts, it's no reason to give up just yet, before you've really started.

If you can't get the problem fixed, try another Distribution, I would recommend these in order:

1. PCLinuxOS
2. Mandriva
3. openSUSE

You can find their homepages on distrowatch.com.

Each Distribution has a different "focus", but the ones I gave you are good for both beginners and hardware support.

Good luck :).

---

### Post by the7erm on 2008-08-01
It might be a shot in the dark, but you could try installing with the kubuntu iso, then if you want to run x/ubuntu install those from apt.

A friend of mine had problems with kubuntu isos, but not ubuntu isos.  While I was good to go with kubuntu, but ubuntu gave me problems :/  

After I installed kubutu, I installed ubuntu, and xubuntu with apt-get.

It's interesting to switch between them.  Although I've got to admit I kinda like xubuntu the most because I don't need flashy graphics :)

---

### Post by mirchichamu on 2008-08-01
> **Growbag said:**
> A quick note:

Ubuntu isn't ALL of Linux, it is merely somebody's version of it, it is a "Distribution".

Just because Ubuntu is giving you the s**ts, it's no reason to give up just yet, before you've really started.

If you can't get the problem fixed, try another Distribution, I would recommend these in order:

1. PCLinuxOS
2. Mandriva
3. openSUSE

You can find their homepages on distrowatch.com.


Each Distribution has a different "focus", but the ones I gave you are good for both beginners and hardware support.

Good luck :).

Thank a lot. I visited distrowatch but they are selling the live Cds and I have no credit card. Can you give me the address to download directly?

---

### Post by Growbag on 2008-08-01
PCLos: [http://iso.linuxquestions.org/download/290/1448/http/distro.ibiblio.org/pclinuxos-minime-2008.iso](http://iso.linuxquestions.org/download/290/1448/http/distro.ibiblio.org/pclinuxos-minime-2008.iso)

Mandriva:[http://mandriva.com/en/download/free](http://mandriva.com/en/download/free)

openSUSE: [http://software.opensuse.org/](http://software.opensuse.org/)

Google is very helpful :)

---

### Post by tamoneya on 2008-08-01
look on the right hand side of distrowatch and you will see a list of the most common distributions.  They have links to all the downloads there.

---

### Post by mirchichamu on 2008-08-01
Thanks a lot all those who are helping me>
I am in the process of downloading Pclinux os. My question is how to install? Is it like Installing Ubuntu? Is there anyway to install through Terminal?

---

### Post by Growbag on 2008-08-01
> **mirchichamu said:**
> Thanks a lot all those who are helping me>
I am in the process of downloading Pclinux os. My question is how to install? Is it like Installing Ubuntu? Is there anyway to install through Terminal?

I hope you're downloading minime2008!  It's much nicer than the 2007 version.

It's also a liveCD (like Ubuntu) and you simply click on "install".

But please try the others before installing because you will get a feel for what you like, and also which one works best with your hardware.

My personal favourite is openSUSE, but if I had to choose another it would be PCLinuxOS.

The reason for not using it:  their kernel is old (same as Ubuntu's) and doesn't work with my wireless card, whereas openSUSE does.

---

### Post by mirchichamu on 2008-08-01
> **Growbag said:**
> I hope you're downloading minime2008!  It's much nicer than the 2007 version.

It's also a liveCD (like Ubuntu) and you simply click on "install".

But please try the others before installing because you will get a feel for what you like, and also which one works best with your hardware.

My personal favourite is openSUSE, but if I had to choose another it would be PCLinuxOS.

The reason for not using it:  their kernel is old (same as Ubuntu's) and doesn't work with my wireless card, whereas openSUSE does.

Thanks once again.
It means that I will have to download the others as well. OOOOOOOOOps. If you use opensuse then I would have been advised the same. Yes I am downloading minime 2008.

---

### Post by Growbag on 2008-08-01
I'm not trying to hijack you from Ubuntu, don't get me wrong.

I was just suggesting that you try other things.

There is still no guarantee that any will work straight "out of the box", and you may find that you want to come back to Ubuntu and work through your display problems.

The great thing about Ubuntu is the forum, you will get good advice (mostly!) and fast as well.

I would recommend trying **envy** if you decide to give Ubuntu another go.  It automatically downloads and install the correct video driver.  Well, it used to do, not too sure with the recent Ubuntu addition, but check Alberto's website:

[http://www.albertomilone.com](http://www.albertomilone.com)

Envy has always worked for me in the past, it works for ATI as well as Nvidia

---

### Post by madarcher on 2008-08-01
You could try this:

```
sudo apt-get install linux-restricted-modules
```

then go to System --> Administration --> Hardware Drivers and enable ATI accelerated graphics driver.  Then reboot

I'm not promising anything but it's worth a try

John

---

### Post by mirchichamu on 2008-08-01
> **madarcher said:**
> You could try this:

```
sudo apt-get install linux-restricted-modules
```

then go to System --> Administration --> Hardware Drivers and enable ATI accelerated graphics driver.  Then reboot

I'm not promising anything but it's worth a try

John

Thanks madarcher for ur support.
The problem is not installation but that after installation my computer freezes.It happened several times.

---

### Post by mirchichamu on 2008-08-02
> **Growbag said:**
> I hope you're downloading minime2008!  It's much nicer than the 2007 version.

It's also a liveCD (like Ubuntu) and you simply click on "install".

But please try the others before installing because you will get a feel for what you like, and also which one works best with your hardware.

My personal favourite is openSUSE, but if I had to choose another it would be PCLinuxOS.

The reason for not using it:  their kernel is old (same as Ubuntu's) and doesn't work with my wireless card, whereas openSUSE does.

Thanks Growbag!
I tried to install pclinuxOS but failed several times. Now I am downloading opensuse. I don't know what will happen. You should be able to understand my miseries.I suffered a lot.By the way I should tell you that Envy also failed.

---

