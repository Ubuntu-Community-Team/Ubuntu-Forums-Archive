---
title: "Keyboard Shortcuts – why don't they work?"
date: 2008-08-08
forum: General Help
---

### Post by Rebelli0us on 2008-08-08
System > Preferences > Keyboard Shortcuts

Opens a shortcut configuration applet. Under Desktop there is “Suspend”. I assigned Ctrl+Alt+End to “Suspend” the computer, but it doesn't work.

How do keyboard shortcuts work?

---

### Post by silkstone on 2008-08-08
Do other keyboard shortcuts work?

If so, have you tried suspending by another method? It's possible that your machine doesn't want to suspend, rather than this being a problem with shortcuts.

---

### Post by Rebelli0us on 2008-08-08
thank you. Yes other shortcuts work and machine suspends S3 just fine. I tried different keys, even rebooted, but no luck.

---

### Post by silkstone on 2008-08-08
Mmmm... In that case I can't explain why that shortcut won't work, unless the instruction it generates is faulty. Have you tried another key combination?

Since other keyboard shortcuts do work, it's unlikely to be a general issue but perhaps specific to that instruction.

EDIT/ Sorry - you said you'd tried other key combinations - so I'm stumped.

---

### Post by jamesrl on 2008-08-25
Came out with roundabout fix, by custom creating a keyboard shortcut to a command that uses dbus-send to suspend the computer: [http://ubuntuforums.org/showpost.php?p=5663386&postcount=4]("http://ubuntuforums.org/showpost.php?p=5663386&postcount=4")

Basically you just, run gconf-editor, go to /apps/metacity/global_keybindings choose an unused run_command number (say run_command_9), set it to some custom value say <Control><Alt>End, then go to /apps/metacity/keybinding_commands/command_9/ and change the value to:
```
dbus-send --session --dest=org.freedesktop.PowerManagement --type=method_call /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.Suspend
```
and it should work.


**EDIT for 10.04:**  Elsewhere in the thread, the above version stopped working.  However, from [reddit]("http://www.reddit.com/r/Ubuntu/comments/cywiy/how_to_suspend_to_ram_using_the_commandline/") I saw a post at [commandlinefu.com]("http://www.commandlinefu.com/commands/view/6246/suspend-to-ram") with an updated command is:
```
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```
I still would rather recommend just giving your normal user password sudoers privileges to execute /etc/acpi/sleep.sh or /usr/sbin/pm-suspend as that seems less likely to change on subsequent upgrades.

---

### Post by Rebelli0us on 2009-01-31
Still not working, Keyboard Shortcuts is basic stuff! Any ideas?

---

### Post by Rebelli0us on 2009-08-05
OK then, in new version Jaunty 9.04 my "Suspend" shortcut (Ctrl+Alt+End) finally does something, but it doesn't suspend, it just blanks the screen! Then, with the next key-press it un-blanks the screen.

Is anybody using keyboard shortcuts successfully?

---

### Post by jamesrl on 2010-03-17
Finally upgraded to 9.10 (preparing to eventually upgrade to lucid) and the previous dbus command stopped working for me, and I couldn't find another dbus command to send.

So my current workaround involves granting me privileges to suspend via ```
sudo /etc/acpi/sleep.sh force
```
without using a password.
(Advice taken from here: [http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd](http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd))

If you are user name "jamesrl" on computer "jamesrl_computer", you can give that user permission to initiate sleep by editing the /etc/sudoers  (e.g., sudo nano /etc/sudoers ), and adding the following line at the end:

```

jamesrl jamesrl_computer = NOPASSWD: /etc/acpi/sleep.sh

```
If you don't know your computer's name, just go to a terminal and type 'hostname'.
Then go to System->Prefs->Shortcut Editor, and a custom shortcut with a command "sudo /etc/acpi/sleep.sh force", bind it to a key sequence (e.g., Ctrl-Alt-End for me) and you are done.

---

