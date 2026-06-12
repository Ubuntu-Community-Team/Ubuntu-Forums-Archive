---
title: "Repairing my broken system...."
date: 2008-09-26
forum: General Help
---

### Post by rossco on 2008-09-26
Hey guys,

I just wrecked my Ubuntu system...  Bummer!  I had just gotten it the way I like it and now I've gone and wrecked it.  Hence I am reluctant to reinstall everything again and have to muck around getting everything back the way I like it.

I'll explain what I did (after I had done it I thought uh-oh I think that was a bad idea).  I was working on trying to install linux on my usb thumb drive and I was looking on [this page]("http://www.pendrivelinux.com/2008/05/23/how-to-fix-ubuntu-804-casper-script-for-persistence/").  I typed the following command:> gzip -dc /cdrom/casper/initrd.gz | cpio -i as root in the root directory (ie /).  After I had done it I thought that was probably a bad idea and sure enough on reboot gdm won't load and comes up with the following error:> var/lib/gdm does not exist
I can still log on into the command line so I haven't wrecked everything so I might be able to salvage something.  My system is Ubuntu 8.04 and is running mythtv-backend on it.  I was trying to get a mythbuntu frontend running on my usb drive so I can use it on my Windows laptop and I did the above command on the Mythbuntu 8.04.1 iso image.  Any help would be great guys, even if it is just that I've stuffed it and have to reinstall.

Thanks.

---

### Post by lewiz on 2008-09-27
i'd reinstall.  the initrd contains a whole stack of binaries that are now mismatched with the rest of your system.  it's odd that (at least my) initrd does not contain anything starting with var... but there could be all sorts of reasons you'd see this error

my advice:

tar cpf /media/usbstick/back.tar /etc /home /path/to/myth/configs

and then selectively restore what you need.  there may be other configs you'll want to grab too... if you've got plenty of space, the whole of /var would be handy

---

### Post by rossco on 2008-10-02
Hi Lewiz,

I had come to the same conclusion anyway and have reinstalled my system.  Its a bit frustrating because not everything works out of the box with my particular system setup and I had forgotten what I had done the first time to get everything to work.  Is there an easy way to back up a linux system so it easier to recover from such stupid mistakes?

---

