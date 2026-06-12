---
title: "Vista To XP"
date: 2008-10-07
forum: General Help
---

### Post by metalmaniac248 on 2008-10-07
i currently dual boot vista with ubuntu hardy

vista was the OS that came pre installed on my computer,

however the laptop is just not good enough to run vista, (which is why i switched to Ubuntu :) )


as i only use vista for itunes, i would like to replace vista with XP as it would be faster,


could anyone advise me as to how to do this



thanks

---

### Post by scouser73 on 2008-10-07
The way I would do it would be to visit this website; [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/") and download it.

Then visit this website; [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html"). That way you have all stuff you have downloaded from the repositories on a CD/DVD to install.

Once you have burned that to disc, you should install Remastersys, which creates an ISO of your current Ubuntu installation & burn it to CD/DVD.

Install XP, get it set up, then install the Remastersys ISO you have made, once that is done then install the APT CD.

I solely use Ubuntu, and this morning it took me twenty minutes to set everything up, I was actually surprised that I didn't have to set up any email account settings, or bittorrent settings either. The whole thing just works.  What is also good with Apt-on-CD is that you can choose bits you want to install, and what you want to leave out.

---

### Post by mixmaster on 2008-10-07
You are going to need an XP installation disk to do this.  If you have such a beast (and the relevant activation code) why not install XP in Virtualbox (which is pretty painless) and just delete the Vista partition.  That way you can boot Ubuntu and run your itunes stuff in the virtualbox without the hastle of dual boot.

Caveat: I've run a number of apps with no problems in virtualbox but I've never used itunes.

---

### Post by hyper_ch on 2008-10-07
you could also try to run itunes through wine or in a virtual windows by virtualbox or vmware...

---

### Post by metalmaniac248 on 2008-10-07
thanks for the replies


i have tried to set up a virtual machine before,

using both vmware player and inotek virtual box


it has never worked for me

very anoying!!

---

### Post by ibuclaw on 2008-10-07
If you have the proper Microsoft CDs and License Keys, and you have every reason to do so, then I suppose there will be no reason as to why not.

As for wrapping everything together if you decide to go ahead, restoring grub is simple.

Just boot into the Ubuntu LiveCD and run "sudo grub" in a terminal.
documentation is here: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

Or if the terminal isn't for you, there is a bash script called "restoregrub" in the [KiwiLinux Repository]("http://kiwilinux.org/archive/pool/main/r/restoregrub/").

If you keep everything in thesame partition layout, then you shouldn't need to edit the grub menu.lst file either.

Regards
Iain

---

