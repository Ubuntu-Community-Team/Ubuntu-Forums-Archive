---
title: "Blank Display After Installing Startup Manager"
date: 2009-12-16
forum: Hardware
---

### Post by gpeck157 on 2009-12-16
Hi All,

I installed Startup Manager from the repositories. Upon launching, it defaulted to 640 x 480 with 8 bit color. I changed it to 24 bit color and 1440 x 1280 if I remember correctly (unsure). Now when I try to login, I have no display after grub. I went to recovery mode (I was able to see the screen there) and uninstalled startup manager from the command line, but still have no display when I try to load normally. Is there a configuration file I now need to edit, and if so, what do I need to do? Or, can I mount my hard drive by using my install CD to edit whatever I need to do to fix the problem?

I'm running an HP zd7000 laptop (old) with an ATI graphics card. 

I'm posting this using my Windows side of my dual boot.

Any help would be greatly appreciated.

Thanks

---

### Post by gs777 on 2009-12-16
run the command

"sudo dpkg-reconfigure -phigh xserver-xorg "

the display willbe reconfigured

---

### Post by gpeck157 on 2009-12-16
> **gs777 said:**
> run the command

"sudo dpkg-reconfigure -phigh xserver-xorg "

the display willbe reconfigured

Thanks. I ran the command above from the recovery command prompt but it didn't work. I still have no display after hitting <Enter> on grub for a normal boot into my Ubuntu 9.10. 

Any other thoughts would be appreciated. Thanks for your response and attempt to help.

---

### Post by gpeck157 on 2009-12-16
I also removed compiz and compiz-core. This also did not help.

---

### Post by gpeck157 on 2009-12-16
Here is the latest. 

I went into (via recovery) /etc/gdm. Then I executed[HTML]sudo sh failsafeXServer[/HTML] This took me through several prompts (menus). One option was to use generic settings. I selected it then went back to the previous menu and selected the option to go to the command prompt. At the command prompt I logged in, then I typed [HTML]sudo gdm[/HTML]This launched my normal desktop. One would think everything was fine, but I still can't launch my desktop normally. I still have to go through the recovery mode and run "sudo gdm" at a command prompt after logging in to get to my desktop. Anyone have any suggestions? 

At least now, if I can't get a solution, I can back everything up and reinstall Ubuntu, but I would rather not. Any suggestions or thoughts are appreciated.

---

### Post by gpeck157 on 2009-12-17
Gave up! Reinstalled Ubuntu.

---

