---
title: "Matrox Triplhead2Go + Macbook Pro (4 years old)"
date: 2012-04-29
forum: Hardware
---

### Post by tbone3421 on 2012-04-29
Hi Everyone,

I've searched and read these forums for HowTo's on setting up external monitors, but I'm still having a very hard time getting my set up to configure correctly. It ALMOST works, but maybe someone can tell me what I'm doing wrong.  I am on the new 12.04 LTS in Ubuntu 2D, but I don't believe the problem is with the OS, its probably my config files.  The hardware is:  

MacbookPro with Nvidia GeForce 8600M GT  (this is the factory set up from Apple about 4 years ago)
Matrox Triplehead2Go
TWO LG monitors, each 1920x1080.

I know the Triplehead2Go can support three monitors, but I only have two right now.  

Currently the problem is almost solved, I have two X screens, both in Twinview in Nvidias X server settings.  X Screen 0 is 3840x1080 and X Screen 1 is 1440x900.  The two external monitors share one large desktop, and I would like for them to have their own desktops.  That way when I maximize a window, it won't split across both monitors.  

Can anyone suggest how to do this?  Also, I'm happy to post a config file if that helps.  
Thank you all very much for your help in past questions and this one too.

Thomas

---

### Post by tbone3421 on 2012-05-01
After reading several other posts about this, it really seems to boil down to being able to trick a single X screen into pretending there are three monitors.  Recall I am in Twinview, so that NVIDIA believes there are two monitors, and each has its own background and panel up top. 

I have changed my set up so that there is only one X screen and I am in Twinview, and I'm hoping to use RandR to try to configure the larger monitor (the Matrox output, which is really two monitors) into somehow pretending to be two monitors.  Sorry if that is really confusing.

Any help at all is greatly appreciated.

Thomas

---

### Post by BicyclerBoy on 2012-05-01
Don't use twinview..
Separate X screens will give you separate desktop on each screen.

Fake xinerama (AFAIK) can be used to split a large screen or twinview into separate screens.
This could have a serious impact on openGL performance..

---

### Post by BicyclerBoy on 2012-05-01
Don't use twinview..
Separate X screens will give you separate desktop on each screen.

Fake xinerama (AFAIK) can be used to split a large screen or twinview into separate screens.
This could have a serious impact on openGL performance..
The Xorg xinerama extension impacts openGL badly..

I don't see fake xinerama allowing a per-screen setup..

Xmonad looks to support per X screen config..

I would suggest separate X screens (need save & reboot) & then try xmonad.

---

