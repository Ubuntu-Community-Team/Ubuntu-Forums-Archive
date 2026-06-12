---
title: "log in as root"
date: 2008-08-17
forum: General Help
---

### Post by arcanewulf on 2008-08-17
ok, I'm trying to set up a virtual machine as a linux server. Because of    my processor, amd with variable clock speed, sometimes (actually often) the virtual machine recognizes 1 keystroke as 5 or more. I want to log as in root as to avoid using the terminal as much. The server is for personal use, and will only be used  with lan, so security is not an issue. Now here's the issue. I set a login password for root but I can't enable logging in from root as the menu to do so closes almost instantly. Is there a command to enable it from terminal or a config file I could edit? Thanks in advance

---

### Post by wilbbe01 on 2008-08-17
If you haven't enabled the root account you can do that by typing the following from an account with sudo privelages.

> sudo passwd root

edit: and I don't know why I thought you wanted ssh access as root.  Do the suggestion above and that should get you what you want I think.  Although, I recommend not logging in as root graphically, local network or not.  It is a lot easier to accidentally screw up your system, the threat to a system logged in as root graphically is between the keyboard and chair more so than the outside internet.

_________
Original stuff I gave you for no reason.

Did you try editing anything in /etc/ssh/ssh_config?  I think to allow root login remotely you could try the following in that file.

> #Do not allow root login
PermitRootLogin yes

---

### Post by arcanewulf on 2008-08-17
It's 1 AM here, I'm going to sleep and I'll check back in the morning. I tried it again, the login window configuration menu appears just long enough to read what you're looking at and see the tabs at the top and then closes again.

---

### Post by arcanewulf on 2008-08-17
Sorry I missed your post, I'll give that a try.

---

### Post by wilbbe01 on 2008-08-17
> Original stuff I gave you for no reason.

It's a good thing you missed my post, I edited it a thousand times before I got it right.  Tell me if any of that helps.  It should prompt you for your sudo password then you can enter the root password twice.

---

### Post by pparks1 on 2008-08-17
> **arcanewulf said:**
> the virtual machine recognizes 1 keystroke as 5 or more. Are you using Microsoft Virtual PC? I've seen this behavior there....but not in VMWare Server or Virtual Box which are both free virtual machine tools and seriously outperform Microsoft Virtual PC with Linux virtual machines.

As far as the logging in with root goes, it's not well tolerated around here.  I think it's actually against the posted rules.   I cannot provide any assistance here as I don't enable or use the root account on my Ubuntu boxes.  I've found the sudo system quite functional and well suited to my needs.

---

### Post by sayakb on 2008-08-17
If you want GUI as root, then either:
```
gksudo nautilus
```
Or:
Press Ctrl+Alt+F1 and do
```
sudo bash
startx
```

Note: Running the UI as root may be potentially dangerous and is liable to threats and security violations. Try to avoid the second option, unless you know what you are doing exactly.

---

### Post by arcanewulf on 2008-08-17
pparks, it's vmware ace edition. If I could actually type most of the time I'd just use sudo for root functions, but unless I type just tapping the keys I get extra letters in almost every word. I just want root enabled as I install apache and php and configure stuff the way I want it.

---

### Post by pparks1 on 2008-08-17
> **arcanewulf said:**
> pparks, it's vmware ace edition. If I could actually type most of the time I'd just use sudo for root functions, but unless I type just tapping the keys I get extra letters in almost every word. I just want root enabled as I install apache and php and configure stuff the way I want it.

Interesting on VMWare.  I've been using VMWare Server 1.x at work under Windows XP, Windows Server 2003, and various Linux hosts and I haven't seen this issue.   They have all been Intel CPU's, (Core 2 Duo's, Xeon's).

I understand what you are saying about root.  I come from the RedHat world myself and do most of my sysadmin work logged in as root...so the sudo system was quite a change for me.  For me, I only log on to do admin tasks and then I'm back to my workstation where I am a normal account.  I only stay on a server for the absolute shortest amount of time possible.

---

### Post by p_quarles on 2008-08-17
Sorry folks, but the forum policy is against how-tos on graphical root logins. Root access on any *nix machine involves delicate privilege balance, and Ubuntu's approach is to use sudo and its graphical wrappers (gksu and kdesu) only. If you go beyond that, you do so at your own risk.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

In any case, this is a hardware issue, and would be better addressed in that vein. Administering any machine (including a Mac OS X or Windows box) without a working keyboard is going to be difficult, and privileges aren't going to fix that.

---

