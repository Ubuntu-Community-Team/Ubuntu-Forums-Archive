---
title: "Speed of X windows, other system tweaks help"
date: 2008-10-01
forum: General Help
---

### Post by gus_393 on 2008-10-01
Hi all,

I use alot of scientific computation apps. Generally I want to sqeeze as much "responsive-ness" as I can out of my system, but I dont know enough to do tweak every single file by hand.

I was just wondering if there are any utilities/suggestions you guys might have for how I can do some tweaks. In particular, I`ve noticed that applications like Matlab (java and x-windows I believe) can be quite sluggish compared to their windows counter-parts. Is there any way I can speed up the x windows environment? I uninstalled the included compiz and I have no desktop effects. I think I`m running "metacity", is there something more minimal than that?

I`ve tried cutting out some services and such, but I really would like to hear some advice on this general subject. Maybe someone has a script/package they've put together for this kind of purpose?

---

### Post by phidia on 2008-10-01
There is a howto [here]("http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html") on various tweaks for Ubuntu.

It covers several of the things you're looking for.

---

### Post by gus_393 on 2008-10-02
thanks. I was hoping there was more I can do to address the lag I`m getting. I still love Ubuntu though.

Thanks for the link

---

### Post by tacutu on 2008-10-02
install openbox. Then, at the login screen select as your session "gnome/openbox". It's still gnome, but way faster, without the overhead of metacity.

Another thing you might want to do is to replace nautilus (the file manager) with pcmanfm, which doesn't look as polished but has more functionality and takes less resources. Read the thread here:
[http://ubuntuforums.org/showthread.php?t=692238](http://ubuntuforums.org/showthread.php?t=692238)

Edit: if you decide to go for pcmanfm, I would recommend you don't install the version in the repos (too old) but get the latest deb from [http://pcmanfm.sourceforge.net/download.html](http://pcmanfm.sourceforge.net/download.html)

---

