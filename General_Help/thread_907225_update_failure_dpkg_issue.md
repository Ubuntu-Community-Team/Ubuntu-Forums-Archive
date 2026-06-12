---
title: "update failure dpkg issue"
date: 2008-09-01
forum: General Help
---

### Post by bmaguire on 2008-09-01
I'm very much a newbie to the Ubuntu world (though a very enthusiastic one).  I clicked on the update icon this morning, and instead of getting the simple, clean update I've gotten before, I got this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried entering 

sudo dpkg --configure -a

and got:

Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
rm: cannot remove `/boot/initrd.img-2.6.24-19-generic.dpkg-bak': Input/output error
dpkg: subprocess post-installation script returned error exit status 1

I'm afraid I have no idea what to do with this.

Thanks for any help,
Brian

---

### Post by ago on 2008-09-03
try to manually remove /boot/initrd.img-2.6.24-19-generic.dpkg-bak
ps did you install on a fat partition

---

### Post by bmaguire on 2008-09-03
Thanks, ago.  I'll give that a try.  The install is on an NTFS partition, so that should not be a problem (I assume from your question that a FAT partition would be)
Brian

---

### Post by llh11456 on 2008-09-06
video [AOC Gold](http://www.usfine.com/Age-of-Conan-USA-c-151.html) gamers have been seeking assistance [Age of Conan Gold](http://www.usfine.com/Age-of-Conan-USA-c-151.html) in playing and conquering the games that they live for.  [Age of Conan Power Leveling](http://www.usfine.com/Age-of-Conan-US-PL-c-146.html) Many of these items have successfully helped gamers achieve victory, but they cannot help with all games.  The easiest way to find  is to buy it. Similar to the above mentioned resources, purchasing is a great way for a player to enjoy and [Age of Conan PowerLeveling](http://www.usfine.com/Age-of-Conan-US-PL-c-146.html) conquer the game.[age of conan](http://www.usfine.com/Age-of-Conan-USA-c-151.html)

---

### Post by bmaguire on 2008-09-07
Hi ago,
The boot dir is empty and a search for initrd did not show the file you suggested I remove.  Any ideas on what I could try next?
Thanks,
Brian

---

### Post by kcee on 2008-09-09
Hi all,

I have a similar problem - used dpkg --configure -a to update to Heron - Update Manager still shows 109 outstanding updates, but doesn't respond.  sudo apt-get update comes back with:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I run it, I get

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpaper-utils:
 libpaper-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libpaper-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on libpaper-utils; however:
  Package libpaper-utils is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
dpkg: subprocess post-installation script returned error exit status 1

I'm not sure how to apply this thread to mine, but it's the closest I've found.  I apologize for any unnecessary info - if the directions are clear I can happily work in terminal, but I don't really know the meaning of what I'm entering.

What do you mean "manually remove"?

BTW I see I have an older kernel - maybe fixing this will allow me to update?

Thanks.

---

