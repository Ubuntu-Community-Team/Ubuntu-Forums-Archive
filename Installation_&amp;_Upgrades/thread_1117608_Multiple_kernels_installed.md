---
title: "Multiple kernels installed"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by voxmagna on 2009-04-06
Hi, not sure if this should be in the newbie section (Me) or here.

I installed 8.10 desktop from a cd image to a small notebook with minimal disc storage, then a load of updates came along and my kernel which I think was 2.6.27.7 is now 2.6.27.11. I'm only just starting so I don't run anything special which might need an earlier kernel.

I'm suspecting that both versions may be taking up twice the HDD storage.

Is there a reason why both kernel versions should be available? If there isn't, how can the 2.6.27.7 version be removed cleanly to recover disc space and presumably the grub menu needs editing.

The second question is I downloaded a 3rd party.tar.gz application, expanded and installed it. After locating the binary and making a link with Nautilus, I can start the App. But how do I get the app listed in say the applications menu? 

As you guess, I'm coming from a total Windows background, so help would be appreciated. Thanks

---

### Post by issih on 2009-04-06
When a new kernel is installed in an update, the system keeps a preset number of the old ones as a precaution in case the new kernel is incompatible with your hardware. Keeping at least one is a good idea.

Ubuntu keeps quite a few by default, but you can tweak the number it keeps if you install startupmanager from the repositories, just search in synaptic package manager or the add/remove utility for startup manager.

You can also remove the old kernels directly by simply deselecting them in synaptic.

The disk space is really not an issue though, on a modern machine, the kernel isn't really that big.

As for your program, first let me ask the important question, did you HAVE to get it from a website? Did you check if it was available from add/remove or synaptic first. Your life will be much much easier if you get out of the windows mindset of downloading from a website and instead get used to installing from the repositories.

Having said that, to edit the menu just right click on the menu itself and select the obvious option :)

Hope that helps.

---

### Post by voxmagna on 2009-04-06
Thanks issih, mindset is a problem for me. I'm trying to translate what little I knew of DOS commands to Linux commands and where possible use the Ubuntu Desktop which has more familiarity. 

My mindset with Windows has been to make sure anything running is available for re-install from my hard drive when things go wrong. In the past this has been an issue with paid for downloads where I've used weblinks to Microsoft installers, only to find some time ahead the links have died or been moved.

Thanks for help on the older kernels. I think then it's a good idea to keep at least the previous kernel release. 

Now I need to find out why my open Windows zip across the screen horizontally as in a 'scroll', then sometimes the top bar disappears, the window stays stuck and I can't move it anywhere or close it down with a mouse click.

---

