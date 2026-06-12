---
title: "Persevere or default to Windows?"
date: 2008-10-09
forum: General Help
---

### Post by sn3rd on 2008-10-09
I have a friend who is a long time Windows user. He recently (about 2 months ago), after using my Ubuntu box a bit, he asked me to help him try Ubuntu, which, obviously, I agreed to.

His system is as follows:
350W Power supply
Celeron 2.4GHz (Socket 478)
ASRock P4VM8 Motherboard
768MB RAM
Sapphire Radeon 9550 128MB

Ever since installing, we've had problem after problem.

[LIST]
[*]The first thing was getting the ATI drivers installed. Followed the instructions on the forum for getting "ati drivers installed on any version of...", and didn't get it right first time, but tried a few more times and eventually got it right (some weird combination of dpkg-reconfigure xserver-xorg and aticonfig --initial). So then ATI drivers were working.
[*]Next, he had issues with video. I've always just used VLC. His VLC was displaying horizontal lines in the video. After trying various video output modules (everywhere we found suggested using X11, which we tried, but it still gave the same problems). The computer's CPU usage was also spiking to 100% while watching videos.
[*]We gave up trying to get that to work, and decided to try use Windows VLC through wine. This worked, but still not perfectly (horizontal lines were still visible, but to a lesser degree, and still very high CPU usage). We decided to try the driver from ATI's website.
[*]We installed ATI driver from their website. This allowed us to use the OpenGL video output module on VLC, which dropped the CPU usage down to about 40 - 50%, but we experienced random flickering. After disabling Compiz, we found it worked fine. But we were still experiencing the horizontal lines.
[*]Our next approach was to try VirtualBox, since VLC on his Windows XP doesn't give any issues whatsoever. The install went fine etc, but VirtualBox alone pushes the CPU usage up to about 50%, and then VLC in VirtualBox (XP) pushes it up to 100% again. Even with Compiz disabled (and only minimal applications and services running).
[*]We gave up on the VLC for now.
[*]Our next problem was that he needs Microsoft Office 2007, mostly for compatibility with his peers' documents (especially preserving formatting). This simply did not want to install. I have installed Office 2003 with success, and am currently trying to convince him to use that instead. In the meantime, I remember seeing some advice given regarding an Office 2007 install using wine where users were getting the "not installed for current user" problem. I can't remember where I saw that, with its accepted solution. Does someone have a link for me, please?
[*]His sound is not working correctly. Sound plays and doesn't use up too much of his CPU's capacity, but sometimes the sound skips and distorts. We have tried using Pulseaudio, Alsa and OSS, all with the same results. What would be the first thing to look for here?
[/LIST]

So the question is...
Should he just go back to Windows, or keep persevering? I'm by no means an expert, but I have at least had some experience. However, most of the systems I have configured have presented little or no problems. If not, does anyone have any solutions? Or links to helpful articles?

Any suggestions would be appreciated.

---

### Post by Forbees on 2008-10-09
when installing the ATI driver . . . you should have just clicked on the restricted driver icon (it appeard where the updates do). might be too late for that. but you can get ATI drivers from add/remove apps . . . that might fix the VLC

microsoft office? for why

OPEN OFFICE!!!!!!! :)

---

### Post by Spaceman9 on 2008-10-09
Not all distros work equally well on all hardware combinations. So Ubuntu might work really well on you're computer but not on your friends. I can't run Fedora 9 on my computer at all. Just won't work with my hardware.

You could try Mandriva 2009 (based on RedHat) or Sabayon (based on Gentoo). Or even Linux Mint (based on Ubuntu).

In regard to Microsoft Office 2007 try OpenOffice. It's 100% Microsoft Office 2007 compatible. It can read and save in doc file format. If you really need tokeep using Microsoft Office 2007 install wine into your Linux distro. Microsoft Office 2007 should work with wine.

---

### Post by sn3rd on 2008-10-09
> **Forbees said:**
> when installing the ATI driver . . . you should have just clicked on the restricted driver icon (it appeard where the updates do). might be too late for that. but you can get ATI drivers from add/remove apps . . . that might fix the VLC

I did do that... Didn't help. And the ATI driver from the repositories isn't the same as the one from the ati.com. VLC gives issues whether using ati.com's driver or fglrx etc from the repositories.

> **Forbees said:**
> 
microsoft office? for why

OPEN OFFICE!!!!!!! :)
I agree. But as I said, it's for compatibility reasons.

---

### Post by sn3rd on 2008-10-09
> **Spaceman9 said:**
> Not all distros work equally well on all hardware combinations. So Ubuntu might work really well on you're computer but not on your friends. I can't run Fedora 9 on my computer at all. Just won't work with my hardware.

You could try Mandriva 2009 (based on RedHat) or Sabayon (based on Gentoo). Or even Linux Mint (based on Ubuntu).

In regard to Microsoft Office 2007 try OpenOffice. It's 100% Microsoft Office 2007 compatible. It can read and save in doc file format. If you really need tokeep using Microsoft Office 2007 install wine into your Linux distro. Microsoft Office 2007 should work with wine.

It isn't 100% compatible. It loses formatting etc. And it can't save as .docx

And I have tried wine with 2007, which gives the issue above after following the guides on the web (as mentioned in my original post)

Edit: Typo... In my original post, I said it wouldn't install... Eventually we got it installed, but it wouldn't run (it gave the error that it wasn't installed for the current user)

---

### Post by sn3rd on 2008-10-09
Just remembered another issue he is having. Randomg lock ups. From what I can tell, Completely random, and it happens at any time (has happened in console, in gnome, while browsing, while watching video, while listening to music, while playing freecell, etc).

I read that powernowd can cause issues someimtes, so I disabled it, and the problem seemed to clear up (for a day or so). But it turns out that was just placebo, because it is still happening. Any ideas where to start?

This issue doesn't occur in Windows.

---

### Post by WWSmith36 on 2008-10-09
> he needs Microsoft Office 2007, mostly for compatibility with his peers' documents (especially preserving formatting)

Open Office will preserve the formatting.  You just need to make sure you have the microsoft fonts installed. 

They are included in the  multiverse repository in the package ubuntu-restricted-extras or you can get them with 

```
sudo apt-get update
sudo apt-get install msttcorefonts cabextract
```

---

### Post by doas777 on 2008-10-09
the specs are a little low (and i hate seeing the word 'celeron'). I had to upgrade my old celeron 3ghz to get it to play new video files. old ones were no problem though. you can build a pretty powerful AMD box for less than 350USD if you have a case (and use a free os). I gaurentee you will have a much better experience.

ubuntu is not like the old linux distros that worked really well on low spec hardware. if you want good performance on a old box, you might want to look at DSL or gentoo, or even straight debian. xubuntu might work as well.

as for ms office wine's [appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992") gives office 2k7 a gold rating, which means it should run pretty well.
good luck,
Franklin

---

### Post by sn3rd on 2008-10-10
> **doas777 said:**
> the specs are a little low (and i hate seeing the word 'celeron'). I had to upgrade my old celeron 3ghz to get it to play new video files. old ones were no problem though. you can build a pretty powerful AMD box for less than 350USD if you have a case (and use a free os). I gaurentee you will have a much better experience.

ubuntu is not like the old linux distros that worked really well on low spec hardware. if you want good performance on a old box, you might want to look at DSL or gentoo, or even straight debian. xubuntu might work as well.

as for ms office wine's [appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992") gives office 2k7 a gold rating, which means it should run pretty well.
good luck,
Franklin

Thanks for this reply regarding the processor!

---

### Post by Spaceman9 on 2008-10-12
sn3rd I found this about OO

OpenOffice.org welcomes gatecrashers to version 3.0 orgy [http://www.theregister.co.uk/2008/10/10/openoffice_org_party/](http://www.theregister.co.uk/2008/10/10/openoffice_org_party/)

I hope it will be of help to you.

---

