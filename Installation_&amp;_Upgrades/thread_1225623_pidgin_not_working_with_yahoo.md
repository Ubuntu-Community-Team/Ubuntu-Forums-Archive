---
title: "pidgin not working with yahoo"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by stlsaint on 2009-07-28
hey, im not the  most experienced but im not a total newbie...so heres my issue! i cant see any of my contacts when i set up pidgin instant messenger with yahoo. i load the profile correctly but when i sign in i see absolutely nothing on the screen...its all white saying that im available but with no contacts!!! please help!!!!

---

### Post by spcwingo on 2009-07-28
(First see edit at bottom)

Have you upgraded to Pidgin 2.5.8?  If not, that version fixes most problems with Yahoo.  You can download and install Pidgin from their site ([[COLOR="Red"]here[/COLOR]]("http://www.pidgin.im")) or from their PPA.  To add the PPA to your sources list just copy/paste this:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXXu9wEEAM2fOLi65x7hpnmDhTelWDSz+2ktpBuaBizVnVrS5clEVW5BfvQQbqzF1rur
gxTf+0y54s+ZIDOX1OIpiaZK9RYIxWq9KuF2urwv4qK3e0AeWYU6b44YPjgFhQ/LEq0QCTuN
/fKpIenTov9P2O66t9d5cQfiAtTB0NogMLiAjXOBABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IFBpZGdpbiBEZXZlbG9wZXJziEYEEhECAAYFAknOAzkACgkQbfU6uV4fG84AJgCgudiLwQbD
+Kur+VdVc8GVMKu15XYAoKzf06cdX4l+RnfTHJ6hj5TQlY9MiLYEEwECACAFAkl17vcCGwMG
CwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRB/uL7gofGWqIi6A/9jDrYXq2wgFjQkCFGH+Nxd
IbGs1O4OKs+AMe2UiN5YVkQu9XOYoaYaxwNe0WnFJhf4cxPChkWYk16GVMchnDWppVUaUGh4
ojmbY4Gi7VnwC0AiMbtZgnJN9NTZ5W2IhmHJKKkFSZcdbcjNr0YL/8XusbTw4Zeb7214G77z
8qj9/Q==
=CKTU
-----END PGP PUBLIC KEY BLOCK-----
```

into your text editor and save as pidgin.gpg to your home directory.  Next press ALT+F2 and enter this command:

```
gksu gedit /etc/apt/sources.list
```

At the bottom of that file add this:

```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main
```

If you're not on Hardy replace with your distribution (ie: Intrepid, Jaunty, etc).  After that open a terminal and enter this:

```
sudo apt-key add ./pidgin.gpg && sudo apt-get update && sudo apt-get upgrade
```

This should upgrade Pidgin to the newest version.  Just to let you know, the PPA route is the preferred way to do this.  The reason is you add the Pidgin repository to your apt sources list.  That way whenever there's a new version you're automatically notified and you can use update manager to install.

Let us know how it turns out for you.

EDIT:  I just thought of something else.  If you don't have Pidgin set to display offline buddies and all of your contacts are offline, you won't see any of your contacts.  To see if this is the case open Pidgin and go to buddies>show>offline buddies.  If that doesn't work, you might have to upgrade Pidgin as I outlined above.

---

### Post by stlsaint on 2009-07-28
tried that and still having the same issues...can setup account but see NONE of my friends/contacts for IM and I HAVE ALOT ON MY MESSENGER LIST!

---

### Post by spcwingo on 2009-07-29
> **stlsaint said:**
> tried that and still having the same issues...can setup account but see NONE of my friends/contacts for IM and I HAVE ALOT ON MY MESSENGER LIST!

When you say that you have "tried that", what exactly have you tried?  Everything that I have listed, or just the part about showing offline buddies?  The reason I ask is this:  Yahoo recently updated their servers.  The new updates included a newer protocol/login method that the older versions of Pidgin doesn't support.  Your contacts are pulled in from the Yahoo servers...see where I'm going with this?

---

### Post by stlsaint on 2009-07-29
tried that commands you have given and gone to site you posted. In my repos..it still shows old pidgin so maybe im missing something?

---

### Post by spcwingo on 2009-07-29
Please, post the output of these commands:

```
cat /etc/apt/sources.list
```

and

```
sudo apt-key list
```

finally

```
lsb_release -a
```

---

### Post by stlsaint on 2009-07-29
you are my new best friend...i re-did everything you posted originally after removing pidgin and re-adding and now i see all my contacts and im now talking away!! its people like you that make me happy to be with ubuntu!! thanks for all your help!!

---

### Post by spcwingo on 2009-07-29
I'm just glad to give you a hand.  Have fun.  :)

---

### Post by Warren Watts on 2009-07-29
Three cheers for the Ubuntu Community!  

=D> =D> =D>

---

