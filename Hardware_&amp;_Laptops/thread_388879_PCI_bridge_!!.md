---
title: "PCI bridge !?!"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by CSandman on 2007-03-20
I'm running Kubuntu on my Toshiba Satallite Pro A100 and when I boot kubuntu I get a quick glimpse of what looks like hardware related error.  Once booted when I switch to one of the terminals (ctrl + alt + F1-F6) I can see the error:

[17179571.268000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[17179571.268000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[17179571.268000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[17179571.268000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0

Should I be alarmed at this... I don't even know what that means!?!?
Comments, suggestions, solutions are all welcome even Holy CR** as long as there is something constructive :D
~CS~

---

### Post by CSandman on 2007-03-20
Oh I guess I should mention that I'm running an Atheros AR5006EG wireless chipset that isn't recognized at all by ubuntu 6.10 but was recognized in my brief trial of 7.04 (Feisty)!  It may or may not be related.

---

### Post by nyinge on 2007-03-20
lol I got a different one for you.
```
 PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0 
```
IMO, as long as things working, you shouldn't be worried.  Of course, we could always wait for a more technical solution.  :D

---

### Post by squirrelplayingtag on 2007-03-22
I get the same errors two errors about the resource region 7 and 8. I also am attempting to upgrade to the 2.6.20-3 kernel using the source from kernel.org. The install goes fine but when it reboots I get the error about "PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0" and my system hangs. If anyone has any suggestions it would be greatly appreciated.

---

### Post by nyinge on 2007-03-23
Remove the word "quiet" from the line starting with "kernel" in the GRUB menu.  This should give you more output to debug.  Did you also make sure that you didn't leave out any essential components when you're configuring the kernel?

---

### Post by CSandman on 2007-03-23
Thanks for the suggestion nyinge, I'd like to say I'm pretty knowledgeable about linux and stuff, but I've only been with linux and ubuntu for a couple of months.  How would you go about editing the GRUB menu?  Also I have enough trouble trying to fix build errors for small programs and drivers I haven't the faintest idea how to configure my kernel, I just let the live CD do its job, then try to clean up whatever is left over.

---

### Post by squirrelplayingtag on 2007-03-23
Ahh I got this one!
Aight, open up a terminal and change to the /boot/grub directory
Make a copy of your current menu.lst file and rename it as something else.
Open up the menu.lst file and remove quiet from the boot options. This must be done as root(sudo).
```

cd /boot/grub; cp ./menu.lst ./menu.lst.old; sudo nano ./menu.lst;

```

---

### Post by squirrelplayingtag on 2007-03-23
Just a side note, I did forget to include an item in my new kernel. I skipped the 2.6.19 release which is where I would have noticed I needed it so apparently the errors are unrelated to the kernel. I still get the same errors about the pci bridge regions and mem #6.

---

### Post by nyinge on 2007-03-24
> **squirrelplayingtag said:**
> Just a side note, I did forget to include an item in my new kernel. I skipped the 2.6.19 release which is where I would have noticed I needed it so apparently the errors are unrelated to the kernel. I still get the same errors about the pci bridge regions and mem #6.

Are you able to boot your previous kernels?  Something got screwed up on my laptop that I wasn't even able to boot any of the kernels.  Well, at least I got an excuse to upgrade to Feisty...  reinstalled everything.  :D

---

