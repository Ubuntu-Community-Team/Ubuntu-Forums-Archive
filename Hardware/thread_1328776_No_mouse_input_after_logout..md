---
title: "No mouse input after logout."
date: 2009-11-16
forum: Hardware
---

### Post by Wander_Free_Forever on 2009-11-16
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

I have found a rather worrying problem!

After I log out of my Ubuntu account I can no longer use my mouse! This
forces me to to do a hard restart.

[http://www.youtube.com/watch?v=KhzyaqCmwsI&fmt=18](http://www.youtube.com/watch?v=KhzyaqCmwsI&fmt=18)

My log files can be downloaded from the link below.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLAfHyzH0f+AFrIBkRCGNAAP4uT6xqnrfwP8sB8De9N5SRmLrYrnV8kBgK
LksWrO1ZlwEA3e15IeNaL70I9P2qRe+nxdidot1oZEbWBvjmFIR2hrM=
=nbLk
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-17
> **Wander_Free_Forever said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

I have found a rather worrying problem!

After I log out of my Ubuntu account I can no longer use my mouse! This
forces me to to do a hard restart.

[http://www.youtube.com/watch?v=KhzyaqCmwsI&fmt=18](http://www.youtube.com/watch?v=KhzyaqCmwsI&fmt=18)

My log files can be downloaded from the link below.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLAfHyzH0f+AFrIBkRCGNAAP4uT6xqnrfwP8sB8De9N5SRmLrYrnV8kBgK
LksWrO1ZlwEA3e15IeNaL70I9P2qRe+nxdidot1oZEbWBvjmFIR2hrM=
=nbLk
-----END PGP SIGNATURE-----

For now, you could try CTRL+ALT+F2 after you log out, typing in "sudo /etc/init.d/gdm restart" and pressing enter.

I'll take a look at your log files. Have any previous versions of Ubuntu been installed on the same computer? Did this work under those versions?

Thanks.

EDIT: This is a virtual machine in VMWare, right? If so, try going to a terminal and typing in "sudo apt-get install xserver-xorg-input-vmmouse" and pressing enter.

---

### Post by Wander_Free_Forever on 2009-11-18
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Yeah, I already have vmtools installed. This includes the appropriate
drivers. However, quite a bit of my hardware is not working. This includes
both physical and virtual hardware. Case in point my keyboard!

[http://www.youtube.com/watch?v=1yRTuPqSzLg&fmt=18](http://www.youtube.com/watch?v=1yRTuPqSzLg&fmt=18)

I have no mouse or keyboard functionality after log out. Seriously, I am
unable to debug from log out! The real shocker is that this is a fresh
install!

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLA4vuzH0f+AFrIBkRCBHcAP9AhJUNSAH+pjicdH8p3WSZrjXlcQcoZTiw
9kFQ/4mGpwEA5PILYN1NC9VJNLz3LCcvnfrVRQGVmywrZq02ViF8y7o=
=E2a8
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-18
> **Wander_Free_Forever said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Yeah, I already have vmtools installed. This includes the appropriate
drivers. However, quite a bit of my hardware is not working. This includes
both physical and virtual hardware. Case in point my keyboard!

[http://www.youtube.com/watch?v=1yRTuPqSzLg&fmt=18](http://www.youtube.com/watch?v=1yRTuPqSzLg&fmt=18)

I have no mouse or keyboard functionality after log out. Seriously, I am
unable to debug from log out! The real shocker is that this is a fresh
install!

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLA4vuzH0f+AFrIBkRCBHcAP9AhJUNSAH+pjicdH8p3WSZrjXlcQcoZTiw
9kFQ/4mGpwEA5PILYN1NC9VJNLz3LCcvnfrVRQGVmywrZq02ViF8y7o=
=E2a8
-----END PGP SIGNATURE-----

I'll take a look into vmware problems then. What is the host OS? Also, what version of vmware and vmware tools are you using?

Thanks.

---

### Post by Wander_Free_Forever on 2009-11-18
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Workstation build 7.0.0 build-203739

Guest OS Windows XP Professional 5.1.2600, Service Pack 3

The Ubuntu VM is my only VM that has had these problems.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLBEBIzH0f+AFrIBkRCMSxAP9dETBYMXCOOAQAsTSsW4kXrX4XjWCue9NM
78dbVal3mwEA30iyVS4VbaAU2JpsXRPNC/a/uQ8pn4cWTPJHF+v0X/U=
=nOxT
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-18
> **Wander_Free_Forever said:**
> The Ubuntu VM is my only VM that has had these problems.

Do you have any other Linux VMs? Could you send log files from one of those with you logging out?

EDIT: Keep in mind that Ubuntu 9.10 is an unsupported platform. It would appear that you're not the only one having mouse problems. Take a look [at this thread]("http://communities.vmware.com/message/1272508"), which contains a potential fix in the form of a script. If you need help trying this, please feel free to ask.

At any rate, I'll continue my search for more information.

EDIT 2: You might also wish to take a look at [this]("http://communities.vmware.com/thread/208507"). It would appear that mouse problems are common. Keep in mind that real and "virtual" hardware are two different animals, and that this is likely a problem with VMWare Tools on Ubuntu.

---

### Post by Wander_Free_Forever on 2009-11-19
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Well this seems to be a problem; I have different problems than those
posted on the VMforums. Heck eve a different host operating system that one
of those threads!  Just for note, I will post my problem on the VMforums as
well. I really do not understand why this is happening, if VMtools were so
incompatible how did the auto install pass? How was I able to run
‘vmware-toolbox &’ in a terminal without reconfiguring for Ubuntu 9.10
kernel?

The other Linux VM I have is OpenSUSE 11.2 that is using KDE. That has
OpenVMtools installed on it. Being that they are different that the VMtools
that come with Workstation, don’t ask me why, I fail to see what can be
gained. But the logs are attached below.


-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLBOpnzH0f+AFrIBkRCOZpAQDi0KZ/IdLesPUOVWC+4gx89ljRZLubWR/I
i8qkHOM8jwEA7tTaXEuTz/t4Surli1cYXhmHUVJcikU3HsNN/bp06wA=
=Apit
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-19
> **Wander_Free_Forever said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Well this seems to be a problem; I have different problems than those
posted on the VMforums. Heck eve a different host operating system that one
of those threads!  Just for note, I will post my problem on the VMforums as
well. I really do not understand why this is happening, if VMtools were so
incompatible how did the auto install pass? How was I able to run
‘vmware-toolbox &’ in a terminal without reconfiguring for Ubuntu 9.10
kernel?

The other Linux VM I have is OpenSUSE 11.2 that is using KDE. That has
OpenVMtools installed on it. Being that they are different that the VMtools
that come with Workstation, don’t ask me why, I fail to see what can be
gained. But the logs are attached below.


-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLBOpnzH0f+AFrIBkRCOZpAQDi0KZ/IdLesPUOVWC+4gx89ljRZLubWR/I
i8qkHOM8jwEA7tTaXEuTz/t4Surli1cYXhmHUVJcikU3HsNN/bp06wA=
=Apit
-----END PGP SIGNATURE-----

Since they are different tools, you are correct in saying that they wouldn't help.

I understand that the mouse problem(s) listed in that thread are different. However, [the script in the second link]("http://communities.vmware.com/thread/208507") may yet help, even if it was originally for 9.04. You may wish to back up your VM image should you decide to try this.

As far as the incompatibility part: it's not that it's "incompatible" it's simply that things change from release to release, and the installer simply installs everything as it was designed to do. It won't fail to work, but it still doesn't produce the desired result. That script is designed to overcome this. Whether or not it will fix your problem, however, is unsure.

Hope this helps.

---

### Post by Wander_Free_Forever on 2009-11-19
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Well that really sort of fixed some stuff and broke the rest. The good news
is that the mouse works, the bad news is that file and text transfer no
longer works. Wow, half working VMtools either way. I was able to get the
logs output by the script by a file-hosting service over the internet.

[http://www.youtube.com/watch?v=INPxz8rokL4&fmt=18](http://www.youtube.com/watch?v=INPxz8rokL4&fmt=18)

It would seem that I am out of options here. Whoops, I forgot to mention
that I have dependent snapshots, so I was able to restore the VM to a good
state.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLBfpEzH0f+AFrIBkRCF2YAP0aShGCPcGZPk0TaIE7X1h0PQbtxwyHCwmW
IVp9uIIafQD+JqR8IAELOMGvpgUjHUbQCVL+I9DPALP+gZPguCX577E=
=I14f
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-19
Another idea: edit your /etc/X11/xorg.conf, changing the mouse driver from "vmmouse" to simply "mouse".

---

### Post by Wander_Free_Forever on 2009-11-20
> **Jon Monreal said:**
> Another idea: edit your /etc/X11/xorg.conf, changing the mouse driver from &quot;vmmouse&quot; to simply &quot;mouse&quot;.


-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Well it would seem that Xorg.conf was missing form that directory, so I
performed a search and found a copy in an archive. I extracted that
xorg.conf and made a modification.

[http://www.youtube.com/watch?v=af6otgxUCGc&fmt=18](http://www.youtube.com/watch?v=af6otgxUCGc&fmt=18)

If this is a system critical file why is it missing?

Wait that fix killed Xserver, damit.

[http://www.youtube.com/watch?v=SMoNzd9gK5A&fmt=18](http://www.youtube.com/watch?v=SMoNzd9gK5A&fmt=18)

Seriously, this sucks.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLBu8LzH0f+AFrIBkRCMQIAQCkjwOFqyZIx/c4/I/5sCKGR2uCTIR0NYXz
ojZlI9KsdQEA0YB20gNSlHOhHcjjua8JFwphNlh/YWtl3RF0pbMayoE=
=t3sW
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-20
It need not be present in 9.10.

Instead of copying the entire thing over, just copy the appropriate bit for the mouse driver and change that. This should work better.

---

### Post by Wander_Free_Forever on 2009-11-22
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

I just finished calling Dr. Quack, it would seem that an unorthodox
solution fixed this. I had taken your advice and modified org.conf only the
xorg.conf in an archive located in '/usr/share/man/man5' instead of
'/ect/x11'.

[http://www.youtube.com/watch?v=IRVY2gxKH44&fmt=18](http://www.youtube.com/watch?v=IRVY2gxKH44&fmt=18)

I am happy to report that everything is working! And when I updated no
functionality was lost!

[http://www.youtube.com/watch?v=7thHRiHwDjU&fmt=18](http://www.youtube.com/watch?v=7thHRiHwDjU&fmt=18)

I was just as shoked as he was! Thank you for all of your efforts.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFLCgcvzH0f+AFrIBkRCHWnAQDp7hLyYkejK3t/N3qOqC6cF5qG9f02NBud
fsqo2jMkNgD/TcYVZx+xXkE9/HS8b/rHW1qERnSmBfAoMn0d+EdkNKg=
=PIVw
-----END PGP SIGNATURE-----

---

### Post by Jon Monreal on 2009-11-22
It's no problem.

Could you mark this thread solved for future reference? (Thread Tools -> Mark Thread As Solved).

Thanks.

---

