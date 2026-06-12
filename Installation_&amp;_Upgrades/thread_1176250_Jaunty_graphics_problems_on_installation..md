---
title: "Jaunty graphics problems on installation."
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-06-02
Hi, I recently tried to upgrade from 8.10 to 9.04 via the update manager, and could never successfully boot into Ubuntu afterward, due to a graphics problem. Turning off quiet/splash screen made no difference, I still saw the problem.

So I reinstalled 9.04 from scratch (keeping /home intact, on a separate partition), formatting /. Afterward I was able to boot into Ubuntu. But my Radeon HD 3870 X2 needed a proprietary driver and when I activated it, upon restarting I saw a very similar graphics problem to what I saw when I upgraded. I will attempt to show the problem below (sorry for the crappy cell phone picture):

[IMG]http://nixiepixel.com/misc/deadjaunty.jpg[/IMG]

Any ideas what this is and/or how I can fix it?

Thanks!

---

### Post by Nixie Pixel on 2009-06-02
Resolved, thanks to [this excellent post]("http://ubuntuforums.org/showpost.php?p=7349505&postcount=240").

---

### Post by neo.patrix on 2009-06-02
I have ATI X1300 and I have not upgraded to Jaunty yet , because new version of X.Org has certain support problems with AMD/ATI proprietary drivers. I like using proprietary driver for compiz 3D desktop. 

If you want to use compiz 3D effects , it is best to stick with Intrepid for now and use ATI proprietary driver from restricted. The anti-aliasing,  sometimes font-quality and usually bad pictures from websites when they are not viewed with their normal size are problems but still you can get your 3D desktop up and running. 

I far as black screen is concerned , I had same kind of problem upgrading from 7.10 to 8.04, all that I could do was ignore Ubuntu for a while made fresh install with 8.10 when I needed it again. You can try some magic commands from posts, forums, blogs, in my experience nothing really gets it back up other than reinstall when you have ATI driver problems.

---

