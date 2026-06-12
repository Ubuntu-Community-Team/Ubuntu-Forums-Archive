---
title: "Restarting into another OS unattended"
date: 2008-07-12
forum: General Help
---

### Post by Arukas on 2008-07-12
A long time ago, when I tried Suse and a lot of other flavors.  Ubuntu wasn't known or not out at the time.  

Suse was the only one with a feature that lets me restart into Windows XP (I dual boot) from the Suse Login or the Suse DE.  


Can this be done in Ubuntu?  I really want this feature.  

Thanks.

---

### Post by WRDN on 2008-07-12
As far as I know, you can't do that. Rather, Ubuntu includes the GRUB bootloader where you can choose the OS on startup.

---

### Post by Arukas on 2008-07-12
Yeah, you could use the bootgrub menu in Suse too.  But you could make choices in the DE or Loggin if you wanted too that way you didn't have to wait and catch the grub menu. 

Any reason why Ubuntu don't have a feature like that?  I know dual/multi boot is a common thing.

---

### Post by Taxman415a on 2008-07-12
I don't think there's a tool to do it automatically for each boot, but I know the manual way: change the default OS in GRUB. I can't think of the syntax off the top of my head, but google for the GRUB howto and look for default OS. Then it will boot into that OS the next time, and each time until you change it during boot or change the grub config.

---

### Post by Arukas on 2008-07-12
Here's a link to the Suse way of manually doing this?
[http://en.opensuse.org/Reboot_from_CLI_to_selective_partitions](http://en.opensuse.org/Reboot_from_CLI_to_selective_partitions)

Does ubuntu have a way of scripting it?

---

### Post by Taxman415a on 2008-07-12
Yeah, you use grub commands basically. From the grub manual [http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html#Invoking-grub_002dset_002ddefault](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html#Invoking-grub_002dset_002ddefault)

You need to change the line in /boot/grub/menu.lst  that has default in it (it probably says default         0), to read like that link I gave you, namely, default saved

Then if you look at the number order of your bootable partitions (either in the grub menu or in /boot/grub/menu.lst) you can set the second one to boot the next time by running
```
sudo grub-set-default 1

```

Then you can change it back to the regular default to first one by running ```
sudo grub-set-default 0

```

Sure this is scriptable, and someone could write a nifty tool like Suse has, but it just doesn't seem to exist yet. For now it seems you'd need to write a script to do it or manually run grub-set-default before you reboot. You could also send up the idea on [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/), it doesn't seem like it would be too hard to code by someone able (read, not me :)

Also big disclaimer: I didn't test this yet since I have a pretty screwy grub config that I haven't gone about fixing yet since it works fine. I've just installed a few times on testing partitions.

---

