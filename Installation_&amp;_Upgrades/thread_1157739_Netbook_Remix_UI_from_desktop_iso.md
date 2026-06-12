---
title: "Netbook Remix UI from desktop iso"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by kylehase on 2009-05-13
I have an older Dell Latitude X300 with a 1.2GHz PentiumM and 12" screen.  It's about the same specs as a netbook and I think the Nebook Remix UI would be perfect for this laptop.

I've tried and failed to install UNR from the USB image.  It just says "boot error".  It's probably not a good idea anyway since UNR is customized for netbook hardware (Atom etc.)  

My question is, **is it possible to install the UNR 9.04 UI after installing Jaunty from the desktop ISO image?**  Some people were [_[COLOR="DarkRed"]doing this with Hardy[/COLOR]_]("http://markusthielmann.com/blog/installing_ubuntu_netbook_remix_ubuntu_hardy_804") but that was before UNR was officially released. Also, I can't seem to find any Jaunty netbook remix packages on Launchpad.

---

### Post by logos34 on 2009-05-13
look through this page:

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by kylehase on 2009-05-13
Yep, went through that but it only describes Jaunty UNR installation using the USB image.  

There's also [[COLOR="DarkRed"]_this section_[/COLOR]]("https://wiki.ubuntu.com/UNR#The%20Hard%20(not-recommended)%20Way") where it says:
[LIST]
[*]harder and not recommended 
[*]most packages are now out of date
[/LIST]
And despite saying "*Packages are available for 8.04 (hardy), 8.10 (intrepid) and 9.04 (jaunty, in main)*" packages for Jaunty are not available.

---

### Post by Partyboi2 on 2009-05-13
> **kylehase said:**
> 
My question is, **is it possible to install the UNR 9.04 UI after installing Jaunty from the desktop ISO image?**  Some people were [_[COLOR=DarkRed]doing this with Hardy[/COLOR]_]("http://markusthielmann.com/blog/installing_ubuntu_netbook_remix_ubuntu_hardy_804") but that was before UNR was officially released. Also, I can't seem to find any Jaunty netbook remix packages on Launchpad. Hi, have a look at
[https://launchpad.net/~netbook-remix-team/+archive/ppa]("https://launchpad.net/%7Enetbook-remix-team/+archive/ppa")
You should be able to add the above repo and install the packages with
```
sudo apt-get install go-home-applet human-netbook-theme maximus ume-launcher window-picker-applet
```

---

### Post by Brandon Williams on 2009-05-13
First, the UNR image is i386, not lpia. I don't know why they decided to do that ... probably because i386 works just fine on lpia but not vice versa.

If you install Jaunty from the standard i386 ISO, simply 'sudo aptitude install ubuntu-netbook-remix' after the installation is complete and you now have UNR installed. 

Be sure to check the 'Known Jaunty bugs' thread in the 'General Help' forum before switching to the UNR interface, since there is a known bug with the desktop-switcher utility that you should work around before using it to switch to the UNR UI.

---

### Post by kylehase on 2009-05-13
@Partyboi2 I tried your suggestion and found that ume-launcher is not available but netbook-launcher is.  I also think the packages came from one of the standard repositories and not the launchpad one.

@Brandon Williams After having tried Partyboi2's suggestion, I think you're right. I'll be reistalling from scratch and trying your suggestion when I get home. Thanks.

---

### Post by kylehase on 2009-05-14
@Brandon Williams _[Your suggestion]("http://ubuntuforums.org/showthread.php?p=7280328#5")_ worked like a charm.  After installing Jaunty from the ISO and running a standard update I was able to install ubuntu-netbook-remix which includes all the necessary packages and settings.

Unfortunately after installation I found that my mouse became misaligned somehow.  The pointer would be over the Firefox icon but the Evolution icon would be selected but that's a problem for another thread.

Thanks

---

