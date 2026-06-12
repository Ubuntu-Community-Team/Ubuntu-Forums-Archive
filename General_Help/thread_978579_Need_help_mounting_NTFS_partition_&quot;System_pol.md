---
title: "Need help mounting NTFS partition &quot;System policy prevents mounting internal media&quot;"
date: 2008-11-11
forum: General Help
---

### Post by Calculon64 on 2008-11-11
Hi all and thank you for taking the time to read my post and help figure out my problem.

I have dual boot on my laptop Ubuntu 8.10 64-bit & Vista Ultimate 64-bit.  I also created 3rd partition (NTFS) for storage so that way I can have easy straight access to my music, movies, documents from both OS.

Partition 1: Ubuntu 8.10 64-bit
Partition 2: Windows Vista Ultimate 64-bit
Partition 3: Storage for both OS

From Ubuntu I can see Vista's partition and the 3rd partition for storage I created.  The problem is that is asking me for a password.  When I created this partition I didn't put any passwords or restrictions.

I get the message: 

"System policy prevents mounting internal media" 

Then in same box ask for password.

---

### Post by yota on 2008-11-11
As the message says, the default system policy prevents standard users from mounting internal hard drives, and requires an admin user password to proceed with the operation.

Either insert your password in the dialog or change the policy (property org.freedesktop.hal.storage.mount-fixed under the hal/storage branch) in System/Administration/Authorizations.

[IMG]http://www.alessandrocarichini.it/images/p.it/ubuntu_804/polkit.jpg[/IMG]

Hope this helps!

p.s. the image shows the tool, but not the correct branch of the tree!

---

### Post by Calculon64 on 2008-11-11
> **yota said:**
> As the message says, the default system policy prevents standard users from mounting internal hard drives, and requires an admin user password to proceed with the operation.

Either insert your password in the dialog or change the policy (property org.freedesktop.hal.storage.mount-fixed under the hal/storage branch) in System/Administration/Authorizations.

[IMG]http://www.alessandrocarichini.it/images/p.it/ubuntu_804/polkit.jpg[/IMG]

Hope this helps!

p.s. the image shows the tool, but not the correct branch of the tree!


Hello again and thank you so much for helping me with this.

One more thing.

Under: "Implicit Authorizations" it says.

**Anyone: No (Default)**  [COLOR="DarkRed"]<--On my first try I put "Yes" here and the rest I left "No" and didn't work. (I though it was enough")[/COLOR]

**Console: No (Default)**

**Active Console: No (Default)**

[COLOR="Green"]But then I put "Yes" to all 3 options then it worked.  Am I in risk of an attack by setting all 3 to "Yes"?  I don't want to put password every time either.[/COLOR]

Also can you explain what each of the 3 options mean? [COLOR="Navy"](Specially "Console & Active Console")[/COLOR]

---

### Post by yota on 2008-11-12
Hi Calculon,

I'm glad that it worked, probably the setting you need is just "Active console", and honoring the least privilege principle you should let other to "No". Anyway the risk wouldn't be overkill because an attacker should still have an account on your computer before being subject to policies.

The difference between "console" and "active console" is that, in a multiuser environment with more than user logged on at the same time, the "active" console is the one that you can see on the local display.
Probably (but I'm not completely sure) anyone should be read as "anyone else".

---

### Post by bob23450 on 2008-12-15
Hi

Can someone point me please where to change these properties in Kubuntu Hardy (KDE 3.5) :confused: ?

Thank you all.

---

### Post by bob23450 on 2008-12-17
> **bob23450 said:**
> Hi

Can someone point me please where to change these properties in Kubuntu Hardy (KDE 3.5) :confused: ?

Thank you all.

I'll answer myself...

I found no GUI to do that in KDE, nevertheless the same result can be achieved at least in one of two ways:
1)Install the package 'policykit-gnome' and all its dependencies, run (Alt-F2) '/usr/bin/polkit-gnome-authorization' and follow yota's post
2)Use the command line and type 'polkit-action --set-defaults-active org.freedesktop.hal.storage.mount-fixed yes'

In both cases, a file named 'org.freedesktop.hal.storage.mount-fixed.override' and containing the string 'no:no:yes' is created in the folder /var/lib/PolicyKit-public and this does the magic.

I hope it can help someone.
Bye

---

### Post by Bearly Able on 2009-06-07
Thanks, Yota - worked for me, too. I'd looked under "Authorizations", but I'd never have found the right entry on my own.

---

### Post by Dark Theli on 2009-06-26
Hi Fellas,

I use Ubuntu 9.04 AMD64

I`m getting the same message "System policy prevents.." for mounting partitions or installing new software

I remember when system prompted me to put the password I just used my user password and I was able to mount any partition or install.

The issue that I have now. I have an Nvidia card and it needs the accelerated graphics driver version 180 for render 3D.

Since my password does not work I don know what to do.

Please any help:confused:

PS:my sudo password works, password for synaptic works, password for my session works too except the one for "System policy prevents.." 

Thanks,

---

