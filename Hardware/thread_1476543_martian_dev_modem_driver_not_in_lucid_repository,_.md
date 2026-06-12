---
title: "martian_dev modem driver not in lucid repository, but martian_modem is"
date: 2010-05-07
forum: Hardware
---

### Post by oryan_dunn on 2010-05-07
I have an old winmodem that I had installed under hardy using the martian_modem built from source.  This would build the userspace component program "martian_modem" as well as the kernel driver martian_dev.  The lucid repos now have a martian_modem package, but this seems to only include the userspace martian_modem app, and not the kernel driver martian_dev.  I don't mind building from source, but this computer is for my gf mom, and so I have to tell her to not download new kernels, or else she looses her internet access until I can stop by and rebuild the driver.  I was hoping to see a martian_dev module that would be updated as the kernel was updated, but no dice.  basically, the martian_modem package seems to be useless without a matching martian_dev driver as well.

Even if I were to get both installed, how do I go about adding a dialup connection to networkmanager?

---

### Post by oryan_dunn on 2010-05-08
> **oryan_dunn said:**
> I have an old winmodem that I had installed under hardy using the martian_modem built from source.  This would build the userspace component program "martian_modem" as well as the kernel driver martian_dev.  The lucid repos now have a martian_modem package, but this seems to only include the userspace martian_modem app, and not the kernel driver martian_dev.  I don't mind building from source, but this computer is for my gf mom, and so I have to tell her to not download new kernels, or else she looses her internet access until I can stop by and rebuild the driver.  I was hoping to see a martian_dev module that would be updated as the kernel was updated, but no dice.  basically, the martian_modem package seems to be useless without a matching martian_dev driver as well.

Even if I were to get both installed, how do I go about adding a dialup connection to networkmanager?

Ok, so I made some progress; I got the martian_dev module installed using packages from the repos, but it still requires manual intervention (I think) when a new kernel gets installed.

First, from multiverse, I installed martian-modem, which is the userspace component of the driver.  I didn't realize, but martian-modem-source is not the source package for martian-modem, but rather the source for the kernel module.  So I installed martian-modem-source, which also pulled in module-assistant.  Not knowing anything about that program, I took at look at this [page]("http://wiki.debian.org/ModuleAssistant") at the debian wiki.

Using those instructions, I did a ```
sudo m-a prepare
``` which pulled in several dependencies (which as I found out later, was not all that is needed).  Then I did a ```
sudo m-a update
``` and then listed the modules module-assistant could build ```
m-a -t list | grep -E '^[^ ].*\(' | cut -d " " -f 1 | sort 
```  After running this command, the martian-modem was not listed.  The FAQ of the debian wiki mentioned the directory /usr/share/modass/packages, and after looking at the installed files of martian-modem-source, noticed that it didn't update anything in that directory.  So I copied an existing script in that dir, called it martian-modem-source with permissions 755 and this content:```
#!/bin/sh
#
# (c) Eduard Bloch <blade@debian.org>, 2003
# generic maintainer script for module-assistant controled packages
# to be sourced or copied as example code

# autodetecting values. They may be overriden by the caller.

MA_DIR=${MA_DIR:-/usr/share/modass}
TARBALL=/usr/src/martian-modem.tar.bz2
BUILDDIR=${MODULE_LOC:-/usr/src/modules}/martian-modem

. $MA_DIR/packages/generic.sh

$1 "$@"

```

then reran ```
sudo m-a update
``` and martian-modem now showed up as a module that could be built.

To build the module, I ran ```
sudo m-a a-i martian-modem
``` which promptly failed on a quilt.make or similar error.  I then installed the package quilt and another dependency that the build failed on at a later step was the package debhelper.  After I had those installed, the module-assistant built the deb for the martian module and installed it.

Finally, after a reboot, the martian_dev kernel module was in use and the userspace program martian_modem was running.  I now had my /dev/ttySM0 link that I could use in GnomePPP.

So, now, how to get my ppp connection to show up and be managed by NetworkManager.  Is that even possible?

---

### Post by MichaelSM on 2010-06-29
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; module-assistant, error message &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                    &#9474; 
     &#9474; Installation of the martian-modem-source source failed.            &#8593; 
     &#9474;                                                                    &#9646; 
     &#9474; Ignoring this package. Maybe you need to add something to          &#9618; 
     &#9474; sources.list, maybe the contrib and non-free archives.  

           &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#9618; 
     &#9474;                                                                    &#8595; 
     &#9474;                                                                      
     &#9474;                               <Ok>                                   
     &#9474;                                                                    &#9474; 
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
      I made a script as suggested, and put it where it belonged(?) so now when I try  

sudo m-a a-i martian-modem                    

the above is the result.

By the way; in synaptic I think it shows that I was successful compiling martian as it is a package called martian-mobile-modules with my kernel 2.6.32-22-generic beside it.

Obviously close, but not close enough!

Any suggestions much appreciated.

Mike.

PS. I entered 'sudo m-a -t list | grep -E '^[^ ].*\(' | cut -d " " -f 1 | sort' which listed - amongst others -:

lufs-source
madwifi-source
martian-modem-source
mga-vid-source
misdn-kernel-source

martian-modem-source is the name I gave to the script, so looks like it turned up in the right spot.

---

### Post by peyre on 2011-05-06
Wow, oryan!  Your procedure got me up and running.  I have a Tecra 8100 with an Agere winmodem, running Lubuntu 11.04.  To help anyone who may need it, I'll clean this up and write it down as instructions rather than a history of what I did.  Hopefully I haven't forgotten anything here.

I installed martian-modem and martian-modem-source.  I also installed quilt and devhelper [SIZE="1"]([this site suggested I needed it]("http://old.nabble.com/Bug-473115%3A-martian-modem-source%3A-Does-not-compile-against-Linux-2.6.24-td16352407.html"))[/SIZE] in Synaptic.  Then I ran
```
sudo m-a update
```

Then, as you suggested, I went to /usr/share/modass/packages [SIZE="1"](you'll need root permission, so I did Alt-F2 and entered **gksudo thunar**)[/SIZE].  I copied one of the files there and pasted it into the same place, then renamed it **martian-modem-source**.  I opened a command prompt there [size="1"](easy to do with a right-click in Thunar)[/size], and entered **chmod 755 martian-modem-source**, and closed the command prompt.  Then I opened martian-modem-source, deleted what was inside, and pasted in that block of code:
```
#!/bin/sh
#
# (c) Eduard Bloch <blade@debian.org>, 2003
# generic maintainer script for module-assistant controled packages
# to be sourced or copied as example code

# autodetecting values. They may be overriden by the caller.

MA_DIR=${MA_DIR:-/usr/share/modass}
TARBALL=/usr/src/martian-modem.tar.bz2
BUILDDIR=${MODULE_LOC:-/usr/src/modules}/martian-modem

. $MA_DIR/packages/generic.sh

$1 "$@"
```

Then I ran
```
sudo m-a update
```
and
```
sudo m-a a-i martian-modem
```

It worked that time!  So I installed hwinfo from Synaptic, ran that from a command line, and now the modem shows in there as active.

I rebooted (don't know if that's necessary), and created a script on my Desktop containing the following:
```
gksudo ln -s /dev/ttySM0 /dev/modem
/usr/bin/kppp
```

For those unfamiliar with how Martian works, it assigns your modem to /dev/ttySM0, which is all well and good--except that KPPP doesn't offer that in its drop-down list.  So the first line of my script associates it with /dev/modem, one of the standard locations [size="1"](and I think the most common one)[/size].  Then it opens KPPP automatically, which saves me a step and makes sure I don't open KPPP before the modem is properly associated.

---

### Post by riig007 on 2011-06-27
Hi, how would I go about enabling more than one modem in the 
/etc/default/martian-modem configuration file.

Is there a way to setup 

ttySM0
ttySM1
ttySM2

??

right now, my ubuntu 10.04 setup is able to see ttySM0 and I have been
able to setup that one modem under Hylafax, but I need to add the other
two modems as well.

FYI, this is what I the system has installed:

**> dmesg | grep martian** 

[    8.581524] martian loaded - 20080620 
[    8.581631] martian 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    8.581672] martian: added device 11c1:44e BaseAddress = 0xdc00, CommAddres = 0xdbe8, irq = 16 
[    8.581691] martian 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    8.581726] martian: added device 11c1:44e BaseAddress = 0xdd00, CommAddres = 0xdbf0, irq = 17 
[    8.581742] martian 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    8.581767] martian: added device 11c1:442 BaseAddress = 0xde00, CommAddres = 0xdbf8, irq = 18 
[    9.865490] martian_modem is attached.

I have been looking all over the net for this, but I have had no luck.

Thanks.

---

### Post by peyre on 2011-06-27
I wish I knew.  I'm kind of a beginner myself, so adding multiple modems with martian is above my experience level.

---

### Post by Richie1980 on 2012-10-20
Hello,

i tried to çonfigure my win agere modem like Oryan Dunn described above.
But I didn'tr get the mistake away when I runned 

'sudo m-a a-i martian-modem' 

It always stops at 31 % with message 'module not succesfull buildt'

Even to install quilt and debhelper did not help. 

How can I fix that bug?

Thanx,

Richie.

---

