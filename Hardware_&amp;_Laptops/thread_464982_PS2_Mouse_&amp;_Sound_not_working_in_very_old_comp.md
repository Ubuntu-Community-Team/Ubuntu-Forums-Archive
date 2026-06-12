---
title: "PS/2 Mouse &amp; Sound not working in very old computer"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by idx on 2007-06-05
I have just loaded edubuntu on my very old computer working on win98 with the following specifications:-

---------------------------------------------------------------------------
Processor - 667 megahertz Intel Pentium III
Main Board: SiS-630 
Bus Clock: 133 megahertz
Standard 101/102-Key or Microsoft Natural Keyboard
PS/2 Compatible Mouse
BIOS: Award Software International, Inc. 6.00 PG 12/11/2000
SiS 630/730 [Display adapter]
SiS 5513 Dual PCI IDE Controller
C-Media PCI Audio Legacy Device
CMI8738/C3DX PCI Audio Device
-----------------------------------------------------------------------------

edubuntu installed just fine in good time without any problems.

However after logging in i realised that the mouse was not working and i also did not hear any sounds.

How do i go about diagnosing and solving my problem?? I am a newbie and do not know how to work in the terminal or any keyboard shortcuts.

---

### Post by hboshoff on 2007-06-14
Are you referring to the Feisty (7.04) release of Edubuntu?

Maybe the mouse problem is related to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382")
which has apparently been fixed for SIS chipsets in a kernel update.

If you can log into the GNOME desktop, press Alt-F1 to activate the menu, and navigate using the keyboard arrows to System -> Administration -> Update Manager. Press Tab twice to highlight the Check button, then Enter, (give your password when requested) and once the list is available, Tab to Install and Enter. Of course you need to be connected to the Internet to let this work.

For the sound card you need to install the correct kernel module using modprobe in the terminal. I see only two CMI modules listed, of which the PCI one likely matches your hardware: snd-cmipci.

Do not fear, it is not that difficult. Open the terminal window from the menu: Applications -> Accessories -> Terminal. Then type in the following line ```
sudo modprobe snd-cmipci
``` and Enter. You will be asked to type your password before the command runs.

If there is no error message, it has likely worked. You can check by typing in the terminal again```
alsamixer
``` This brings up a graphical interface inside the terminal. If the module is correct, you will be able to change the parameters using the arrow keys on the keyboard. Press Esc twice to quit AlsaMixer.

Now you want to automate loading the module every time you boot. Press Alt-F2 and type in the box```
gksu gedit /etc/modules
``` You may be asked for your password again, then a window opens with the text editor Gedit, ready to change the file. Add the name of the working module on its own line at the bottom of the list. Save & close the window.

Should you not get past the mouse problem, you might consider using previous versions of Edubuntu, namely Dapper or Edgy, at least until Gutsy comes out in October.

Good luck.

---

### Post by idx on 2007-06-16
Thank u very much. It was exactly what I was looking for.

Although mouse is working, sound is still not working. 'sudo modprobe snd-cmipci' gave a 'no such command' but 'alsamixer' works, at least the GUI is visible and seems to be working.

I have not yet investigated the sound problem thoroughly. Is there any specific tool I could run. I tried the System -> Preferences -> Sound without any results.

Thank u once again. I had almost given up hope. well..........patience pays.

---

### Post by hboshoff on 2007-06-18
I am surprised at the 'no such command' result.

If you enter 'sudo' on its own in the terminal, do you get a 'usage' message? What about 'modprobe' on its own?

If either is absent, it would be very strange. Both are basic commands to (Edu)buntu. They should be in /usr/bin/sudo and /sbin/modprobe respectively, and if they are not, it must be an installation error. (Try eg 'which sudo' in the terminal.)

If both are there, try 'sudo modprobe' and see if it asks your password (at least the first time), and then gives the 'usage' of modprobe again.

Then, if you try 'sudo modprobe snd-c' and instead of completing the module name or pressing Enter, press Tab twice to see which modules are available. (This is called Tab-completion of commands, and is quite useful.) snd-cmipci should be on the list. If it's not, I don't know where to get it. Someone?

If you start AlsaMixer, does it report the card and chip correctly? I have used neither AlsaMixer nor Sound Preferences, but they seem like different interfaces to much the same settings. I suspect that both need the kernel module to work before they can be used. And I know that support for some older sound cards has been dropped from more recent kernels, which means that the module has to be loaded with modprobe. Whether this is true for snd-cmipci, is not clear to me.

But if the driver is loaded already, 'sudo modprobe -rv snd-cmipci' should print a list of removed modules. You can see them being inserted again with 'sudo modprobe -iv snd-cmipci'. That is, if you have all the necessary files...

---

