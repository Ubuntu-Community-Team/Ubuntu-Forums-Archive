---
title: "&quot;Alternative&quot; dual-booting?"
date: 2008-07-15
forum: General Help
---

### Post by Veracon on 2008-07-15
Hello all!

I'm currently running Vista on a reasonably new (c. 4 months old) laptop, and I'd like to dual-boot this with Ubuntu (8.04). Now, installing Ubuntu shouldn't be a problem, but if possible, I'd like to have Windows still as the default OS, with no traces as Ubuntu unless I specifically decide to boot it (reason being I occasionally lend my computer to not-so-computer-savvy people, who might not have a clue to do with the GRUB screen).

So, essentially, is there a way to (either):
[LIST]
[*]Hide GRUB and boot into Windows UNLESS I press a certain button while the computer starts? or
[*]Hide GRUB entirely, boot Ubuntu from a boot CD (or USB key)? or
[*]Something else which'll allow my computer to run as any other Windows computer but with the option of booting to Ubuntu, however not explicitly showing this option upon boot?
[/LIST]

Sorry if that came out confusing, but I hope someone understood my question and is able to help me. Thanks in advance! :)

---

### Post by tramir on 2008-07-15
You can use Start-up manager (it's in the repositories, package name "startupmanager") to hide the Grub menu, setup Windows as the default option, remove the timeout when showing the menu etc. You can experiment with it, I think the only thing that could happen is that you'd get a short message about pressing ESC to see the menu and then Windows should start loading. And when you want to boot in ubuntu, you'd just have to be fast enough to press ESC when that message shows and the grub menu would show etc etc. Hope this helps.

---

### Post by Veracon on 2008-07-15
> **tramir said:**
> You can use Start-up manager (it's in the repositories, package name "startupmanager") to hide the Grub menu, setup Windows as the default option, remove the timeout when showing the menu etc. You can experiment with it, I think the only thing that could happen is that you'd get a short message about pressing ESC to see the menu and then Windows should start loading. And when you want to boot in ubuntu, you'd just have to be fast enough to press ESC when that message shows and the grub menu would show etc etc. Hope this helps.
Thanks, I'll give it a try. :)

---

