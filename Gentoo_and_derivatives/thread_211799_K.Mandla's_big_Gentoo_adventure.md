---
title: "K.Mandla's big Gentoo adventure"
date: 2006-07-08
forum: Gentoo and derivatives
---

### Post by K.Mandla on 2006-07-08
I decided it was time to get my hands dirty. I have a spare laptop (yes, a spare ... everyone has spares, don't they?) installing now, and I'm picking my way through the howto guide. 

This is a first for me; I cut my teeth on Ubuntu and dabbled in Arch a little, but Gentoo seems like a necessary next step. I want this to be a learning experience, even if it falls flat.

So far I'm fairly comfortable with the process. I like the idea of booting into a live environment and building the system underneath you. 

Of course, I'm just getting started and I'm taking it as slowly and carefully as I can. I managed to download the stage 3 tarball and the portage files, even though I'm not sure yet what they do.

The test machine is a 1Ghz Dell Inspiron 8100. I decided on a laptop instead of a desktop, because I understand that it can take days to build a system, and I'd rather run a 60W adapter than a 300W PS for days on end. :)

Wish me luck! [-o< If you have any advice, I'd be more than happy to hear it.

---

### Post by K.Mandla on 2006-07-09
Well, the first try didn't work out so well, but I blame myself for that. I partitioned the hard drive in a way that differed from the manual, then couldn't remember what I had done. The startup yielded a kernel panic, so I'm starting over.

Thus far though, it has been exceptionally educational. All the commands and configurations I had taken for granted are a little clearer now. 

But yes, setting it up does seem to take a long time.

---

### Post by K.Mandla on 2006-07-10
Hey, wow. I did it. It works. Of course, I have no network because I messed that up. And I can't exactly do anything, but it boots. Didn't take as long as I thought it would. Cool. ;)

---

### Post by tseliot on 2006-07-11
> **K.Mandla said:**
> Hey, wow. I did it. It works. Of course, I have no network because I messed that up. And I can't exactly do anything, but it boots. Didn't take as long as I thought it would. Cool. ;)

Perhaps you didn't enable the support for your network card when you compiled your kernel (that happened to me too the 1st time I tried Gentoo)

---

### Post by K.Mandla on 2006-07-11
I have a feeling you're right. When I get the time, I'll start over and see if that works. 

I've taken a break for now but I think I'll try it again at the end of the week. If I can get some of the fundamentals working, I suspect I'll like Gentoo.

---

### Post by gratefultux on 2006-07-12
I also got a kernel panic the first time i installed Gentoo.  Second time worked, but i forgot PCMCIA, which isn't a big problem, but it was bothersome.  Especially since i realized it too late (read: after 30 hours of compiling KDE).  I never got myself to try it again, but i like the distro.
> If you have any advice
FOLLOW THAT MANUAL :-k .

---

### Post by viraptor on 2006-07-15
@gratefultux: You don't have to recompile whole system to get pcmcia to work! Just recompile the kernel to include hotplug / pcmcia subsystem and update packages that need it:
- add pcmcia to /etc/make.conf
- emerge -ND world (this updates only the packages that you have installed and that depend on pcmcia use flag)
It's possible, that you won't have to update anything other than kernel - I haven't got even one package, that uses pcmcia flag (but it's on server, so your 'world' set may be different) - kde surely doesn't depend on it.

---

### Post by synacktion on 2006-07-15
Gentoo is a lot of fun if you have some time on your hands - after using Gentoo for a while, you will be a much more efficient Linux user in general because it forces you to really learn the guts of your OS.  As far as your PCMCIA troubles go, I recommend this wiki page:

[http://gentoo-wiki.com/HARDWARE_PCMCIA_NIC]("http://gentoo-wiki.com/HARDWARE_PCMCIA_NIC")

---

### Post by gratefultux on 2006-07-15
Well, the problem was that without my pcmcia card, i don't have an internet connection.  I couldn't go to a nice forum like this one and ask someone how to recompile a kernel in gentoo, so i had to go by what the handbook said.  And the only point where it explicitly mentioned how to do it was in the beginning.  So my only option was reinstalling :( .
I formated and ended up installing Ubuntu :-D .

I might try gentoo again when i get my laptop.  That way i have a running system to browse the web.

---

### Post by Iandefor on 2006-07-16
Good luck! I tried Gentoo a couple of weeks ago. Didn't work out too well. For some reason, it partitioned my hard drive in a way that was exactly the opposite of what I thought I'd told it to do, which has sort of scared me off it for a while- if I'm so silly as to be unable to get the drive partitioned correctly, I don't want to screw around compiling my own system.

---

### Post by tseliot on 2006-07-16
> **Iandefor said:**
> Good luck! I tried Gentoo a couple of weeks ago. Didn't work out too well. For some reason, it partitioned my hard drive in a way that was exactly the opposite of what I thought I'd told it to do, which has sort of scared me off it for a while- if I'm so silly as to be unable to get the drive partitioned correctly, I don't want to screw around compiling my own system.

If you used the graphical installer I can tell you that I had the same problem when I partitioned my hard disk.

---

### Post by Iandefor on 2006-07-16
> **tseliot said:**
> If you used the graphical installer I can tell you that I had the same problem when I partitioned my hard disk. I did use the graphical installer. Well, glad to know it's not just me :).

---

### Post by K.Mandla on 2006-07-16
> **tseliot said:**
> If you used the graphical installer I can tell you that I had the same problem when I partitioned my hard disk.
There's a graphical installer ... ?! ](*,) 

I'd better dig out that spare laptop again. The more I think about it, the more I think I can get it working *this* time. I think I can, I think I can. ...

---

### Post by viraptor on 2006-07-16
> **K.Mandla said:**
> There's a graphical installer ... ?! ](*,)

It's relatively new - It might've not been ready yet, when you've tried to install your system...

---

### Post by gratefultux on 2006-07-18
Don't bother with the graphical installer.  For me it was a problem just to get the whole thing on the screen (it's too long).  I also never got past the preliminary information stuff before my computer rebooted.  Go with the text based installer and the excellent manual.

---

### Post by Iandefor on 2006-07-18
> **gratefultux said:**
> Don't bother with the graphical installer.  For me it was a problem just to get the whole thing on the screen (it's too long).  I also never got past the preliminary information stuff before my computer rebooted.  Go with the text based installer and the excellent manual. Yeah, I'd sort of been hoping it would actually provide similar functionality to the text-based installer.

---

### Post by tseliot on 2006-07-19
> **K.Mandla said:**
> There's a graphical installer ... ?! ](*,) 

I'd better dig out that spare laptop again. The more I think about it, the more I think I can get it working *this* time. I think I can, I think I can. ...

The installation failed 3 times (without an apparent reason) but in the end the installer froze and I had to hard reboot.

Then I saw that Gentoo had been installed with a completely invented partition layout.

The graphical installer definitely needs to be fixed.

---

### Post by vince32 on 2006-09-06
[SIZE="5"][/SIZE]
Even though I use Ubuntu and I have tried so many distro's I always go back to Gentoo, and I use Ubuntu, WinXP.
  
 Once you are bitten by the Gentoo bug it has you.
 I love setting up a new Gentoo system and do it differently every time.
If you want a good easy guide to go with Gentoo's handbook, Google with 3 words--->Gentoo kanotix slicer,just that way. It is the way I learned to install Gentoo. It's a little outdated but will explain how to setup the system easier then Gentoo's handbook. I have been using Gentoo about 3/years and still build my system with kanotix or knoppix cd and not gentoo's install cd.  I also use the Jackass Project for there guide for gcc-4.1 with enhanced Cflags.
 
Also for the Gentoo's new user there is and excellent Gentoo live-dvd that can be installed to your system called "SabayonLinux" RR4. This is good if you don't have the time to build your own system and get a feel of what Gentoo is all about.

I would be glad to help with setting up your Gentoo,using kanotix or knoppix drop an email with questions.


Vince32

Just a note I love my Ubuntu also and can't wait for edgy!!!!8)

---

