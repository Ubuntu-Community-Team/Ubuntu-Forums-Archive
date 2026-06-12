---
title: "New ATI driverse"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by lean on 2004-11-11
In november new ATI drivers has been released. Specifically in this version Doom3 works (and propably also Savage).
Will these drivers be incorporated in Warty? Will they be incorporoted in the unstable? And the last question is... When?

---

### Post by daniels on 2004-11-11
[QUOTE=lean]In november new ATI drivers has been released. Specifically in this version Doom3 works (and propably also Savage).
Will these drivers be incorporated in Warty? Will they be incorporoted in the unstable? And the last question is... When?[/QUOTE]Absolutely not in Warty.  Probably in Hoary.  Don't know when.

---

### Post by HungSquirrel on 2004-11-11
The real question is will these drivers fully support kernel 2.6, XF86 4.3 *and* 4.4, and xorg?

Knowing ATI, choose two.

---

### Post by daniels on 2004-11-11
[QUOTE=HungSquirrel]The real question is will these drivers fully support kernel 2.6, XF86 4.3 *and* 4.4, and xorg?

Knowing ATI, choose two.[/QUOTE]The first three, actually.  And X11R6.7.  But not 6.8.

---

### Post by emperor on 2004-11-12
[b]From the ATI chat on [http://www.rage3d.com]("http://www.rage3d.com") yesterday:
    
 Summary: Next Release in December, features close to Windows Driver and should get better, support Xorg 6.8, and AMD 64 platform. Xorg composite extensions will not be supported in the next release!
    
    [/b]**Q**: GLSL has been in the Windows CATALYST OpenGL for about a year now, while it is currently abscent in the Linux OpenGL implementation. This suggests to me that the two do not share the same codebase. Are there plans to take a more unified approach so that developers can gain access to new OpenGL improvements and extensions at roughly 
     the same time for either platform?
     
     **A**: [i]**Since 3.9, the code has been tracking the windows codebase for each release. In upcoming releases we will match the Windows version number (December will be a 8.08 release**. A feature disparity may in some cases (GLSL for example) may be absent since the code is not stabilised or there are technology restrictions for Linux. As we have opportunity we will bring features on par with windows.
 
 [/i]    **Q**: Back in Mid-August, 2004, at [http://freedesktop.org/bugzilla/show_bug.cgi?id=1085#c4]("http://freedesktop.org/bugzilla/show_bug.cgi?id=1085#c4") , Ati stated that they would be re-releasing driver 3.12 with X.org 6.8 support in a few weeks. What is the status on this re-release? 
     
     **A**: [i]That was a leak from beta program mailing list... It was 'planning' and not a definite statement. (I didn't say it, Stefan from SuSE did). We had other important things to work with that delayed that work. ATI did not state... Stefan did. [b]Anyway, 6.8 is going to be in the next release.
  [/b]   
    [/i]**Q**: AMD64 users are generally forced to use cards from a competitor to have decent 3D support on 64-bit Linux systems. Are there any (at least) beta drivers for AMD64 Linux, and if so, are there plans on making them public as the Windows beta drivers?
     
     **A**: [i]**We are planning our first release of AMD64 with the next release.**
    
    [/i]**Q**: Given ATI's business focus, The priority seems to be on 2d performance and functionality. Does ATI have any plans to support new desktop developments such as the X.org Composite extention?
     
     **A**: *As the technology becomes deployed in the market, we will respond to what is needed. Currently there is minimal requirements for Composite and so on, until some fundamental architectural changes are made.*

---

