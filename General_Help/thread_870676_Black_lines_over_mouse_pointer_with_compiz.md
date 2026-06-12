---
title: "Black lines over mouse pointer with compiz"
date: 2008-07-26
forum: General Help
---

### Post by mlilien on 2008-07-26
Hi, I've had a problem since updating to Hardy that my mouse will get several black lines across it frequently.  This only seems to happen with the arrow cursor, and if I get it to change to the text cursor or something and then change back, it sometimes fixes itself.  I've been checking the forums occasionally to see if anyone else has this problem, but hadn't found much.

I found this thread [http://ubuntuforums.org/showthread.php?t=594038&highlight=ati+compiz+cursor&page=2](http://ubuntuforums.org/showthread.php?t=594038&highlight=ati+compiz+cursor&page=2), where someone else seems to have the same problem (last post), but couldn't respond to it since it's in the archive.

I'm using a Lenovo t60p with an ati firegl 5250 graphics card.

Anyone else having a similar problem or know of a solution?

Thanks

---

### Post by Saint Angeles on 2008-07-26
sounds like a little glitch with the driver... which driver are you using?

---

### Post by mlilien on 2008-07-26
I'm using the latest version of the xorg-driver-fglrx found in synaptic.  Aside from this problem with the cursor, which seems to be completely aesthetic, compiz is running fine.

---

### Post by nandaiyo on 2008-08-07
I had this exact problem and found a solution for my Thinkpad T60p. I'm not sure if this will solve your issue, but possibly, if you are using an ATI card and fglrx. Here's what I did:

- I followed steps 1-4 on [Forlong's Blog (old)](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support) - I DID NOT REBOOT
- Went to Ati.com and click on support & drivers -> download graphic drivers
- I picked linux x86 -> FireGL -> FireGL V5200 for my thinkpad T60p's ATI card
- downloaded the (.run) file to my desktop
- opened a terminal session and went to my desktop 
- typed: > sudo bash ./ati-driver-installer and hit TAB to finish the filename (mine may be different than yours)
- followed the instructions (automatic install), and rebooted after.

Everything seems to be working just fine.

---

### Post by mlilien on 2008-08-07
Awesome.  That worked like a dream.  I've been trying to figure out how to get rid of those stupid black lines since Hardy came out.  Thank you.

So, is this driver going to come built into Intrepid?

---

### Post by mlilien on 2008-08-08
Slight problem.  This seems to have killed my video playback.  Kaffeine has audio, but no video and movie player just crashes.  I'm gonna look into it more in the morning, but in the meantime, did you have this problem when you started using these drivers?  How'd you fix it?

Thanks

---

### Post by XanTrax on 2008-08-08
This seemed like it would work but it didnt.  It got rid of those lines but now when I try to enable compiz it makes my entire screen a whiteish/yellow (kind of eggish) and wont start.  I have to reboot gnome to have it work again.  It fails and does the same thing no matter what I do

sudo compiz --replace

or 

Appearance -> Desktop Effects -> Enable (one of the two)

It just goes to that blank screen and doesnt go anywhere from there.

Any ideas?


EDIT:

New problem now.  I uninstalled it and reinstalled it and then now it goes:

> 
eax@kozler:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0


hm?

---

### Post by Andross707 on 2008-08-22
I've yet to find any solution to this yet....other than just ignoring it I guess.

> **mlilien said:**
> Hi, I've had a problem since updating to Hardy that my mouse will get several black lines across it frequently.  This only seems to happen with the arrow cursor, and if I get it to change to the text cursor or something and then change back, it sometimes fixes itself.  I've been checking the forums occasionally to see if anyone else has this problem, but hadn't found much.

I found this thread [http://ubuntuforums.org/showthread.php?t=594038&highlight=ati+compiz+cursor&page=2](http://ubuntuforums.org/showthread.php?t=594038&highlight=ati+compiz+cursor&page=2), where someone else seems to have the same problem (last post), but couldn't respond to it since it's in the archive.

I'm using a Lenovo t60p with an ati firegl 5250 graphics card.

Anyone else having a similar problem or know of a solution?

Thanks

---

### Post by Woodsyx on 2008-10-03
Just posting this for other people that are having this problem it works 100% to fix those annoying black bars. You can also make them go away if you disable visual effects but who wants that.

---

### Post by Andross707 on 2008-10-03
Is there a fix?

---

### Post by dchky on 2008-10-03
One thing that might work:

Edit your xorg.conf file /etc/X11/xorg.conf

In the "Device" section add the following line:
Options   "HWCursor"  "true"

Restart X (ctrl + alt + backspace a couple of times)

You should have no more pointer artifacts.

---

