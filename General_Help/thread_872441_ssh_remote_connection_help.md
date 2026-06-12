---
title: "ssh remote connection help"
date: 2008-07-28
forum: General Help
---

### Post by vvtc on 2008-07-28
hello,

i am not sure which section to post this in, so i posted this is general

i am running ubuntu 8.04

my question is if it is possible to show a remote ssh connection computer's desktop using "X windows"

what i know to do is first connect to the remote computer by:

ssh -X user@ipaddress
then enter password and i am in

i have already tested this and can run/see/use remote programs

is there a command to show the remote computer's desktop in full GUI? or if not with ssh, is there some other way to achieve this?

thanks

---

### Post by Locke_99GS on 2008-07-28
Do as you have done, then run *gnome-session* or *startkde*.

---

### Post by vvtc on 2008-07-28
that works...thanks!

the only problem is that when i do that, the remote desktop loads on top of my ubuntu desktop and is a mix between the two, how to I open the remote desktop in a separate window?

---

### Post by cariboo on 2008-07-28
You can use the remote desktop software that is installed by default, or you could use one of the vnc variants. Search for tightvnc in synaptic.

Jim

---

### Post by vvtc on 2008-07-28
i tried the remote desktop software, im not sure how to use it

i installed the tightvnc stuff...but iono how to use that either

sorry, im new to ubuntu, and linux in general

thanls

---

### Post by vvtc on 2008-07-28
:confused:

---

### Post by dontodd on 2008-07-28
Try NoMachine's NX. You need to install the server on the box you're connecting to, and the client on, well, the client.

This gives you a whole new X session, and I've found it *much* faster than regular old X over ssh.

---

### Post by ryanhaigh on 2008-07-28
What you want to do is use the default VNC server that you can activate via System>Preferences>Remote Desktop Connection. Using putty (on windows or linux) and following these instructions makes it relatively simple. Just setup the port forwarding, establish the ssh connection and then start the vncviewer.

[https://help.ubuntu.com/community/VNCOverSSH#Windows%20clients](https://help.ubuntu.com/community/VNCOverSSH#Windows%20clients)

note: the cygwin instructions may work if you want to establish the connection without putty from within linux although I have never used that myself.

EDIT: by the way this will connect you to your current session rather than creating a new one

---

### Post by dmflad on 2008-07-30
I do the ssh -X <servername> thing all the time. To keep my ssh session separate I run it in one of the other "desktops". Usually I don't want the whole GUI of the box I'm ssh'ed into, just certain part like Oracle NetManager, so I haven't tried gnome-session.

---

### Post by geirha on 2008-07-30
You can also use XDMCP. On the remote machine you need to enable it from System -> Administration -> Login Window or run it from a terminal with "gksudo gdmsetup". Under the "Remote"-tab you enable remote login with a drop-down box. After that, restart gdm either by logging out to the login screen and hit Ctrl+Alt+Backspace, or by running ```
sudo /etc/init.d/gdm restart
``` (This will also restart any currently running xsessions.)

On the client side, you need to install [xnest](apt://xnest). And after that's installed, you can connect to the remote machine with Applications -> Internet -> Terminal Server Client. Choose XDMCP as the protocol.

---

### Post by bodhi.zazen on 2008-07-30
You can use Xephyr:

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

