---
title: "Drive Letters"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by Gtaylor on 2005-03-29
For some reason, my Inspiron 5150 (and a few Desktops I've seen) insist on setting hda as the cdrom drive. This is fine until you want to install some things with GUI installers (ut2004, Vega Strike, etc.) These get confused and assume you want to install to hda so it yanks the free space from there instead of your actual hard drives. So I get errors saying I don't have enough space to install.

Is there any way I can re-letter my cdrom (hda) to hdc and my hard drive (hdc) to hda? It's a real pain and it doesn't make sense!

---

### Post by mercurus on 2005-03-29
Curious ... I would have thought that installers would use the information provided by mount, rather than dig for it themselves ... You should be presented with the option of which partition you would like to install the software, or rather where abouts in the filesystem. eg. /opt or /usr/local rather than on which drive ... Is there nothing in the installer documentation that would suggest an argument you could pass the installer to MAKE it use /usr/local or /opt or /dev/hdc1 ?

Either way, I do have a suggestion. How are your drives configured physically ? If your optical drive is attached to the Primary Master IDE controller, then it will be /dev/hda. If you switch your IDE cables at the motherboard you should see the optical drive go to /dev/hdc and your HDD become /dev/hda ... Only do this if you're confident with manipulating hardware - and remember to turn the machine OFF first.

Cheers
mercurus

---

### Post by Gtaylor on 2005-03-29
[QUOTE=mercurus]Curious ... I would have thought that installers would use the information provided by mount, rather than dig for it themselves ... You should be presented with the option of which partition you would like to install the software, or rather where abouts in the filesystem. eg. /opt or /usr/local rather than on which drive ... Is there nothing in the installer documentation that would suggest an argument you could pass the installer to MAKE it use /usr/local or /opt or /dev/hdc1 ?[/quote]
There is an option to specify where to install, it just doesn't appear to work right. Installing to anywhere but /home results in it thinking I only have a gig free whereas I just 24 gig free since it's one big partition that encompasses the root dir and everything else.

[QUOTE=mercurus]
Either way, I do have a suggestion. How are your drives configured physically ? If your optical drive is attached to the Primary Master IDE controller, then it will be /dev/hda. If you switch your IDE cables at the motherboard you should see the optical drive go to /dev/hdc and your HDD become /dev/hda ... Only do this if you're confident with manipulating hardware - and remember to turn the machine OFF first.
[/QUOTE]
Yeah, that'd be the best thing to do but this is a laptop and I'm not too eager to crack it open and change things around. Is this the only option to fix the lettering?

---

