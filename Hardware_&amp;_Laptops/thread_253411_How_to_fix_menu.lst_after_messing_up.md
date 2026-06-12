---
title: "How to fix menu.lst after messing up???"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by mariner09 on 2006-09-08
I'll post here since this is not a version specific and might get more visibility than in the Edgy forum.

I was playing with hibernation settings and added swap=/dev/hda2 in the kopt line of menu.lst.

Now, when I boot it kernel panics thinking I was hibernated and reading an empty swap.

I tried booting the Live CD to fix, I removed that option from menu.lst, but how would you run grub-update to make the changes stick?

Is there some other method of fixing things at that point?

I'd hate to re-install...

---

### Post by dasunst3r on 2006-09-08
1. Take out the swap= parameter when booting.  Can someone kindly post the procedures to do that?
2. Once you're back in, go into the terminal, *cd* into where menu.lst is
3. Check if menu.lst~ is there: *dir menu.lst~*
4. If it is, issue the command *sudo cp menu.lst~ menu.lst*

Hopefully that works.

---

### Post by zxee on 2006-09-08
Grub is different from lilo in that regard i.e changes made to menu.lst are immeadiately available. How did you do the edit to menu.lst? Maybe check to make sure the changes were saved? Or there is another reason for the kernel panic.

---

### Post by mariner09 on 2006-09-08
From my experience playing with suspend2 in the past, it looks like the machine is trying to restore a hibernation session that never finished properly.  I'm getting a kernel panic with file I/O sync error.

If I boot in single-user mode, the line before the panic looks to be the process of reading /dev/hda2 which is my swap.

Hibernation and Suspend in Edgy don't seem to work properly on my machine as it just sits there with the crescent moon or sleep light flashing forever.

I booted the live CD and mounted /dev/hda1 as /tmp/tmproot and then dug in and vi'd my /boot/grub/menu.lst.

I can't copy menu.lst~ to menu.lst, because they were identical.

---

### Post by Neobuntu on 2006-09-08
Isn't it "update-grub" and couldn't you rename menu.lst and let update-grub fix it (so it would boot as before?)

---

### Post by mariner09 on 2006-09-08
update-grub won't work from the live CD.

It references the booted grub environment and not a temp mounted environment.

I did end up fixing it by making sure menu.lst and menu.lst~ were the same and removed all mention of the resume option.

Now to just get suspend working in edgy...

---

### Post by Neobuntu on 2006-09-08
Yeah I was thinking about in Single mode (recovery) booting (then "update-grub".)

---

