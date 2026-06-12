---
title: "CD won't install over HP Unix with lif"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by landloper on 2009-10-12
Hi All,
I looked all over for this before posting - I hope it's not a duplicate question.
I have a used HP C3750 with HP-UX on it, tried to install Ubuntu 9.04 from CD. I have the CD set as 1st boot drive and physically removed the 2 slide-out SCSI hard drives from the PC. Still, the PC boots some sort of OS, and will only boot from the hard drive, requiring a login and password I don't know. Trying to boot from the CD, it says I don't have a lif file. So I can't boot the PC to format the drive or anything.
I don't care about the OS or data already on the PC, I just want to install Ubuntu.
Any ideas? Thank you for your help.
- landloper

---

### Post by brbpab94 on 2009-10-12
disable password in your bios

---

### Post by landloper on 2009-10-13
I can't find a way to access the BIOS, but I think it is a different issue.  I will try to explain better than I did before.
This used castoff HP c3750 PC has a company's HP-UX on it.  I can get it to boot from the CD drive initially, but the 64 bit Ubuntu CD gives an error message like this:
ipl error bad lif magic not a valid lif volume
so I can't get the Ubuntu CD to boot the machine.  I don't want to preserve any data or use more than one OS.  I can get to ISL, if I could format the drive from there (if I knew how), but even with the 2 hard drives removed, it gives the error booting from the CD, it doesn't seem that that would help.
Thanks for looking...  anybody have an idea?

---

### Post by Mark Phelps on 2009-10-14
I think a problem you're going to have is that it uses a RISC processor, and I would be surprised if the standard Ubuntu 9.04 build can work on that processor.  You may need a kernel version specifically for a RISC processor.  There are different kernel versions, I just don't remember which ones they are.

---

### Post by rob2uk on 2009-10-14
There is an ISO image for HP RISC-based servers at [http://cdimage.ubuntu.com/ports/releases/jaunty/release/]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/")

I don't think the server installs come with a DE as default, so you'd need to install ubuntu-desktop (or your preferred flavour) once done

---

### Post by landloper on 2009-10-14
Thanks Mark and rob2uk!  It is a RISC processor, though I don't really know what that means yet, either.  I will try the other ISO image when I get home to it.  The old HP C-3750 only has 8 meg. of memory, but it was free.  I hope it works.
I really appreciate your sharing your experience.  It helps a lot.
- landloper

---

### Post by rob2uk on 2009-10-15
> **landloper said:**
> Thanks Mark and rob2uk!  It is a RISC processor, though I don't really know what that means yet, either.  I will try the other ISO image when I get home to it.  The old HP C-3750 only has 8 meg. of memory, but it was free.  I hope it works.
I really appreciate your sharing your experience.  It helps a lot.
- landloper

8 meg?

That's WAY below the minimum spec...

---

### Post by earthpigg on 2009-10-15
are you sure you don't mean 8 gb of ram, and not 8 mb...?

how old is this machine?

if it ***really*** does have 8mb of RAM, you will be taking a trip in the wayback machine and experience great deals of difficulty trying to install what we consider a usable operating system in 2009 on it....

...honestly, if it is that old, still ran fine, and where mine?

i'd leave the HP-UX on it, wait a few years, then sell it to a collector for several thousand dollars.

or donate it to a museum. seriously - it would be considered a very valuable artifact to the right museum.


try the command 'free' at the terminal of the current operating system and tell us what you get.

---

### Post by Mark Phelps on 2009-10-15
Spec sheets say it has 512MB to 8GB of memory, not 8MB.

---

### Post by landloper on 2009-10-15
8 Gig it is...  Thanks, guys.  By the way, the image you suggested booted right up.  I am going to learn a lot on this machine (Translation: What did I get myself into now?)
Again, thanks for your help.

---

### Post by rob2uk on 2009-10-15
> **landloper said:**
> 8 Gig it is...  Thanks, guys.  By the way, the image you suggested booted right up.  I am going to learn a lot on this machine (Translation: What did I get myself into now?)
Again, thanks for your help.

Glad to be of help :)

I did stop to think after I posted the last reply that there was no way you could mean 8 meg - I'd only just been looking at the product page on hp.com and what I was seeing was definitely not an Atari ST era machine ;)

8gb puts you WAY ahead of most current users - looks like you got yourself a top machine - enjoy it, especially if you got it cheap :)

EDIT: cleaned up my drunken typo

*can't find a drunk smiley, so just imagine one*

---

### Post by landloper on 2009-10-16
I installed Ubuntu desktop, then noticed rob2k talked about the server software.  Both are at the site he pointed me to.
Should I have installed the server version?  It is a single dedicated RISC machine that will access the internet in my home wired network.  What is the difference between server and desktop?
Also, since this install doesn't have a DE, how can I
a) get a DE on a CD to install it so I can follow the doc's directions to connect to the internet or 
b) connect to the internet without a DE, then how do I get a DE using the command line?
Thanks for the help
landloper

---

### Post by ShizzlePDX503 on 2009-10-16
sorry new to the linux world and just wanted to know what DE stands for? I see it a lot in the forums and wondered what it stood for?

check out the ubuntu website for the differences in the desktop edition and the server edition... If you are just going to use it as a regular computer then I would go with desktop edition. I am however a new ubuntu user so that doesn't give much help to you.

---

### Post by landloper on 2009-10-16
Hi Shizzle,
I'm new too.  DE is Desktop Environment.  It is a graphical interface plus applications.  I had to look it up myself.  I am reviewing the Ubuntu documentation online, even though I haven't gotten mine installed yet.  It helps a lot.
-landloper

---

### Post by ShizzlePDX503 on 2009-10-16
the desktop edition is if you are using the computer for normal things such as web browsing, documents (openoffice), email, any other day-to-day usage. server editon is more for network things such as a file, print, web server type stuff. though this is a brief description of their usages there are many usuages for each version of the OS.

thanks for the definition... I tried looking on google and all I got was a bunch of linux sites in european languages like german and dutch.

---

### Post by rob2uk on 2009-10-16
> **ShizzlePDX503 said:**
> the desktop edition is if you are using the computer for normal things such as web browsing, documents (openoffice), email, any other day-to-day usage. server editon is more for network things such as a file, print, web server type stuff. though this is a brief description of their usages there are many usuages for each version of the OS.



Almost.

The HP RISC server edition is, for all intents and purposes, the same as the desktop edition, except:

- It actually supports the processor in the C3750
- It supports the full 8gb of RAM in the C3750
- It doesn't come with a Desktop Environment or any of the extras such as Pidgin, Evolution, Firefox, etc.

After installing the server edition, it's as simple as connecting the machine to the ethernet, and typing

```
sudo aptitude install ubuntu-desktop
```

*ubuntu-desktop* installs everything that comes as standard in the desktop edition - after a reboot you'll have the Gnome Desktop Environment and all the shiny extras that come with a standard Ubuntu install

---

### Post by landloper on 2009-10-16
Then I will install the server edition and go from there.  This is going to be fun!  Thank you for taking time to help out.
-landloper

---

### Post by landloper on 2009-10-17
I need some more help...  The alternate PA-RISC imagesfor 9.10, both desktop and server, give me a "No common CD-ROM drive was detected." error.  I switched out physical CD-ROMs - same error.I found this on the forums:
[http://ubuntuforums.org/showthread.php?t=973831](http://ubuntuforums.org/showthread.php?t=973831), which suggested I install 8.04 then upgrade, because of a bug in 9.10 and 8.10.
I can only find x86 and AMD64 alternate install images.  Does anyone know if there is an 8.04 install for RISC?
While I'm asking, while booting 9.10 desktop or server, the image says it can install 32 or 64-bit, then defaults to 32 and says, "kernel name doesn't end with 32 or 64".  How can I get it to install 64-bit?
Thanks,
landloper

---

### Post by ShizzlePDX503 on 2009-10-17
I think this is what you are looking for:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

also the howto:
[https://help.ubuntu.com/8.04/installation-guide/hppa/index.html](https://help.ubuntu.com/8.04/installation-guide/hppa/index.html)

---

### Post by ShizzlePDX503 on 2009-10-17
BTW, I used to goto Oceanside alot when I was in the Marine Corps.

---

### Post by landloper on 2009-10-17
I looked and looked for that file.
I live a stone's throw from the base - Thanks again, Shizzle

---

### Post by ShizzlePDX503 on 2009-10-17
I hope that is the correct one that you need. I just type ubuntu 8.04 risc into google and that is what I got.  hope the best of luck for you and hopefully no more errors. :)

---

### Post by ShizzlePDX503 on 2009-10-22
how did the install go?

---

### Post by landloper on 2009-10-28
I was able to install 8.04 from the info you gave me, Shizzle.  Then I had to leave town, and just got back.  I can't get the desktop to install now.  I will have to get back to it to see what the error is, or I could try upgrading from 8.04 then installing the desktop.  Thanks for the help.
-landoper

---

### Post by landloper on 2009-11-01
I'm in need of more help.  I did get 8.04 installed, and could use the command line.  I installed the desktop with 'sudo aptitude install ubuntu-desktop', and it went through the whole installation.  On reboot or when I typed startx, the desktop tries to load, and I get: "glibc detected /usr/bin/x: invalid pointer: 0x001cfd64" which locks up the machine.  This message stays at the top of the screen, and I can type text, but nothing does anything.  Thanks for your help.
-landloper

---

### Post by ShizzlePDX503 on 2009-11-02
Not sure what to tell you there... hopefully someone else will read this thread and have an idea for you

best of luck!

---

### Post by landloper on 2009-11-04
I'm going to put this in here - may not be the right posting.  I could install only 8.04 on my RISC machine, but could not get the DE to work.  I started over, using Debian 5.0.3, loaded KDE, then got to a blank screen.  I think it a video driver problem.  Card is HP A4982B Visualize fxe (there are two in the PC - connected to only one).  How do you find and install a video driver for this?  Thanks for the help.  Sorry if this is not the right place to post - I'm trying to learn, and would install Ubuntu if it supported PA-RISC HPPA.

---

### Post by ShizzlePDX503 on 2010-05-15
-delete-

---

### Post by ShizzlePDX503 on 2010-05-15
not sure if you ever got this working but I came across this, which looks like a lot of useful information from the manufacturer:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&taskId=&prodSeriesId=295887&prodTypeId=12454](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&taskId=&prodSeriesId=295887&prodTypeId=12454)

System Specs listing:
[http://h18000.www1.hp.com/products/quickspecs/11579_div/11579_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11579_div/11579_div.HTML)

Looks as though you were on the right track with installing Debian. [http://www.openpa.net/linux_pa-risc.html](http://www.openpa.net/linux_pa-risc.html)
[http://www.parisc-linux.org/](http://www.parisc-linux.org/)

---

