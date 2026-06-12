---
title: "Empathy: What is this &quot;default keyring&quot; it prompts me for?"
date: 2008-09-25
forum: General Help
---

### Post by Luke has no name on 2008-09-25
I typed in my password, my GPG key, etc. trying to unlock whatever this is. Could someone inform me?

Also, why can't Empathy function without accessing an external program to store passwords? What if I don't want it to store passwords? Why can't it do this on its own?

Help please, as I can't get this software to function correctly.

---

### Post by clopnaz on 2009-05-10
This is probably a dead subject, but I can't get it to act how I'd like it to in jaunty, either. I"m sick of typing in my password twice every time I log on or even come out of hibernate. Why does empathy have to bug me to start up when pidgin or xchat or skype do not?

---

### Post by forger on 2009-05-30
I think this is how you fix it:
System > Preferences > Encryption and Keyrings > PGP Passphrases
Remember passphrases for: "300" minutes

Check "Ask me before using a cached passphrase"
Check "Show icon in status area when passphrases are in memory"

---

### Post by mcduck on 2009-05-30
> **forger said:**
> I think this is how you fix it:
System > Preferences > Encryption and Keyrings > PGP Passphrases
Remember passphrases for: "300" minutes

Check "Ask me before using a cached passphrase"
Check "Show icon in status area when passphrases are in memory"
Unless you specificly tell the keyring mananger to only open a certain keyring for a limited time, the time limits are meaningless.

There are couple of things about the keyring manager you should know:

1. If you use login password the keyring will be unlocked automatically at login time as long as keyring password is the same as your login password. So you should never need to type two passwords when you log in.

2. If you enable automatic login, the keyring isn't automatically unlocked so you need to either type the keyring password, or set the keyring password to empty.

3. If you change your login password, you'll want to change your keyring password as well to keep the automatic keyring unlocking working.

To change your keyring password, or remove it, go to Applications/Accessories/Passwords and Encryption Keys. On the Passwords-tab right-click the "Passwords:login"-entry and select "Change Password".

(And the keyring manager is used to store passwords because it's simpler, easier and more secure to have one program to handle this tasks for all your programs. It also allows much better desktop integration (like the signing and encrypting options you have in your right-click menu, and the automatic keyring unlocking)

---

### Post by derekge on 2009-10-11
Thanks - this helped but the password I changed to empty was - Passwords:Default.  Then network manager didn't ask for a password anymore on boot up.

---

### Post by tempus on 2009-10-15
this may be a stupid question but what the f**k is a default keyring manager? how do i get rid of it?

---

### Post by aboud on 2009-11-04
> **forger said:**
> I think this is how you fix it:
System > Preferences > Encryption and Keyrings > PGP Passphrases
Remember passphrases for: "300" minutes

Check "Ask me before using a cached passphrase"
Check "Show icon in status area when passphrases are in memory"

There is nothing like Encryption or any Keyring in my Karmic Preferences >  menu, neither do search in the control panel for "Keyrings" give any result .

---

### Post by Peter09 on 2009-11-04
If the problem is that you are being asked for a password when connecting to a wireless network then - go to the wifi icon, right click and select edit, edit the connection that you want to change. Tick the - share this connection option and save.

---

### Post by komputes on 2009-12-21
I can confirm this as well. I was never requested to create a protected keychain when first using epiphany or networkmanager and yet every time I start epiphany I get a request for the default keyring password (which is not blank, but my user password). How did that happen?

:confused:

---

