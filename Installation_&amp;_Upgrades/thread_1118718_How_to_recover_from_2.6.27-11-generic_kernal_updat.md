---
title: "How to recover from 2.6.27-11-generic kernal update"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Daddyo-613 on 2009-04-07
**[SOLVED] The Problem:** My system crashed during a kernel update from 2.6.24.23-generic to 2.6.27-11-generic. On reboot 2.6.27-11-generic can not initiate or even identify the hard drives. Clearly the new kernel was corrupted as a result of the crash while the kernel was being installed.

I have been able to boot my system using a previous kernel 2.6.24-23-generic so that I could make this post. However, the nVida driver can only function in low graphics mode. I am running Ubuntu 8.10 \n\l with a GeForce 7300 LE and I am presently using ver. 177 of the nVida driver.
[B]
My Question:[/B] Now that I'm back into my system can I safely run the update of the kernel to 2.6.27-11-generic again and reboot in the normal way?

Any help would be appreciated.

---

### Post by Zwack on 2009-04-07
I have an odd problem with 2.6.27-11 too... I have to hold down control to get it to boot.  No seriously.  

2.6.24-23 boots fine on it's own, but 2.6.27-11 requires me to hold down control. or it just sits there.

Z.

---

### Post by Daddyo-613 on 2009-04-07
After some further research and some sage advice from a friend I was able to solve my problem. The kernel can safely be reinstalled and, if done properly, won't affect any of your custom settings for your desktop or other programs you may use. The preferred method is as follows:
[B]
The Solution:[/B]
[B]
Step 1: Verify the Kernel Presently in Use:[/B]

Before you go to step 2 to remove the remains of the corrupted kernel you want to be certain that you have logged on using a previous version. 
Open a terminal 

Applications>Accessories>Terminal 

and cut and paste the following code:

```
uname -r
```That will display the kernel that is in use. If it is the same as the Kernel you want to replace, restart your computer and boot up using a previous version. You can do that by pressing the <esc> key when the computer starts to reboot and displays "Grub" on the screen. A list of kernels should appear. Scroll down to the previous version and press enter. Once your system has booted up you can open a terminal and run the command above again to verify the kernel that is running.
[B]
Step 2: Remove Corrupted Kernel:[/B]

Open the Synaptic Package Manager, 

System>Administration>Synaptic Package Manager

when it opens type in the name of the Kernel you want to remove. In my case it was "2.6.27-11-generic" (without the quotes, remember the search is case sensitive and dashes and dots count). What will be displayed is a long list of packages that contain the characters you typed into the search. What you're looking for is a package called
"linux-image-2.6.27-11-generic". Of course if you're doing this for a different kernel it you will want to find the listing "linux-image-" followed by the kernel number that you want to remove. Right click on the selected line and click on the line "Mark for Complete Removal" then press "Apply" and the Synaptic Package Manger will complete the removal.
[B]
Step 3: Reinstalling the Kernel:[/B]
Once the corrupted kernel has been removed and while you're still in the Synaptic Package Manager you want to update the list of packages to make sure that you're installing the most recent version, so click on reload.

Type in "linux-generic" in the search box (don't forget no quotes and the case sensitive stuff). To the right of the list under the heading "Latest Version" it will show the number of the version you're looking for. In my case 2.6.27.11.14. This is the linux meta package for the kernal you want. A meta package contains all of the other files you will need that are dependent on the kernel. Just right click on the linux-generic package selected and click on "Mark for Installation" then press "Apply" and the Synaptic Package Manager will complete the install.

**Step 4: Reboot:**
Once the install is fully completed you can close the Synaptic Package Manager and reboot your system. It should reboot normally using the new kernel and you're done.

You may want to run uname -r again when you're back up just to have the pleasure of seeing the correct kernel infomation displayed. 

I hope this will be of some help to others.

P.S. All of the steps can be completed using your terminal but if you're like me and can't remember the commands from day to day using the GUI features is just as good and fixes the problem just as well. Good luck!

---

