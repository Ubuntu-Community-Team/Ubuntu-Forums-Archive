---
title: "why no kernel headers for 2.6.8 in repository?"
date: 2004-10-16
forum: General Help
---

### Post by wayover13 on 2004-10-16
This looks like a real oversight to me.  I put universe in my repository list right away.  Now, I need to compile my vmware.  But it needs headers for the running kernel - 2.6.8-1-i386.  They're not in the repository.  How the heck'm I supposed to compile my vmware stuff?  Stick a standard Debian unstable source in my sources.list?

---

### Post by oddabe19 on 2004-10-16
They're in Universal, uncomment those repos.... you can't do a apt-get install kernel-headers-$(uname-r) I actually had to open synaptic and search for them myself... and i found them.

---

### Post by wayover13 on 2004-10-16
Look, I've been using Debian full time for over a year now.  I know how to use apt from the command line, and Synaptic.  Like I said, I added universe to apt sources right away.  I've done the customary update/reload several times.  I looked through all kernel header packages listed: they're not for the running kernel - 2.6.8.  They have headers for 2.6.7, 2.6.6, 2.6.5 and 2.4.25.  But there are NO kernel headers for 2.6.8.  My Ubuntu is running the 2.6.8 kernel, and those are the headers I need to get my vmware modules to compile.  Leaving them out of the repository is a big oversight on the maintainers' part.  Does anyone here have access to them to let them know about this?  I can't be the only one wanting to compile stuff that needs kernel headers.  Or are you folks all compiling your own kernels from source?

---

### Post by Rancoras on 2004-10-16
Actually they're named linux-headers-`uname -r`

---

### Post by wayover13 on 2004-10-17
[quote=Rancoras]Actually they're named linux-headers-`uname -r`[/quote]

Know what?  U happen to be . . . right!  Now, why didn't I think of searching under 2.6.8.1?  But nooooooooo.  I had to make like Mr. Knowitall . . .

Thanks

---

### Post by port7 on 2004-10-22
hmm, i am still having problems here.

a `uname -r` on mine gives me 2.6.8.1-2-386 of which there are no kernel headers in the repositries.

anyone shine a light on this for me?

ta

other than that ubuntu rocks

---

