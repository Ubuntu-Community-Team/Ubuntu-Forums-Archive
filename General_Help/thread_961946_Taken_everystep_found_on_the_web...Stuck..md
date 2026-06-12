---
title: "Taken everystep found on the web...Stuck."
date: 2008-10-28
forum: General Help
---

### Post by brightJoker on 2008-10-28
Hey so currently whenever I try to enable my Desktop Effects via System>Administration>Appearance, I get the "Could not enable desktop effects." Message.  I have run compiz-check, everything works.  I am running a Toshiba Satellite, however it seems that the computer can not recognize my video card, which may be the problem.  Unfortunately, I do not remember which video card is in this laptop.  I also just upgraded to 8.10 and that has seemed to throw off Compiz.  I can enter compiz --replace and emerald --replace, but when I logoff or shutdown, it does not restart with the effects enabled and I have to go through terminal and reconfigure Compiz each time.  I tried adding Compiz and Emerald to sessions, but that does not seem to work.  I appreciate any help given.

---

### Post by drelyn86 on 2008-10-28
Copied from [http://www.ubuntu.com/testing/intrepid/beta#X.Org%207.4]("http://www.ubuntu.com/testing/intrepid/beta#X.Org%207.4")
> X.Org 7.4, the latest stable version of X.Org, is available in Intrepid. This release brings much better support for hot-pluggable input devices such as tablets, keyboards, and mice. At the same time this will allow the great majority of users to run without a /etc/X11/xorg.conf file. A new failsafe X is introduced, to give better tools for troubleshooting X startup failures.

The fglrx and two of the older nvidia binary drivers are not available for X.Org 7.4 yet, so users of these drivers will be automatically switched to the corresponding open source drivers. 

---

### Post by brightJoker on 2008-10-29
Well see I upgraded to Intrepid using update-manager -d, and right before that I had just gotten my Ubuntu to working the best I believe it could, and now the only problem is my desktop effects cannot be enabled.  I also have noticed that it seems it can not detect my video card.  Another thing to note, on boot after GRUB loads, a screen pops up asking to choose the correct video settings, noting at the top that the current config. is not recognized.  I then can press "enter" to choose the correct display or "space" to continue.  When I choose any of them, the splash screen looks distorted, when I press "space" it looks normal.  Is that a link to download the new Xorg that I don't have?  Please any help with this would be awesome, I love linux and Ubuntu and was about to repackage my settings as a Ubuntu distro for my friends using Vista for Christmas and would be really awesome to get this fixed ASAP!!! Thank you! And LOVE Ubuntu, best new-linux user experience there is.  I have had experience with other distros, but this one has just blown me away at simplicity and performance.  Thank you!

EDIT: Really could use help, I have corrected the video card issue and I honestly have no idea what is wrong at this point.  I am very experienced with Linux and I have taken every step I know to try and correct this problem.  Any suggestions or someone willing to work with me would be great.

---

### Post by brightJoker on 2008-10-29
*bump*

---

### Post by drelyn86 on 2008-10-29
> **brightJoker said:**
> Is that a link to download the new Xorg that I don't have? 

You have the new Xorg - it's included in Intrepid, and yes, that's the problem. The hardware drivers do not yet support it. 

I've had to deal with this same problem in Fedora9 before... some people managed to roll back to the older version of Xorg, but that gets way too complicated. 

IMHO, you should stick with Ubuntu Hardy for now.

---

