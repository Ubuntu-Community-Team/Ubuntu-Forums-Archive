---
title: "Bad firefox fonts vs good desktop fonts"
date: 2008-09-19
forum: General Help
---

### Post by melat0nin on 2008-09-19
Hi all

Today I installed Myriad, because it's a nice font.  I got my desktop looking really nice by using slight hinting.  The trouble is, this screws up firefox's fonts.

Here's an example:

[IMG]http://i36.tinypic.com/f22esl.png[/IMG]

As you can see the font on the applications menu, Computer window and Appearance windows is really nice and smooth.  However the firefox fonts are pretty horrible.

Here is the same setup with the fonts set to Full hinting:

[IMG]http://i37.tinypic.com/10qgrhw.png[/IMG]

Firefox looks good, but the desktop font looks rather clumsy compared to the above.

Is there any way around this?  Ideally I want firefox to look like the second pic and my desktop to look like the first.

Any suggestions much appreciated! :)

---

### Post by DagMan on 2008-09-19
This is what I use for firefox out of this gentoo wiki page [http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#Mozilla_Firefox_1.0.2B](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#Mozilla_Firefox_1.0.2B) none of the other suggestions had to be used from the wiki though I did pull in a crap load of fonts after I set up Ubuntu and installed a package.  I don't know what pulled them in as it was a long list of things I was installing though if I had to guess I'd say it was ubuntu-restricted-extras.  If you have the following fonts then it's not a worry.

Proportional: Serif (Size: 16)
Serif: Bitstream vera serif
Sans-serif: Bitstream vera sans
Monospace: Bitstream vera sans mono (Size: 12) 

I copied my .mozilla folder over when I migrated to Ubuntu but I think I remember that Ubuntu didn't use the above as default and does need to be changed for them to look their best.  My fonts look pretty good now.

---

### Post by melat0nin on 2008-09-20
> **DagMan said:**
> This is what I use for firefox out of this gentoo wiki page [http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#Mozilla_Firefox_1.0.2B](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#Mozilla_Firefox_1.0.2B) none of the other suggestions had to be used from the wiki though I did pull in a crap load of fonts after I set up Ubuntu and installed a package.  I don't know what pulled them in as it was a long list of things I was installing though if I had to guess I'd say it was ubuntu-restricted-extras.  If you have the following fonts then it's not a worry.

Proportional: Serif (Size: 16)
Serif: Bitstream vera serif
Sans-serif: Bitstream vera sans
Monospace: Bitstream vera sans mono (Size: 12) 

I copied my .mozilla folder over when I migrated to Ubuntu but I think I remember that Ubuntu didn't use the above as default and does need to be changed for them to look their best.  My fonts look pretty good now.

Thanks for the reply.  The problem is not the fonts I've chosen (I have the MS fonts installed and I prefer to use them because they are what most sites are designed with in mind).. it's just the actual *display* of the fonts.  Ideally I'd like to have independent control over FF's hinting, to make it "full" while the rest of the system is "slight".

Anyone know if this is possible? I really like the new look of the OS in general, but the MS fonts in FF look pretty horrible.

---

