---
title: "xpilot-ng help"
date: 2008-10-02
forum: General Help
---

### Post by helpineed on 2008-10-02
when i start a game of xpilot-ng (installed form synaptic package manager) and connect to a server it works fine. but when i click on the screen or try to toggle mouse steer mode the program crashes (the window closes and the program stops). I ran the program in the terminal and when i clicked on the screen it spit out this.```
  Major opcode of failed request:  135 (XFree86-Misc)
  Minor opcode of failed request:  3 (XF86MiscGetMouseSettings)
  Value in failed request:  0x2e0017b
  Serial number of failed request:  544609
  Current serial number in output stream:  544609

```
please help

---

### Post by helpineed on 2008-10-04
hey i found out that you can just use bloodspilot for your client and keep the server.

---

### Post by Iridos on 2008-11-23
This looks like bug #272908  ( [https://bugs.launchpad.net/bugs/272908](https://bugs.launchpad.net/bugs/272908) ) - the author of this bug filed it just against hardy and claims it was fixed in intrepid. 

Please file a bug report against the package! (or clarify that it is not fixed in intrepid in the bug above).

The fix mentioned in the bug should work for you as well (disable the function that switches 3-button-emulation off for the duration of the game)

I.

PS. and yes, this bug does not exist in Debian, as the problem can be avoided via the build-dependencies as well.... I'm slightly miffed at how the package could have been released with an obvious bug like this - you'd think that the client of a game was at least tested for 10 seconds before releasing it (even if just on the most common i386 platform) - enough to click the mouse and find the bug...

---

