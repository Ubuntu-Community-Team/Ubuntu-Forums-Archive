---
title: "rdesktop - ignore certain key combinations"
date: 2008-10-21
forum: General Help
---

### Post by prjorgen on 2008-10-21
I have a laptop set up with Ubnutu Hardy running compiz with the desktop cube enabled. I have the cube set to rotate via CTRL-ALT-left and CTRL-ALT-right. I also have two windows workstations I need to use for work and I love some of the possibilities of rdesktop.

Currently, the command line I use to connect is this:

rdesktop -K -D -f -u <user> -d <domain> -p <password> -a 16bpp <ip of workstation>

This is almost perfect for my needs except for one thing -- Alt-Tab (which I use very heavily) gets passed back to X not to the local workstation. Currently to work around this, I am using CTRL-Tab in Gnome to switch apps but I'd really like to keep it at alt-tab if I can.

I know that if I take the -K switch out, I can use alt-tab and other reserved key combinations on the remote desktop, but then what I can't do is use ctrl-alt-left and right to move between desktops (I love having both workstations connected and then still having two open desktops for ubuntu apps!)

My question is this: is there a way to only reserve ctrl-alt-left and ctrl-alt-right within rdesktop but continue to pass every other key combination to the remote operating system when the window has focus? Or do I need to continue with my current workaround of re-mapping my local keyboard shortcuts so that they are not the same as the unchangeable windows shortcuts?

---

### Post by prjorgen on 2008-10-28
Is this just an impossible request? I've been all over google looking for something similar and the closest thing I've found is the ability to remap keys but not to selectively reserve keys. I'd appreciate any thoughts that anyone has.

---

### Post by Ciantic on 2009-03-31
> **prjorgen said:**
> Is this just an impossible request? I've been all over google looking for something similar and the closest thing I've found is the ability to remap keys but not to selectively reserve keys. I'd appreciate any thoughts that anyone has.

Any thoughts now? I've been looking for similar thing for **a long time** too.

I'd like to ideally ignore Win+1,2,3,4, and alt+ctrl-left, alt+ctrl-right from rdesktop, rest should work like they do in remote.

I find the -K switch weird, it doesn't explicitly tell how it knows which are wmbindings and which aren't... Maybe we should fork rdesktop directly?

---

### Post by sunner_sun on 2009-10-16
Hi, all

I made a rdesktop patch for this problem. You can download the binary file and source [here]("http://blog.sunner.cn/2009/10/rdesktop-patch-switch-local-workspaces-and-windows-by-local-hot-keys/"). If you have any suggests, let me know.

Details:

[LIST]
[*]Double press Ctrl+Alt+Left or Ctrl+Alt+Right to switch local active workspaces.
[*]Double press Ctrl+Alt+Tab to switch local active window.
[*]Other hot keys are sent directly to remote machine.
[*]If rdesktop is running in fullscreen mode (-f), Ctrl+Alt+Left/Right/Tab will toggle it to window mode first. After switching back, it can NOT toggle to fullscreen automatically. Press Ctrl+Alt+Enter to do that. (I know this is boring. But it is the best I can do. Rdesktop use override_redirect to implement fullscreen which makes it always the top-most window no matter which workspace/window you have switched to)
[/LIST]

---

### Post by computercolin on 2009-11-06
@sunner_sun Great patch, I totally appreciate it. A winner, in my opinion. I don't know what the status is of adding this to the rdesktop sources, but if you can, I would love to see your modifications included.

---

