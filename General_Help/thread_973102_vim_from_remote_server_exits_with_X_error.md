---
title: "vim from remote server exits with X error"
date: 2008-11-06
forum: General Help
---

### Post by zzdrumzz on 2008-11-06
After upgrading to 8.10 server, when I run vim -V -g from a remote box with the display set to the ubuntu server, I get this error from vim as soon as I hit any key:


edgar:root:3005:/:# X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  151 (XKEYBOARD)
  Minor opcode of failed request:  16 (XkbSetNamedIndicator)
  Serial number of failed request:  14865
  Current serial number in output stream:  14882

Here's what I've tried to no avail:
regenerating the xorg.conf file with:
sudo dpkg-reconfigure -phigh xserver-xorg

putting the InputDevice section back in the xorg.conf and in the ServerLayout section

I can use other X programs from the remote server using the ubuntu server display with no problems. It seems to only be affecting vim.

---

### Post by C-- on 2008-11-07
As you can see from the following thread (no solution yet): 

[http://ubuntuforums.org/showthread.php?t=972646&highlight=BadAlloc](http://ubuntuforums.org/showthread.php?t=972646&highlight=BadAlloc) 

I am also having the exact same problem when I try to use emacs or gedit in a GUI window (I can't use vim in a GUI, it isn't enabled at compile time for me). I am not sure what is causing the problem.

One question: if you run "sudo dpkg-reconfigure fontonfig" do you get an error like: 

"Fontconfig error: "/etc/fonts/conf.d/30-defoma.conf", line 6: not well-formed (invalid token)?" 

I believe the X server can throw exceptions when your fonts are screwed up, and I am suspecting that this might be the problem for me as both this error and the crashing remote GUI occurred when I upgraded to Intrepid.

---

### Post by zzdrumzz on 2008-11-10
I ran the dpkg-reconfigure and had no errors. After running it, I still have the same error when using vim remotely.

I'm thinking it has to be related to the keyboard or keymapping, because I can use the vim menus with the mouse & open/close files, but as soon as I hit any key (even the shift key), vim aborts with the error.

---

