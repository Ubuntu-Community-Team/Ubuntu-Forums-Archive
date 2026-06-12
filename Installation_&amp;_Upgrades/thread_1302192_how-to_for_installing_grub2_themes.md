---
title: "how-to for installing grub2 themes?"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by vav on 2009-10-26
How could I install these?
[http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes)
My grub2 currently shows up with a nice background but not a nice menu!

---

### Post by cchester on 2009-10-26
> **vav said:**
> How could I install these?
[http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes)
My grub2 currently shows up with a nice background but not a nice menu!

Here you go. This is what I found.

# Grub 2 Splash Images
Why reinvent the wheel? Visit this site for an excellent presentation on creating Grub 2 images:
[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html)

However, if encrypted disks are not an issue, here are the basics:

    * Manually copy grub splash images into the /usr/share/images/grub folder or install the default grub2 splash images via Synaptic or:
      Code:

      sudo apt-get install grub2-splashimages

    * The grub2's splash images are controlled by /etc/grub.d/05_debian_theme. Open this file for editing:
      Code:

      gksudo gedit /etc/grub.d/05_debian_theme

      Find the following line and edit the highlighted area, replacing it with the grub splash image you wish to use (and located in /usr/share/images/grub):
      Quote:
      for i in {/boot/grub,/usr/share/images/grub}/moreblue-orbit-grub.{png,tga} ; do
      Note: There is a period ( . ) following the filename.
          o At one point Grub 2 splash images were downloaded and stored in /usr/share/images/desktop.base If this is where your grub images are stored, change the address in the previous command accordingly ( ... /usr/share/images/desktop-base} ... ).
    * Save the file, then update grub2:
      Code:

      sudo update-grub2

---

### Post by vav on 2009-10-27
I've done that part! Thats why it shows with a background. I wanted the nicer menu, which I think requires more extensive changes.

---

