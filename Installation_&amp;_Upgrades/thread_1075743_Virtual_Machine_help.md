---
title: "Virtual Machine help"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by Stavro on 2009-02-20
Hi All,

I’m very interested in acquiring a new computer soon without Windows installed because after a lot of experience with Vista on other peoples computers I don’t really want it.

I would like to try Ubuntu as my main OS, I’ve tried it before and liked it and so will either get the shop to install it or do this myself, however, there are a couple of Windows specifics applications that I cannot do without. I’m a musician and have a notation package that I really like plus a software synthesizer to go with it, I also am a keen computer chess enthusiast and will want to continue using my chess packages. Both the musical and chess software are quite expensive and so I won’t drop them just yet.

Therefore, I would like to run Windows in a virtual machine, I own a full copy of Windows ME which I’m actually happy with and it runs my packages flawlessly. I don’t want to dual boot, I really want to do without the hassle of shutting down one and going into another. I think Windows ME should be fairly easy to run in a virtual machine, though I’m not an expert and this is what I would like to ask about.

How easy is this to setup? I know how to install Ubuntu, I just want Windows ME in a virtual machine. Does anyone know how much success I’m likely to get regarding sound, USB etcetera in the virtual machine? If it helps, the computer is built with with linux in mind, so everything works out the box on that front.

Any help is most appreciated. I want something simple and reliable. Finally, the processor is 64-bit, will this be a problem?

---

### Post by howefield on 2009-02-20
Couldn't be easier !!

Once you have Ubuntu installed, install the PUEL (personal use and evaluation licence) version of Virtualbox from virtualbox.org that corresponds with your version of Ubuntu. There is an OSE,.. (Open Source Edition) version of virtualbox in the repository but it doesn't have support for USB, which you obviously need).

You will then create the virtual machine and install windows into it using your copy of ME.

---

### Post by Therion on 2009-02-20
This is how you set up a virtual machine in Ubuntu using VirtualBox (see link below).  

The key to getting USB working in VirtualBox is to 1) Download the newest version of VirtualBox from their website (ignore the link in the tutorial) and 2) Being sure to get the PUEL (Personal Use) version.  From there, it's just a matter of following the instructions:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

Think you can handle that?

---

### Post by Stavro on 2009-02-20
Thanks, but how complicated is this? Does it have wizards to set how much disk space and RAM etcetera Windows ME is allowed? I hope you don't mind me asking so much. Is it expensive? Finally, Windows ME is normally installed by booting from a floppy disk drive and then accessing the CD-ROM setup program, but my new computer will not have a floppy disk drive so how do I start DOS in the virtual machine so as to be able to run the Windows ME setup?

---

### Post by Regnulify on 2009-02-20
64 bit is not a problem. 32 bit OSes run just fine in VBox. I run a combination of both.

---

### Post by Stavro on 2009-02-20
Oh, wonderful, thanks for the link Therion, I was writing the above reply before I read your post. I think I can manage this. ;)

---

### Post by Stavro on 2009-02-20
> **Regnulify said:**
> 64 bit is not a problem. 32 bit OSes run just fine in VBox. I run a combination of both.

Cool, I have to say this forum is really helpful and fast! Anyone else ran a DOS operating system like Windows ME in a virtual machine? I bet it is blazing quick on modern hardware?

---

### Post by Therion on 2009-02-20
> **Stavro said:**
> Cool, I have to say this forum is really helpful and fast! Anyone else ran a DOS operating system like Windows ME in a virtual machine? I bet it is blazing quick on modern hardware?
ME, no.  XP yes.  Or at least I did.  XP was pretty snappy with 512MB of RAM set aside.  I had all the usual stuff up and running without any problems (e.g. MS Office, Nero, etc.) but bear in mind there's no (stable) support for anything that requires 3D acceleration.  So, in short, no real complaints.  

Well, other than .NET Framework-bloat, install Validation, WGA, Silverlight...

---

### Post by Stavro on 2009-02-20
> **Therion said:**
> but bear in mind there's no (stable) support for anything that requires 3D acceleration.  So, in short, no real complaints.

No problem, I'm not particularly fussed about all that stuff anyway. I've been using Windows ME for years so as you can imagine I'm not so interested in being "cutting-edge"! I use a lot of "standard" programs that write to the screen in a conventional way.

> **Therion said:**
> Well, other than .NET Framework-bloat, install Validation, WGA, Silverlight...

haha, yes, I know. On the plus-side of ME, at least it doesn't have WGA, uPnP (a huge risk) disabled by default, silverlight can't be installed and .NET is not so well supported which forces you to use a lot of the classic API applications that were actually well written. I'm the sort that if it works don't change it.

---

### Post by Stavro on 2009-02-20
Sorry to ask one more question please, but can an OS in a virtual machine easily connect to the internet connection provided by Ubuntu? How is this done, emulating a network adapter?

---

### Post by Therion on 2009-02-20
> **Stavro said:**
> Sorry to ask one more question please, but can an OS in a virtual machine easily connect to the internet connection provided by Ubuntu? How is this done, emulating a network adapter?
You'll see no difference in your internet connectivity when using your WinME virtual machine, or at least I never did when using XP in a VM.

I honestly don't know how; Virtualization is **PFM** as far as I'm concerned.

---

