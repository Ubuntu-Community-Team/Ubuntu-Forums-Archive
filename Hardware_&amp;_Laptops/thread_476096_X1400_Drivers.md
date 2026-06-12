---
title: "X1400 Drivers ???"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by ssmith335 on 2007-06-16
Hi Everyone,

Is it me or is the X1400 so new that there isn't much support for this video card? I've been tinkering with my Dell e1505 over the past week trying to get Beryl running under Ubuntu and this X1400 video card. I've been able to get the ATI drives loaded and running which is confirmed using the fglrxinfo command. 

However, in trying to get Beryl running (gone through the step by step instructions posted here earlier, Beryl attempts to run then resets back to "Metacity (Gnome Window Manager). In fact I've noted if I try to enable "Desktop effects" Ubuntu returns "The Composite extension is not available." Great, I edit my xorg.conf file and place "enable" under the appropriate "Section" and restart. After the restart I issue the fglrxinfo command again only to see the MESA drivers loaded. 

Anyone out there had any luck getting this same combination to work? Dell Inspiron E1505, ATI X1400, Ubuntu 64...

Many thanks,

~Steve

---

### Post by dustigroove on 2007-06-16
[FONT=Arial][SIZE=2][COLOR=Black]My T60 uses the ATI X1400 as well. [This guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") located on the beryl-project page is what helped me in getting Beryl up and running. Basically it boils down to using the beryl-core 0.2.0 package as the 0.2.1 version included in the repos doesn't include the proper xgl executable.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by ssmith335 on 2007-06-16
DustiGroove,

Thanks for the suggestion. I have followed and applied the procedure given in your link via another specific for the ATI cards found here and in your original link. [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

To no avail.

This is harder than it should be.

~Steve

---

### Post by neptho on 2007-06-16
Composite is not supported with the fglrx driver.  Beryl is annoying eyecandy, and the Xgl server is really awful with my X1300, so I just went back to Metacity.  Beryl is not stable, and it's even worse with ATI's drivers.  I'd strongly suggest you give up on it, and just get on with life for now.

---

### Post by ssmith335 on 2007-06-16
neptho,

Yup. I agree with you. I've gotten Ubuntu working almost flawlessly to this point and from what I've seen in Beryl "demos" its just a bunch of eye candy.

For now I'm happy to be running Ubuntu 64 with full functionality on my laptop.

Regards,

~Steve

---

### Post by dustigroove on 2007-06-16
[FONT=Arial][SIZE=2][COLOR=Black]Actually I have found Beryl to be quite a boon for me in the usability department. It allows me to have windows act the way I want them to (there are a number of features related to window management; smart arrangement, custom arrangement, grouping, etc).

And although figuring out the right dance to do to make it all work was a bit of a pain on my laptop (my desktop machine was a breeze), I honestly couldn't see ever going back to not using it.

[/COLOR][/SIZE][/FONT]

---

### Post by ssmith335 on 2007-06-16
Well it would be nice to get it running so I have the option of using it or not.

Hopefully in time the x1400 will have better support and Beryl will become stable.

~Steve

---

