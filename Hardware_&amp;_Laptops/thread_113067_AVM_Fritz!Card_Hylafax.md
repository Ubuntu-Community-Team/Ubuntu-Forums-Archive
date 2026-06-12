---
title: "AVM Fritz!Card Hylafax"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by lptr on 2006-01-05
Anyone got this AFCH combination working, yet? 

rob*

---

### Post by Amon_Re on 2006-01-05
[QUOTE=lptr]Anyone got this AFCH combination working, yet? 

rob*[/QUOTE]

[http://www.hylafax.org/archive/2004-11/msg00442.html]("http://www.hylafax.org/archive/2004-11/msg00442.html")

---

### Post by lptr on 2006-01-06
[QUOTE=Amon_Re][http://www.hylafax.org/archive/2004-11/msg00442.html]("http://www.hylafax.org/archive/2004-11/msg00442.html")[/QUOTE]

We are in Breezy 5.10, right?

I know that it has been done with previous kernel versions from Debian, though. I found a very nice description for Debian Sarge Kernel 2.6.8-2-686 in PDF form (German language form, too - sorry - see attachment).

Breezy comes with:
# cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8 )) #1 Mon Oct 10 13:14:36 BST 2005

I could not even find linux-headers-2.6.12.9-i386 in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but linux-headers-2.6.12.10-i386 and this do not install because of dependency problems.

Why I need this? Obviously there are no drivers provided for AVM Fritz!Card PCI for linux-source-2.6.12.9-i386 installed with breezy. So I need to build the Fritz! drivers myself from sources to be downloaded from AVMs homepage [http://www.avm.de/de/Download/index.php3](http://www.avm.de/de/Download/index.php3).

They do having a similar 'source' construction that Nvidia provides, too. Something in a lib that will be plugged into the running system to get it running.

Because I am not the real kernel freak, I would like to keep my running kernel version. Things are difficult enough without building a new one :( 
having a RAID1 running for data.

Anyone knowing where I can get 2.6.12.9 sources/headers?

rob*

---

### Post by Amon_Re on 2006-01-06
[QUOTE=lptr]We are in Breezy 5.10, right?

I know that it has been done with previous kernel versions from Debian, though. I found a very nice description for Debian Sarge Kernel 2.6.8-2-686 in PDF form (German language form, too - sorry - see attachment).

Breezy comes with:
# cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8 )) #1 Mon Oct 10 13:14:36 BST 2005

I could not even find linux-headers-2.6.12.9-i386 in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but linux-headers-2.6.12.10-i386 and this do not install because of dependency problems.

Why I need this? Obviously there are no drivers provided for AVM Fritz!Card PCI for linux-source-2.6.12.9-i386 installed with breezy. So I need to build the Fritz! drivers myself from sources to be downloaded from AVMs homepage [http://www.avm.de/de/Download/index.php3](http://www.avm.de/de/Download/index.php3).

They do having a similar 'source' construction that Nvidia provides, too. Something in a lib that will be plugged into the running system to get it running.

Because I am not the real kernel freak, I would like to keep my running kernel version. Things are difficult enough without building a new one :( 
having a RAID1 running for data.

Anyone knowing where I can get 2.6.12.9 sources/headers?

rob*[/QUOTE]

[http://www.kernel.org](http://www.kernel.org)

---

### Post by lptr on 2006-01-07
> [FONT="Arial Black"]http://www.kernel.org/pub/linux/kernel/v2.6/[/FONT]

Thanks... had been already there. 

Could not find 2.6.12-9 - sorry - even changelog stops with [   ] ChangeLog-2.6.12.6  !!

Another ideas?

rob*

p.s. Wouldn't it be much easier for us all when the maintainers of Breezy would place sources in official apt form? Thanks a lot for this in advance... :KS

---

### Post by Amon_Re on 2006-01-07
[QUOTE=lptr]Thanks... had been already there. 

Could not find 2.6.12-9 - sorry - even changelog stops with [   ] ChangeLog-2.6.12.6  !!

Another ideas?

rob*

p.s. Wouldn't it be much easier for us all when the maintainers of Breezy would place sources in official apt form? Thanks a lot for this in advance... :KS[/QUOTE]

I don't know about the Breezy sources, i'm pretty new to it, but if the changelog on kernel.org stops at 2.6.12.6, then there's no newer official kernel

However, i did find a gentoo ebuild for 2.6.12-r9, wich is nothing more then vanilla 2.6.12 with patches applied.

---

### Post by lptr on 2006-01-07
[QUOTE=Amon_Re]I don't know about the Breezy sources, i'm pretty new to it, but if the changelog on kernel.org stops at 2.6.12.6, then there's no newer official kernel

However, i did find a gentoo ebuild for 2.6.12-r9, wich is nothing more then vanilla 2.6.12 with patches applied.[/QUOTE]

Mumble mumble... 

:confused:I am starting to bruxism. Finally got here doing this:
[SIZE="2"]http://ubuntuforums.org/showthread.php?t=84174&highlight=building+kernel+howto
[/SIZE]
did as RubenGonc told there but didn't this (as no desktop machine):

> In "General Setup" activate:
-Support for paging of anonymous memory (swap)

There isn't 1GB at my .config just 4GB or 64GB so I took 4GB.
> 
-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM


"Processor type and features": Used P4 

building was ok. .deb created installed it with 
[SIZE="2"]#sudo dpkg -i kernel-image-2.6.14*.deb
[/SIZE]

restart during boot Linux told me that it cannot mount my dmraid device [SIZE="1"]
(see this here: [http://ubuntuforums.org/showthread.php?p=635263#post635263](http://ubuntuforums.org/showthread.php?p=635263#post635263))
[/SIZE]

Restarted next time using original kernel 2.6.12.9 - RAID being back as before.

Now I'm building kernel again with i386 support only. Hopefully dmraid working there so I can continue with AVM driver integration (I do need hylafax working with Fritz!Card).

Kernel builds take a very loooong time so maybe some insights I should be followed supporting my dmraid? Suggestions would be highly appreciated.


[edit1]
This kernel cannot dmraid, too 

[edit2]
should have been read the whole thread - there are mount problems...

[edit3]
# uname -r
2.6.12-10-686
Don't ask me - anyhow after building kernels, then lots of fiddling around with apt-get deinstalling packages reinstalling others, this kernel inclusive linux-headers got somehow here on the machine.

---

