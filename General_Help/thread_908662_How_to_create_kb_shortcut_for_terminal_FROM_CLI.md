---
title: "How to create kb shortcut for terminal FROM CLI???"
date: 2008-09-02
forum: General Help
---

### Post by j.e.ludovico on 2008-09-02
Hi,

I need to launch terminal blindly while in GUI session.

I f**kd my GNOME screen res. 

I think that if I can launch terminal while in GUI session I can type blindly xrandr -s 0 and get displayable resolution. But unfortunately I had not previously set keyboard shortcut for launching terminal.

So how do i create a gnome keyboard shortcut from cli? What file should i edit using vi?

xorg.conf is fine and my other use account works but gnome screen resolution for by other account is wrong and i need to change it.

---

### Post by j.e.ludovico on 2008-09-02
> **j.e.ludovico said:**
> Hi,

I need to launch terminal blindly while in GUI session.

I f**kd my GNOME screen res. 

I think that if I can launch terminal while in GUI session I can type blindly xrandr -s 0 and get displayable resolution. But unfortunately I had not previously set keyboard shortcut for launching terminal.

So how do i create a gnome keyboard shortcut from cli? What file should i edit using vi?

xorg.conf is fine and my other use account works but gnome screen resolution for by other account is wrong and i need to change it.

In 7.04 I did:

gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal -t string "<Control><Alt>x"

for control+alt+x

---

