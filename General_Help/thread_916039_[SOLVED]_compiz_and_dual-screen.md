---
title: "[SOLVED] compiz and dual-screen"
date: 2008-09-10
forum: General Help
---

### Post by malachi1990 on 2008-09-10
I know other threads on this particular problem exist, but none address the 
"Compiz extension not available" error I get when I try to use Compiz on a dual screen setup.  

If anyone has an idea, it would be greatly appreciated.

---

### Post by overdrank on 2008-09-10
> **malachi1990 said:**
> I know other threads on this particular problem exist, but none address the 
"Compiz extension not available" error I get when I try to use Compiz on a dual screen setup.  

If anyone has an idea, it would be greatly appreciated.

Hi and what is the model of the graphics card? You may also look at 
compiz-check
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
Moved to Desktop Effects & Customization :)

---

### Post by malachi1990 on 2008-09-10
Oh, sorry I forgot.  My video card is a Nvidia Geforce 7150.

Compiz check spit this out.

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7150M (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Thanks for your time.

Edit:

I forgot to add my direct check of compiz itself when I start it from terminal.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:12.0 0300: 10de:0531 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

I tried xgl, but it ultimately created other problems, as well as failing to solve the compiz issues.

---

### Post by malachi1990 on 2008-09-10
Ok, I fixed this using the Nvidia-settings app.  It just took a bit of tinkering to get all of the different settings right.

---

### Post by Sillywombat on 2008-09-16
> **malachi1990 said:**
> Ok, I fixed this using the Nvidia-settings app.  It just took a bit of tinkering to get all of the different settings right.

Hey, im currently having the same problem on a NVIDIA 6600.
And there doesnt seem to be any actual solutions listed here for this problem.
Could I ask you what "tinkering" you did? And now, if everything works, are you actually using twinview or xinerama with the Composite extension running?

---

### Post by overdrank on 2008-09-16
> **Sillywombat said:**
> Hey, im currently having the same problem on a NVIDIA 6600.
And there doesnt seem to be any actual solutions listed here for this problem.
Could I ask you what "tinkering" you did? And now, if everything works, are you actually using twinview or xinerama with the Composite extension running?

Hi and if the drivers are installed along with nvidia-settings what issues are you having? Have you tried compiz check? Are you able to get the dual screens working with twin view?

---

### Post by Sillywombat on 2008-09-16
> **overdrank said:**
> Hi and if the drivers are installed along with nvidia-settings what issues are you having? Have you tried compiz check? Are you able to get the dual screens working with twin view?

I currently have my own post open, but no one is answering :confused:
I did run a compiz check and it turned out that i didnt have my composite extension.

Here is the link to the thread:
[HTML]http://ubuntuforums.org/showthread.php?t=920684[/HTML]
Listed there is a compiz check script and a general check.
To answer your question, yes, I am currently running my dual desktop, but in Xinerama.

---

### Post by LOTM on 2008-10-17
Compiz and Xinarama don't seem to be able to co-exist. Once I disabled Xinarama, compiz started working.

---

