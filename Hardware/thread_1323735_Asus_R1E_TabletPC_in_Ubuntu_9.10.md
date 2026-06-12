---
title: "Asus R1E TabletPC in Ubuntu 9.10"
date: 2009-11-12
forum: Hardware
---

### Post by standarshy on 2009-11-12
Hi y'all.


I have looked through a few posts but couldn't manage to get this working on my own. I saw some posts about older versions of Ubuntu but wasn't sure if it still applied.

I am using an Asus R1E-D1 which I hear uses the wacom drivers through usb (instead of serial).

I wanted to try to livecd out first to make sure the tablet function worked before going through the install.  (I don't know if this is the problem.)

I know that my tabletpc device is being recognised because [http://pastebin.ca/1667571](http://pastebin.ca/1667571) is the part of the output I get when typing "xinput --list".


Any suggestions would be appreciated.  I'd be glad to provide more info if I left any details out.

Thanks,
Standarshy

---

### Post by Favux on 2009-11-12
Hi standarshy,

I'm pretty sure we've gotten some other Asus R1E & Asus R1F's using the modified .fdi I'm linking you to.  I forget, do you have touch too.  Anyway see gali98's [HOW TO]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").

I think all you need is the .fdi in "Section 2: Creating the Fdi File".  You can do as much of the rest of it as you want/need or you could probably just set up wacomcpl.  Oops, just noticed my HOW TO got butchered in an update.  Darn.

---

### Post by standarshy on 2009-11-12
The R1E and R1F do not have the touch screen.  Thanks for the advice.  I will try when I find some more time.

---

### Post by Favux on 2009-11-12
Hi standarshy,

OK, then you can remove the touch section of the .fdi if you want.

Anyway as I was saying you could then setup wacomcpl using "Section 3: Calibrating your Tablet PC" on this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by standarshy on 2009-11-16
I am getting confused at this part:

Start with this as a reference.
Code:

sudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

If you are on Karmic, use: (delete the contents)
Code:

sudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

Copy and paste the above contents then save.


>>It's telling me to delete the contents of what exactly? because it previously states to delete the contents.

---

### Post by Favux on 2009-11-16
Hi standarshy,

Gali98 is saying replace the contents of the default 10-linuxwacom.fdi with the new modified .fdi he shows you, but still call it 10-linuxwacom.fdi.

---

### Post by standarshy on 2009-11-17
I thought the one he was showing me was the default, he says "First as a reference I will include a default fdi File:"



> **Favux said:**
> Hi standarshy,

Gali98 is saying replace the contents of the default 10-linuxwacom.fdi with the new modified .fdi he shows you, but still call it 10-linuxwacom.fdi.

---

### Post by Favux on 2009-11-17
Hi standarshy,

I believe from context, he means he is showing you the default modified .fdi, as below it he shows one with options specific to his TX2000.  So back up the .fdi installed by the Karmic linuxwacom 0.8.4-1 packages and replace it with "default" modified 10-linuxwacom.fdi.  And if you want, you can remove the touch section.

---

