---
title: "[SOLVED] Locking Thunderbird"
date: 2008-10-21
forum: General Help
---

### Post by jakupl on 2008-10-21
Is there a way to lock Thunderbird so that nobody can read your personal stuff?

My computer is positioned so that other people.. well one friend, uses it too. I have tried to make different users on ubuntu, but it is too much hassle, having to change user everytime the actual user changes.

I have activated the built in lock in Thunderbird, but all it does is preventing Thunderbird from accessing the server. All he needs to do is press the X in the password dialog four times, and he can read all my mail. (view attachments)

By the way, he does not know my root password, but I somehow do not like the idea of running Thunderbird as root.

Thanks in advance
jakupl

EDIT: After some more searching, I found this in the archive: [Thunderbird password question [Archive]]("http://ubuntuforums.org/archive/index.php/t-407078.html"). I will post if it works, but you are free to post any  suggestions. Thankyou

---

### Post by cicatrix1 on 2008-10-21
You can set a master password, which thunderbird will prompt you for before it opens.  If you get it right, it opens and mail is accessible.

Preferences -> Privacy -> Use master password

That is about the only way.

Switch user functionality doesn't take that long. . .

---

### Post by jakupl on 2008-10-21
> **cicatrix1 said:**
> You can set a master password, which thunderbird will prompt you for before it opens.  If you get it right, it opens and mail is accessible.

Preferences -> Privacy -> Use master password

That is about the only way.

Switch user functionality doesn't take that long. . .

I am allready using master password, but as demonstrated above, one only needs to exit the password promt four times to read my personal email.

Switching users is no problem for me, but for the other one... he is one lazy ******* ;)

---

### Post by jakupl on 2008-10-21
Buuuuuut booyah!

It worked beautifully. Just do this.

This is the segment relevant for me, as i only have one email profile on thunderbird.

I edited the link. The previous one was dead.

[QUOTE="RKCole"]Password Protecting Profiles
1) Click on this link ([http://nic-nac-project.de/~kaosmos/profilepassword-en.html#PPFF](http://nic-nac-project.de/~kaosmos/profilepassword-en.html#PPFF)) (This extension also works with profiles on SeaMonkey, Mozilla Suite, and Firefox, apparently)
2) DO NOT left-click on the Download link/button ( :) ). I learned a long time ago that you coudl directly install extensions in Firefox by left-clicking on the download button, but this does not work for installing extensions on Thunderbird. You must right-click on the Download link/button and use the option Save Link As... to save the link (extension) to your desktop or folder of choice.
3) Open Thunderbird (under your profile) and enter your password as you usually do.
4) Click on Tools->Extensions to open up the Extensions dialog box.
5) Click the Install button.
6) Navigate to wherever you saved the ProfilePassword extension (link) and double-click on it.
7) A dialog should open asking what you want to do. Click Install now to install the ProfilePassword extension.
8) Restart Thunderbird.
9) Click on Tools->ProfilePassword->Password manager to open the Password manager dialog.
10) Click on the Set/Change Password button.
11) Enter a password for your profile and confirm it.

NOTE: You do not have to have multiple profiles for this to work.

Now, when you open Thunderbird, you will be asked for the password to your profile. The password request box is the only thing that will show, and Thunderbird will not be displayed until the password is entered. You will then have to enter your account password as usual.

One precaution, however: If you open Thunderbird in Safe Mode, all extensions will be disabled, thus there will be no password protection for your profile. For normal home use, though, this method should work just fine.[/QUOTE]

stolen from [http://ubuntuforums.org/archive/index.php/t-407078.html](http://ubuntuforums.org/archive/index.php/t-407078.html)

---

### Post by cicatrix1 on 2008-10-21
Ah.  I was confused by what you meant with "built in lock". Makes sense now.  Glad you found something that works.

---

### Post by illpig on 2008-10-23
sweet!

---

### Post by geirha on 2008-10-23
Another possibility is to learn to lock the session whenever you leave the computer. I use Ctrl+Alt+l for this (and I think that is the default in the later Ubuntu relases). If your friend comes along and wants to use the computer, he has to log in with his own user.

---

### Post by malikkabanis on 2010-09-14
i installed it but it keep showing 

restart to complete installation..

i restarted Thunderbird many times.

i use ubuntu 10.04 32 bit - thunderbird 3.0.6

 and extentin name is here = profilepass-TB-RDF-0.7.13


plz help

---

