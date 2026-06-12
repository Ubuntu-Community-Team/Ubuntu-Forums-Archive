---
title: "No menu.list file..."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Izobalax on 2009-10-30
Right, so I've downloaded a clean, proper version of Kubuntu 9.10. I've MD5SUM checked the download and the burnt disc. It's all fine. 

The Live CD runs absolutely fine and the install proceeds with no trouble. 

HOWEVER...

In my first two installs, my first harddisk bootup was greeted with a GRUB error 15. I've found on the net that this means that GRUB cannot find the boot record. So on my third install I changed the boot loader to the correct device. Now, on running from the harddisk, GRUB says it's loading and stops there and does nothing. I'm back on the Live CD again, I've found my ext4 harddisk, looked in /boot/grub/ and there is no menu.lst file. 

What's going on?

/izo

---

### Post by drs305 on 2009-10-30
> **Izobalax said:**
> Right, so I've downloaded a clean, proper version of Kubuntu 9.10. I've MD5SUM checked the download and the burnt disc. It's all fine. 

The Live CD runs absolutely fine and the install proceeds with no trouble. 


What's going on?

/izo

If you did a clean install you are now the proud parent of GRUB 2, which replaced Grub legacy. There is no more menu.lst.

You can read about the new file system by viewing the Ubuntu community doc, [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")  This link has information on booting from the grub prompt, grub-rescue prompt, hung menu or how to reinstall G2 from the LiveCD if that becomes necessary.

There are also other links in my signature line that provide a lot of information about the new GRUB system.

And "ranch hand" has written an excellent introduction to Grub 2 here: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

and "Qqmike" on the kubuntu forums here:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0]("http://kubuntuforums.net/forums/index.php?topic=3106368.0")

---

### Post by Sealbhach on 2009-10-30
You could try this, it's the procedure to reinstall Grub 2 from a Live CD:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

The old menu.list has been replaced by grub.cfg in Grub 2 but we're not supposed to edit it anymore, instead there are other config files that feed info into grub.cfg, and we can edit those.

.

---

### Post by Izobalax on 2009-10-30
> **drs305 said:**
> If you did a clean install you are now the proud parent of GRUB 2, which replaced Grub legacy. There is no more menu.lst.

You can read about the new file system by viewing the Ubuntu community doc, [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")  This link has information on booting from the grub prompt, grub-rescue prompt, hung menu or how to reinstall G2 from the LiveCD if that becomes necessary.

There are also other links in my signature line that provide a lot of information about the new GRUB system.

And "ranch hand" has written an excellent introduction to Grub 2 here: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

and "Qqmike" on the kubuntu forums here:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0]("http://kubuntuforums.net/forums/index.php?topic=3106368.0")
Thank you very much for the fast and helpful post! I didn't realise that GRUB2 is now implemented. Unfortunately, none of this makes any sense to me. All I know is, I get the:

```
GRUB Stage 1.5

GRUB is loading...
```

...and then it stays there and does nothing. And I don't know how to fix this. I barely understand how devices are named with Linux! :(

/izo

---

### Post by Izobalax on 2009-10-30
> **Sealbhach said:**
> You could try this, it's the procedure to reinstall Grub 2 from a Live CD:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

The old menu.list has been replaced by grub.cfg in Grub 2 but we're not supposed to edit it anymore, instead there are other config files that feed info into grub.cfg, and we can edit those.

.


FIXED by following this link. Thank you very much!

/izo\

---

### Post by joplass on 2009-10-30
Someone screwed here in my case.  I did an upgrade.  When my box boots it displays a list with all my old kernels all in black and white.  You can't modify this in /etc/default/grub.  I can still go to my old grub and see the other list in there.  Why didn't they set up this thing that when grub2 is installing it removes grub or give us the option to use the old stuff.

---

