---
title: "Flashing/blinking login screen"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by wsxaz on 2009-10-30
This is what happened:

I've upgraded one of my PC's from Ubuntu 9.04 to Ubuntu 9.10 using the standard upgrade manager. It all went well, until the system restarted. When the splash screen disappeared, I expected the login screen I'm used to to appear. But, however, this time a textual login screen appeared. My first thought was that it won't be a big deal. But it was. The text on the screen was flashing a couple of times per second, and I had to press a couple of times on a key on the keyboard to get a reaction. I was able to enter my username, but because you don't get visual feedback of the amount of characters you've entered for the password, I couldn't log in. 
Cold restart.
This time, I chose the "Recovery mode" in Grub. I was able to login, but not to start the Gnome GUI. 

Do any of you know what is happening and how to solve this?

---

### Post by apparle on 2009-10-30
Do you have nvidia. Did you install the drivers from .run file from nvidia instead of repositories?
A person I know had this problem. He installed the drivers from ubuntu repositories and his problem was fixed.

---

### Post by lefty_lou on 2009-10-30
I have the same issue but mine is a fresh install so what do you suggest for me?
and just if you didn't notice we can NOT login to the desktop!!

---

### Post by layingback on 2009-10-30
Tried [this]("http://ubuntuforums.org/showthread.php?p=8195286#post8195286") fix?

---

### Post by lefty_lou on 2009-10-30
Thanks worked a charm for me only thing different that i used the Ubuntu live cd and sudo in terminal to edit with gedit reboted and the Ugly Lol gdm was in place thanks layingback for pointing out that post!

---

### Post by gsumners on 2009-10-30
I had an easier fix than the above, on two computers.  One is a HP G60 laptop, the other is a homebuilt based on an ASUS M3N78 Pro mobo.

The commonality to both is the onboard nVidia graphics, for which restricted drivers were in use on 9.04 amd64.

Trouble symptom is flashing text login terminal, as others here and elsewhere have.  I did notice as the upgrade was running (I activated and watched the terminal section) that it failed to properly deal with the existing nVidia driver on the homebuilt rig, which was 180.44.  I wasn't surprised by the failure to boot to GUI.

Resolution steps I used on both:

1.  "Three finger salute" to cause a reboot.
2.  Go to the grub menu when available, and select the new kernel's recovery mode.
3.  At the offered menu when boot completes, select to go to root with networking.  Since you're now root by default (silly security risk that I disable once upgrade completed!), you don't need to use sudo for the following commands.
4.  apt-get update
5.  apt-get install nvidia-glx-185 (This is the most recent nVidia driver as of this post.)

This causes an uninstall of any existing nVidia driver fragments left from 9.04, as well as downloading / compiling / installing the new driver (and DKMS if not detected).

After these steps, the next boot went to GUI exactly as it's supposed to, on these two machines.

I hope it's this easy to fix for others, as it was for me!

---

### Post by sledd on 2009-10-31
I had the same problem with the flickering screen. I rebooted into recovery mode and could not find any X11 Directory, or Xorg.conf, so I ran ran nvidia-config from root. I then rebooted. This time it booted into the login screen and I was happy! I wanted to change screen resolution, so I had to run a terminal and entered "gksudo /usr/bin/nvidia-settings" logged in and reset my resolution and clicked on "Save to X configuration File" button, and rebooted. Settings were saved and again I'm happy!! 9.10 up and running, I hope this helps someone else...

---

### Post by wsxaz on 2009-10-31
> **apparle said:**
> Do you have nvidia. Did you install the drivers from .run file from nvidia instead of repositories?
A person I know had this problem. He installed the drivers from ubuntu repositories and his problem was fixed.
I didn't install any drivers, and absolutely don't know how to from the terminal.


I'm going to try all of these solutions, please stand by.

---

### Post by wsxaz on 2009-10-31
Success! 
What I did:

Connected the PC to the internet by cable instead of WiFi.
Started Aptitude, reloaded list of software, updated all packages.
Download and install pacakge xserver-xorg and rebooted :)

Now it all works fine

---

### Post by acme401 on 2010-03-22
> **gsumners said:**
> I had an easier fix than the above, on two computers. One is a HP G60 laptop, the other is a homebuilt based on an ASUS M3N78 Pro mobo.
 
The commonality to both is the onboard nVidia graphics, for which restricted drivers were in use on 9.04 amd64.
 
Trouble symptom is flashing text login terminal, as others here and elsewhere have. I did notice as the upgrade was running (I activated and watched the terminal section) that it failed to properly deal with the existing nVidia driver on the homebuilt rig, which was 180.44. I wasn't surprised by the failure to boot to GUI.
 
Resolution steps I used on both:
 
1. "Three finger salute" to cause a reboot.
2. Go to the grub menu when available, and select the new kernel's recovery mode.
3. At the offered menu when boot completes, select to go to root with networking. Since you're now root by default (silly security risk that I disable once upgrade completed!), you don't need to use sudo for the following commands.
4. apt-get update
5. apt-get install nvidia-glx-185 (This is the most recent nVidia driver as of this post.)
 
This causes an uninstall of any existing nVidia driver fragments left from 9.04, as well as downloading / compiling / installing the new driver (and DKMS if not detected).
 
After these steps, the next boot went to GUI exactly as it's supposed to, on these two machines.
 
I hope it's this easy to fix for others, as it was for me!
 Thank you for posting these instructions, this fixed it for me.  As this was my first try installing ANYTHING linux based it took a few trys but once I figured out the "Three finger salute" I was good to go  :)

---

### Post by pembertonq on 2010-05-02
Editing xorg.conf didn't work for me. What did was deleting xorg.conf completely. Then it worked a treat!

---

### Post by AeonEchelon on 2011-03-04
I tried the recovery mode solution, but there is no nvidia-gix-185 package. Maybe it's out  of date. What is it now?

---

