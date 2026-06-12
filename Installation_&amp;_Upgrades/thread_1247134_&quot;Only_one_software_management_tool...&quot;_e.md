---
title: "&quot;Only one software management tool...&quot; error"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by Aldentron on 2009-08-22
I just got my new laptop today and it runs Ubuntu, so I am very new to this OS.  I am trying to install the Adobe Flash Player 10, i downloaded the .deb file and saved it to my desktop. upon trying to install it with Package Installer, i get an error message that says "Only one software management tool is allowed to run at the same time, please close other application e.g. 'Update Manager,' 'aptitude' or 'Synaptic' first."
i am not running any of these applications and do not know how to close them, if they are indeed running.  please help?

---

### Post by stlsaint on 2009-08-22
do a reboot and when you get to your desktop dont open anything except add/remove or synaptic and try again!!

---

### Post by Aldentron on 2009-08-22
add/remove does not have flash player, and when i run synaptic it gives me an error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by 0faber on 2009-08-22
Flash Player 10 from Adobe has it's own installer. You probably need to do this over. Down load it. Select "save" -- not the default "install..." Close Firefox (it can't install the plug-in while it's running. Then double click the Flash-Player box icon on your desktop. It should install from there. 

If that's what you just did, forgive me.

Since you're new, I'll add: This not the usual way to install software in Ubuntu. Most of what you need will be in the Ubuntu repositories, and you can get it through "Add Remove" under "Applications" or "Synaptic Package Manager" under "System > Administration." But in this case, the version of Flash in the repositories isn't current, so you really do have to get it directly from Adobe's website (and go through some extra riggamaroll you usually don't have to bother with).

Hope this helps.

---

### Post by Aldentron on 2009-08-22
Well I am glad you told me about the repositories, but I was doing that procedure in the first place.

---

### Post by K.Y.A on 2009-08-22
Open a terminal... 
Applications >> Accessories >> Terminal.

Copy/paste the following into the box:

```
killall dpkg
```

And press enter. Then try again...

I haven't had this issue in years! :P

---

### Post by Aldentron on 2009-08-22
I got "dpkg: no process killed" message.

---

### Post by Chronon on 2009-08-22
> **Aldentron said:**
> add/remove does not have flash player, and when i run synaptic it gives me an error "E: dpkg was interrupted, **you must manually run 'dpkg --configure -a' to correct the problem.** 
E: _cache->open() failed, please report."

Did you try that?

---

### Post by stlsaint on 2009-08-22
what version of ubuntu  are u on?

---

### Post by lisati on 2009-08-22
> **Aldentron said:**
> add/remove does not have flash player, and when i run synaptic it gives me an error [COLOR="Red"]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR] 
E: _cache->open() failed, please report."

> **Chronon said:**
> Did you try that?

I noticed the message too.

Open up a terminal (Applications->Accessories->Terminal) and type in; ```
sudo dpkg --configure -a
```
Type in your password when asked - it won't show, this is normal - and let us know how you get on.

---

### Post by Aldentron on 2009-08-22
> **lisati said:**
> I noticed the message too.

Open up a terminal (Applications->Accessories->Terminal) and type in; ```
sudo dpkg --configure -a
```Type in your password when asked - it won't show, this is normal - and let us know how you get on.


This seemed to fix the problem, I ran the installation again and it worked this time. Thank you very much!

For future reference, whenever an error asks me to run a command manually, will I need to enter "sudo" before the command in the Terminal?

---

### Post by oldrocker99 on 2009-08-22
> **stlsaint said:**
> TOP TEN REASONS NOT TO USE UBUNTU!!!


Ho ho he he haw haw giggle giggle ROTFL ROTLF!

:guitar:

---

### Post by prakashkumar on 2010-01-23
use this ,it worked for me

prakash@prakash-laptop:~$ sudo dpkg --configure -a
[sudo] password for prakash: 
Setting up libdvbpsi5 (0.1.6-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
prakash@prakash-laptop:~$ 

now it will work good

---

