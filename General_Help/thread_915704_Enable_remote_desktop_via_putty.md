---
title: "Enable remote desktop via putty"
date: 2008-09-10
forum: General Help
---

### Post by Jowah on 2008-09-10
Before opening this thread, and even register to forums, I made appropriate researches but found nothing....well nothing that's not graphical way to do this.

Basically, I bought an ubuntu server (currently running ubuntu-8.04--hardy-lts) and obviousily i have full-root access to it, but only through SSH.

I installed VNC succesfully and would like to log in using remote desktop, but I can't actually do the "enable step" on my server, since all guides i found online say:


> Navigate to the System \ Preferences \ Remote Desktop on the Gnome top menu.

You'll see this window:

The first two checkboxes need to be checked in order for remote desktop to be enabled.

The Security section is important: If you select the "Ask you for confirmation" code, then you will need to be at the computer in order to allow the other person to access your desktop. If you are trying to remotely access one of your own computers, you will want to uncheck this box.

The second checkbox should always be checked, and you should enter a secure password. You will be prompted for this password when you try to log on.

Too bad I can't actually do it. What should I do relying on putty only? I'm not a big Linux guru, hence why I'm asking some help  here. 

Thanks in advance for help~

---

### Post by Ctrl+Alt+Del on 2008-09-10
If your box is located outside your house and you are connecting to it via the internet vnc isn't really ideal...

Security-wise it would be much better to go for [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

---

