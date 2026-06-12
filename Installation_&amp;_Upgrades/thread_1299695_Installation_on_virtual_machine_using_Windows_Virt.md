---
title: "Installation on virtual machine using Windows Virtual PC in Windows 7"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Wilester on 2009-10-24
When I load the installation ISO into the VM and start the VM I get the normal Ubuntu screens, i.e. language selection and then "Try", "Install" etc. 


Now my problem is whichever of this options I pick and whether I pick them using safe graphics mode the VM will close after this screen:

[IMG]http://i6.photobucket.com/albums/y224/wilester/UbuntuVM.jpg[/IMG]

I'm assuming it's a problem loading the hardware drivers. :D

Anyone have any thoughts?

Many thanks.

---

### Post by mikewhatever on 2009-10-24
Does Windows Virtual PC supports Linux OSs? If it doesn't, get virtual box instead.

---

### Post by howefield on 2009-10-24
> **mikewhatever said:**
> Does Windows Virtual PC supports Linux OSs? If it doesn't, get virtual box instead.

That's the problem, scroll to the bottom ,.. "supported guest operating system"

[http://www.microsoft.com/windows/virtual-pc/support/requirements.aspx](http://www.microsoft.com/windows/virtual-pc/support/requirements.aspx)

---

### Post by Wilester on 2009-10-24
I could have sworn I read articles with people using Virtual PC with linux. Never mind. I've installed VirtualBox now and it works fantastically.

Thanks guys.

---

### Post by howefield on 2009-10-24
To be honest, I thought that too which lead me to check the website. If it can be, then MS (predictably ?) are keeping it quiet :)

You're probably better off with virtualbox in any event, in support terms should you need it. Remember to install guest additions for the extra drivers and features it gives you.

---

### Post by chr1sM on 2009-10-25
VirtualBox was unnecessary, you can can install Ubuntu on Win7/Virtual PC. I have it running, did you try the i8042.noloop kernel booy option.

I have Ubuntu running in virtual pc, I am just having a problem getting the vm to release the mouse when you give it the focus. If anyone can help on this front let me know.

---

### Post by howefield on 2009-10-25
> **chr1sM said:**
> VirtualBox was unnecessary

but...as it would seem, preferable. imho ;)

---

### Post by Davepar on 2009-10-25
ctrl-alt-left arrow will release the mouse from the virtual machine.

I just attempted installing 9.10 RC into a Win7/Windows Virtual PC. Install seemed to go fine, although it ended in a black screen rather than auto-rebooting. I did a "turn off" on the virtual machine. Now when it boots I get:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Dave

---

### Post by Jeshimon on 2010-02-24
> **Davepar said:**
> ctrl-alt-left arrow will release the mouse from the virtual machine.
 
I just attempted installing 9.10 RC into a Win7/Windows Virtual PC. Install seemed to go fine, although it ended in a black screen rather than auto-rebooting. I did a "turn off" on the virtual machine. Now when it boots I get:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
 
Dave
 
I have a very similar problem.  Does anyone have it working under 'Windows Virtual PC' on Windows 7?  I could install Virtual PC 2007 SP1, I know it works there, but I'd rather not.  I'd like to keep things at a minimum.

---

