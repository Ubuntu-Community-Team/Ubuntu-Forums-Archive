---
title: "User Access Problem"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Belthazard on 2009-06-26
Hi there, I am quite new to Linux and I have just installed Xubuntu 9.04 onto my Playstation 3 and am now having a problem doing anything. 
I have no access to sudo or anything else that require administrator access.
When I type id into the terminal I get:
uid=1000(hayden) gid=1000(hayden) group=1000(hayden)
I have tried to add myself to the admin in group file from the live cd, however the cd I have does not give me the option to boot the live cd.
Also while installing, I was not given an option of whether or not to create an admin account, so am unsure whether one was defaultly made or not.

Can someone please help me to get admin user control on my account?

---

### Post by tommcd on 2009-06-26
While I know nothing about the particulars of installing Ubuntu onto the Playstation 3, I can point you in the right direction to troubleshoot the sudo problem. See this page from Asiyu's Ubuntu site about editing the /etc/sudoers file:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

And welcome to the Ubuntu forums!! Welcome to the cool side of computing!

---

### Post by Belthazard on 2009-06-26
Thank you for the warm welcome. 
I will try booting into recovery mode and looking into the group file

---

### Post by Belthazard on 2009-06-26
I seem to be unable to boot into recovery mode. 
Pressing escape during boot up only brings up a few weird characters.

---

### Post by tommcd on 2009-06-26
> **Belthazard said:**
> 
I will try booting into recovery mode and looking into the group file
The actual file in question is the /etc/sudoers file.

---

### Post by Belthazard on 2009-06-26
Ok how would I go about editing the contents of that file?

---

### Post by tommcd on 2009-06-26
> **Belthazard said:**
> I seem to be unable to boot into recovery mode. 
Pressing escape during boot up only brings up a few weird characters.
If you don't see the grub menu on bootup (by default if Ubuntu is the only OS on the Playstation, or any computer, you would not see the grub menu on bootup) hitting the **Esc** key on bootup should display the grub menu, which gives you the option of booting to recovery mode.

What "weird characters" are you seeing exactly?

---

### Post by tommcd on 2009-06-26
> **Belthazard said:**
> Ok how would I go about editing the contents of that file?
You have to boot from recovery mode as it says in the tutorial that I linked to. If you can't boot to recovery mode, this may be a problem.
What CD did you use to install Ubuntu onto the PS3?

---

### Post by Belthazard on 2009-06-26
The characters I get from pressing Esc are 
'^['
I have tried pressing Esc from when I restart the PS3, up until the kboot screen appears where I have tried to enter 'grub', 'live' 'linux 1' and pressed Esc.
But nothing has brought up a different menu.
After pressing Enter and allowing the boot to continue, i have pressed Esc and have only recieved the above characters before the screen loads the GUI Login

---

### Post by Belthazard on 2009-06-26
I downloaded the disc image from [http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/) 
I downloaded the Playstation 3 alternate install disc

---

### Post by tommcd on 2009-06-26
> **Belthazard said:**
> The characters I get from pressing Esc are 
'^['
I have tried pressing Esc from when I restart the PS3, up until the kboot screen appears where I have tried to enter 'grub', 'live' 'linux 1' and pressed Esc.
But nothing has brought up a different menu.
After pressing Enter and allowing the boot to continue, i have pressed Esc and have only recieved the above characters before the screen loads the GUI Login
I'm not sure why that would be. Some google searching did not find abything about this problem for the PS3.

---

### Post by Belthazard on 2009-06-26
Hmm yes I tried google, but he didn't help me too much. I am going to try a reinstall and look at the instructions more carefully. Thank you for your help

---

### Post by dedicated1 on 2009-07-04
I'm having the same thing.   From what I've experienced is that I have not been asked to give an root password while installing Xubuntu 9.04 on my ps3. sudo won't work and I have limited access to things, for example I can't access Users and Groups.  The worst thing is that because it's installed on a ps3 I suspect (X)ubuntu cannot go into recovery-mode using GRUB. If there is any alternative to using the esc button please do let me know!

---

### Post by DrRSP on 2009-07-23
I've had the same deal with the PS3 (xubuntu 9.04). So know the problem and cannot boot into recovery mode to solve it. How did you folks get on? Did you have success with a different version?

Thanks

---

### Post by runebinder on 2009-08-03
I've got the same issue with Xubuntu 9.04 on the PS3. Any ideas?

---

