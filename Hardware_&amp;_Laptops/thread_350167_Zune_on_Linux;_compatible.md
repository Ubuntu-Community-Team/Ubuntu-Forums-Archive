---
title: "Zune on Linux; compatible?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by kloy1334 on 2007-01-31
Does anyone think or has anyone been able to set up their Zune on Ubuntu? Not to see the files, like said in XNJB, but to actually transfer the files. Would installing the Zune software via Wine be able to make it work? Oh, how I hate using Windows Vista right now.

This should be interesting.
Thanks in advance!

---

### Post by mjm115 on 2007-01-31
The Zune is just a digital media player, so Linux should be able to identify it like a regular MP3 player.  You could try it and see if that works.  I use Amarok, and it is pretty good at picking up the iPod and other MP3 players.

---

### Post by kloy1334 on 2007-01-31
The thing is that the Zune is "supposedly" incompatible with Linux and Mac. So far, publicity has only shared that it is viewable (but not transferrable) with applications for Creative players. I should've bought an iPod (hah)!

---

### Post by mjm115 on 2007-01-31
I still think you should try it.  The iPod is only compatible with iTunes, supposedly, but there are plenty of examples in the forum showing that the iPod does work on Linux, without iTunes.  Give it a try and you may just be happy with your results.

---

### Post by kloy1334 on 2007-01-31
Okay, I just tried it with Listen and no go. I'll try Banshee and then Amarok next.
And but right now, I'll try Zune on Wine, hope that works.

---

### Post by ErikTheRed on 2007-01-31
If you're planning on trying Amarok you'll need to recompile it with libmtp support, as the version in the repos doesn't have libmtp support. Even then there's no guarantees it'll work, since I tried it back when I first got my Zune and I could see the files but I couldn't add new ones.

---

### Post by Mammlouk on 2007-02-11
Current status is still the same.  I compiled libmtp 0.1.3 and amarok 1.4.5 to support it.  I can see the music on my zune and delete it, but cannot transfer any files either way.  hopefully support will be increased.  I also attempted connecting to the zune in VMWare and then transfering via Amarok, but Windows is accessing it the zune seems to be using a different protocol because Amarok fails to even connect.

---

### Post by codesplice on 2007-02-19
I've recently gotten a Zune as well, and have been doing some research on getting it to work.  It seems that the Zune PC Software has to perform some sort of handshaking with the device before it allows write access. This is the same reason that you have to have a sync session open in the software before you can add files to the device after doing the Windows registry hack to let it show up as a removable device in My Computer.  

So until someone figures out how to fake that handshake, I doubt that any existing programs will be able to interface with the player :(

---

### Post by c-breakdown on 2007-04-01
I'm keeping an eye on [Zune-Linux]("http://www.zune-linux.com/") for any updates.  And I also found a tutorial on ZuneBoards that says you can View songs on Zune, Delete Songs from Zune, Sync songs from Zune to Linux PC.

[Click Here For Tutorial]("http://www.zuneboards.com/forums/general-talk/2772-zune-linux-progress.html?highlight=linux")

I haven't tried those methods yet though, if anyone does before me please post the results!

[Edit:  I couldn't get Wine to run the setup, google "Zune Linux VMWare" for another solution]

---

### Post by Selcal on 2007-09-20
Thanks for that tutorial and all but i was curious if there was any way to flash the zune and make it into a linux device itself.  It would be awesome if it could be compatible with the 'muisc player'.  I just don't want to be dependent on anything windows at all.  

I know it was done on the ipod, has no one even attempted this yet?  I am kind of new to linux myself but i would be willing to learn and do this if anyone can give me a start.

---

### Post by brokencrystal on 2008-02-26
I would just be happy to be able to get the Zune software to install and run on WINE.  Since the WINE team is now working on getting .net apps to run in WINE via .mono, there may be hope in the future...  I hope this is a priority.  I am not sure if the Zune software depends on the .net framework, but the more compatible WINE is, the better chance of getting it to run.  I wonder if there is any terminal output I can submit to the WINE team while trying to install the Zune software so they have some idea on why it is failing...?

---

### Post by TWeerts on 2008-05-18
isnt the zune a drag and drop player anyways?

---

### Post by omega_user on 2008-07-03
> **TWeerts said:**
> isnt the zune a drag and drop player anyways?

No, it uses mtp and organizes files in it's own special hierarchy and categories determined by the zune software. It doesn't support a basic mini-filesystem like the one used in ipod-Linux's "userland".  So no, it's not drag and drop

---

