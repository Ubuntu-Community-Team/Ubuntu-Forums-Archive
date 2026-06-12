---
title: "Xdmcp"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-05-22
A few minutes ago, I finished installing Ubuntu on a remote desktop.
Just walked back to my desk.

On that remote Ubuntu desktop, I would like to turn on the XDMCP feature.

If I was sitting at that remote Ubuntu desktop, I would make the following change:
**[COLOR="Blue"]System-->Administration-->Login Window-->Remote-->Style:Same as Local[/COLOR]**

But I am not sitting at the remote Ubuntu desktop.
I only have SSH access to the remote Ubuntu desktop.
So how do I make the same change from the command line?

---

### Post by asmoore82 on 2009-05-22
SSH can provide X tunneling for individual Apps with the ``-X'' switch

```
**me@local ~$** ssh **-X** *<remote_admin_user>*@*<remote_machine>*
**me@remote ~$** sudo echo
**me@remote ~$** gksudo gdmsetup
```
^^the `sudo echo` is just to temporarily store sudo authentication -
gksudo can be dog slow over X tunneling :biggrin:

---

### Post by boondocks on 2009-05-23
asmoore82, Thanks for the response.

That helped.  I am able to run gdmsetup on the remote system now.

---

### Post by boondocks on 2009-05-23
Yes, it is dog slow.  
So instead of running the full gdm, I was trying to run specific admin apps like "users-admin".

But regardless of
"gksudo users-admin"
or
"sudo users-admin"


I can get the Users Settings window but the Unlock button is gray.
So I cannot edit any user settings.
I have root access on this remote system.

So how do I get the Unlock button to not be gray.

(I walked back to the remote system and login via gdm.
Then I typed "users-admin" and it works.)

---

### Post by asmoore82 on 2009-05-23
for Apps that have Policy Kit integrated(the "Unlock" button),
you'll actually want to run them as your plain user account without gksudo

and yet for other Apps such as `gdmsetup` you need the gksudo ...
It's a bit of a strange Duopoly at this point in its evolution.

---

### Post by boondocks on 2009-05-23
I tried that...

```
users-admin

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(users-admin:17942): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

```I get the Users Settings window.
It does not ask for the admin password and the Unlock button is still gray.
And when I hover the mouse over the "unlock" button, it says:
"This action is not allowed"

---

### Post by asmoore82 on 2009-05-23
D'oh!! I forgot that Policy Kit also assumes by default that certain Admin actions
should only be grant-able on local login.

You could tweak these settings at "System -> Administration -> Authorizations"

---

### Post by boondocks on 2009-05-28
> **asmoore82 said:**
> You could tweak these settings at "System -> Administration -> Authorizations"

I am looking at the Authorizations screen.

policykit
[LIST]
[*]Revoke authorizations from other users
[*]Read authorizations of other users
[*]Modify defaults for implicit authorizations
[*]Grant authorizations to other users
[/LIST]
It is not clear to me which/how these option(s) would allow me (the Admin) to access XDmcp from a remote system.
Could you please give me some direction here?

---

