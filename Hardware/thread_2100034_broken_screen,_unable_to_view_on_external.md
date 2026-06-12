---
title: "broken screen, unable to view on external"
date: 2012-12-31
forum: Hardware
---

### Post by milkythebrowncow on 2012-12-31
Hi, not entirely sure this goes in this section of the forum, I'll move it if not. 

OK so here's the scoop, my hp computer is toast, irrelevant, but my sister gave me her old dell studio 1737.  The lcd is shattered, and she has taken the hard drive out.  I put the hard drive from my old laptop in, with ubuntu (i believe Natty) as the only OS.  I hook up my external screen, and boot.  Using the fn keys, I can see the bios screen and GRUB.  I can see Ubuntu load, all the way up to the login screen, but then the external cuts out before the login screen shows.  The fn keys no longer allow me to use the external to view the login screen.  I'm pretty confident that if i can get past the login screen, the fn keys would work again.  Does anyone know a way around this?  Can anyone confirm that hitting fn f5 at the login screen does not port the video over to the external? At an impasse here, can't even put the hard drive into another computer to change the settings because the hard drive has those weird interlacing connectors that dont allow me to hook it up to a cable (i think its still sata) - barring this fix, does anyone know what kind of connection this is for the hard drive? I've spent the morning googling it to try to find an adapter to hook my hd up to my desktop, but i cant even find mention of this type of sata hook up.  It just slides down onto the connectors, again designed in such a way that i can't hook the normal SATA cables up to it, but i do believe its SATA the pins are in the same position and size for power and data. 

Thanks a ton, sorry this was long-winded.  I've seen other posts about broken screens, they say to use the fn keys or consult the manual.  For windows OSs, apparently I could boot into safe mode and it would keep the external monitor showing the whole way, but such is not the case here i suppose
Thanks again!:popcorn:

---

### Post by sudodus on 2012-12-31
Welcome to the Ubuntu Forums :-)

So you are running Ubuntu Natty (11.04). Do you remember if you have installed any proprietary driver for the graphics chip or the wifi chip? If so, it may create problems running in another computer.

With the default built-in drivers, you should be able to boot your system in most computers, where you can connect the drive.

So one way to rescue the data on your drive might be to borrow another computer, download a current version of Lubuntu, Xubuntu, Ubuntu or Kubuntu (with the most light-weight flavour first and the most heavy-weight and fancy flavour last). I suggest 12.04 LTS. Make a boot CD/DVD/USB drive from the iso file, boot from that and you should be able to access your internal drive and its data.

If no luck within the Ubuntu flavours, try Knoppix. It is very good at recognizing and running various hardware, also old hardware.

---

### Post by ahallubuntu on 2012-12-31
Some Dell laptops are set so you don't use Fn + function key, you just hit the function key.  (You can probably change that behavior in BIOS Setup.)  Have you tried that, using the function key instead of just Fn + function key?

Sometimes in BIOS Setup there are options for multiple screens, too.  Use F2 to get into BIOS Setup on a Dell.

You can get a replacement screen for it for about $80 USD shipped off eBay in the US.  I've replaced more than one Dell screen.  It's not terribly hard most of the time.  Lots of tutorials on YouTube.

> **milkythebrowncow said:**
> Hi, not entirely sure this goes in this section of the forum, I'll move it if not. 

OK so here's the scoop, my hp computer is toast, irrelevant, but my sister gave me her old dell studio 1737.  The lcd is shattered, and she has taken the hard drive out.  I put the hard drive from my old laptop in, with ubuntu (i believe Natty) as the only OS.  I hook up my external screen, and boot.  Using the fn keys, I can see the bios screen and GRUB.  I can see Ubuntu load, all the way up to the login screen, but then the external cuts out before the login screen shows.  The fn keys no longer allow me to use the external to view the login screen.  I'm pretty confident that if i can get past the login screen, the fn keys would work again.  Does anyone know a way around this?  Can anyone confirm that hitting fn f5 at the login screen does not port the video over to the external? At an impasse here, can't even put the hard drive into another computer to change the settings because the hard drive has those weird interlacing connectors that dont allow me to hook it up to a cable (i think its still sata) - barring this fix, does anyone know what kind of connection this is for the hard drive? I've spent the morning googling it to try to find an adapter to hook my hd up to my desktop, but i cant even find mention of this type of sata hook up.  It just slides down onto the connectors, again designed in such a way that i can't hook the normal SATA cables up to it, but i do believe its SATA the pins are in the same position and size for power and data. 

Thanks a ton, sorry this was long-winded.  I've seen other posts about broken screens, they say to use the fn keys or consult the manual.  For windows OSs, apparently I could boot into safe mode and it would keep the external monitor showing the whole way, but such is not the case here i suppose
Thanks again!:popcorn:

---

