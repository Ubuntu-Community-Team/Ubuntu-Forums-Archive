---
title: "DellMedia Button"
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by Mr Fat Bat on 2006-05-15
Hi Guys,

I have a great working Dapper install on a Dell Inspiron 6400.  Like most of the new Dell laptops it comes with the "Dell Media Experience" Software that **nobody in there right mind** would ever use ;) 

When only XP is installed on the laptop and the laptop is off the "MediaDirect" button on the laptop launches the Media Experience software.  But when GRUB is installed the MediaDirect button tries to start the Media Experience software but just ends up in GRUB.

Okay my question:  Does anybody know how to alter what the "MediaDirect" button starts when the laptop is off?  Also does anybody have any cool ideas or suggestions for when the button is pushed?  I don't care how wacky or silly it sounds :p because at the moment I have a perfectly good button sitting on my laptop being boring and useless!

---

### Post by mimp on 2006-05-18
Theres a long post about exactly how this works over at [http://www.notebookforums.com/](http://www.notebookforums.com/) although i've not had the time to read all of it yet so i can't offer much advice. 

Basically mediadirect lives on a partition the bios hides from you, so you can't get rid of it even with pre-os partitioning software like boot magic or RPM, however if you do anything that alters the MBR it screws up the loading process, so you can't ever get to it. This is fixable but like i said i've not bothered reading how yet. Would be nice if someone hacked a way to configure it - I've got a different kernel compiled for audio work for instance, would be ace to boot straight to that with the media button or go to my regular ubuntu with the normal on switch..

---

### Post by Mr Fat Bat on 2006-05-18
Cheers,

i'll have a looksy when my other [issue]("http://ubuntuforums.org/showthread.php?t=178545") is solved ;)

---

