---
title: "Can't add new printer through cups"
date: 2008-07-20
forum: General Help
---

### Post by mcradish on 2008-07-20
Hi,

I'm trying to add a printer to my 8.04 Server (headless). I've installed cups, connected the printer (Brother Laser via USB). After fiddling with the cupsd.conf I was able to get the web admin page working. 

However, when I go to add a printer there's a problem. I click "Find New Printers". This finds the correct printer, I click "Add this printer", enter a name etc and then continue. On the next page I have to select the driver to use - I want to use Raw (sharing via Samba) but when I click Continue it just hangs forever, until FF times out.

I've looked in the cups log and I see this:

```
E [20/Jul/2008:21:56:17 -0400] cupsdCloseClient: Error in the push function.

```

and in dmesg there's hundreds of these:

```
[  836.513835] audit(1216605911.861:26): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5718 profile="/usr/sbin/cupsd" namespace="default"

```

I've googled around but can't find much. Any ideas? I really want to replace my Windows server but this is going to be a problem...

---

### Post by plucky on 2008-07-21
Have you installed the Brother Laser drivers for your printer?

See the Wiki for [Brother Driver Packaging](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother)) for the packages you need to install for your printer from the Synaptic Package Manager.

You need to install both the cups-wrapper and lpr-drivers from Synaptic.


Good Luck

---

### Post by mcradish on 2008-07-21
I didn't have the drivers installed as I specifically wanted to set it up as a Raw device (so that Windows clients could print directly to it) following the advice on the Samba site. 

After your suggestion I did try installing the drivers and it seems to work fine, but now the Raw driver type isn't even shown in the list of possible types when I add it. It does print if I select the correct one, so I guess I'm OK for now, but I have a couple of other printers for which there are no Linux drivers and so I'd like to know why the Raw mode didn't work.

Any more ideas would be welcome :)

---

