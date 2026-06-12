---
title: "[SOLVED] Nautilus not FTP'ing - only certain IP's.."
date: 2008-08-18
forum: General Help
---

### Post by Syndacate on 2008-08-18
Hey,

I use nautilus as a method of an FTP client for awhile, by just plugging it into the path ([ftp://UN@Server:](ftp://UN@Server:)[port])

So here's the thing, both me 'n my friend have FTP servers on, on  our macs - now before you start saying "oh, it's because it's a mac" - let me give you the low-down, because I think the issue is on my end.

A)  I can connect to my mac's FTP (via my router) by both nautilus, and terminal FTP
B)  I can connect to her mac's FTP server in terminal, but NOT in nautilus (it just hangs after I type the password)
C)  I can connect to her mac fine using an FTP client in Windows, or default FTP connection in OS X from my  mac.

The problem seems to be ONLY when nautilus tries to connect to it...which is fine, I'd say normally, if I didn't connect to it 1000 times in the past, and still connect to my own server without problems just fine.

It seems that ONLY nautilus won't connect, to ONLY her IP.

Any ideas what in the hell is wrong?  Everything else works fine.  I can use terminal for now...but this is just straight up weird...and I've never had a prob with nautilus on my own server...

---

### Post by Syndacate on 2008-08-24
> **Syndacate said:**
> Hey,

I use nautilus as a method of an FTP client for awhile, by just plugging it into the path ([ftp://UN@Server:](ftp://UN@Server:)[port])

So here's the thing, both me 'n my friend have FTP servers on, on  our macs - now before you start saying "oh, it's because it's a mac" - let me give you the low-down, because I think the issue is on my end.

A)  I can connect to my mac's FTP (via my router) by both nautilus, and terminal FTP
B)  I can connect to her mac's FTP server in terminal, but NOT in nautilus (it just hangs after I type the password)
C)  I can connect to her mac fine using an FTP client in Windows, or default FTP connection in OS X from my  mac.

The problem seems to be ONLY when nautilus tries to connect to it...which is fine, I'd say normally, if I didn't connect to it 1000 times in the past, and still connect to my own server without problems just fine.

It seems that ONLY nautilus won't connect, to ONLY her IP.

Any ideas what in the hell is wrong?  Everything else works fine.  I can use terminal for now...but this is just straight up weird...and I've never had a prob with nautilus on my own server...

Bump?

Anybody?

Can anybody recommend a stable, solid, easy to use FTP program in the repos then?

---

### Post by cariboo on 2008-08-24
You can give gftp or filezilla a try, both are available in the repositories, You can use Add/Remoce PRograms, Synaptic Package Manager and of course the command line to install them.

Jim

---

### Post by Syndacate on 2008-08-26
> **cariboo907 said:**
> You can give gftp or filezilla a try, both are available in the repositories, You can use Add/Remoce PRograms, Synaptic Package Manager and of course the command line to install them.

Jim

Thank you, gftp was exactly what I was looking for, just a "3rd party" FTP program other than nautilus.  It seems nautilus suffers the same problems as windows' explorer in terms of FTP use, sometimes it just utterly fails.

It's only happened with one IP for me, but it kept happening, and that's enough for me to not be able to trust it as much and need a back up.

Thanks!

---

