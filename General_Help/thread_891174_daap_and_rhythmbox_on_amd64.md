---
title: "daap and rhythmbox on amd64"
date: 2008-08-15
forum: General Help
---

### Post by romeyde on 2008-08-15
When I try and start rhythmbox on my amd64 box using the DAAP plugin I get a pop up that says: Unable to activate plugin DAAP Music Sharing.   If I start rhythmbox from the command line, I see this: /home/xxxxxx/.gnome2/rhythmbox/plugins/daap/libdaap.so: wrong ELF class: ELFCLASS32.

I'm trying to get simplify media to work with rhythmbox.   I'm guessing I'm having issues because the plug in that came with simplify media was compiled for 32 bit?

----------

I was able to get it working without an error by renaming the libdaap.so that simplify media installed and then linking to the one that comes with rhythmbox but by doing this, rhythmbox doesn't seem to work with simplify media and the only way to connect to a daap server is to type in the Host:Port info of the daap share.  I believe I'm supposed to be able to just see/browse my friends shares.

---

### Post by NeilMonday on 2008-08-18
I am having the exact same problem. I had an idea to replace simplifymedia's libdaap.so with my own by compiling libdaap from source on my 64 ubuntu. It did not work however. I'll send a message to the folks over at simplifymedia.

---

### Post by kapstaad on 2008-08-21
"Me Too" :(

Intel Xeon, Hardy, latest RB and SM.  I have IA32libs installed (for various reasons, including the recommendation in Simplify Media's FAQ).

Hope there's an answer soon!

---

### Post by NeilMonday on 2008-09-09
Just received this from SimplifyMedia:

> Hi Neil,
Sorry for the delay. I'm sending you a 64 bit rhythmbox plugin.
Just copy it in ~/.gnome2/rhythmbox/plugins/daap

Thank you,
Yavor

I have attached the file here. Haven't tested it yet, but I will later today.

---

### Post by NeilMonday on 2008-09-10
Tested and it works! Follow installation as normal and then just drag the .so file in the specified folder. Make sure to give simplify media and rhythmbox a restart just in case.

---

### Post by The_Phil on 2008-09-24
ok, so when I try to replace libdaap.so I get "permission denied". I'm a newbie here, any help on how to get rid of the original file so I can replace it?

---

### Post by technot on 2009-09-19
the attatched plugin does not work on ubuntu karmic(9.10), on AMD64.

getting the same message as with the original from simpplify's download page :\

---

### Post by lkilcher on 2009-11-17
I am having the same issue after upgrading from Ubuntu 9.04 to 9.10 (on a ia64 box).  simplifymedia no longer works.  i.e. If you're thinking of upgrading to 9.10, and you use simplifymedia, WAIT A FEW MONTHS(?)
Is anyone else currently having this problem?  Has anyone found a fix/workaround?

I sent simplifymedia a request (three days ago) for a version of libdaap.so for 9.10, but haven't heard back yet.
How hard can it be for them to recompile their src on a 9.10 machine?  And wouldn't it be nice if they added playlist sharing for ubuntu?

Oh well, for now I'm stuck without being able to stream my music, which wouldn't be such a big deal except that I JUST centralized everything for use with simplify media.  ... One of these days I'll learn to NOT update my distribution until >2 months after its release (it's just so temptingly easy now-of-days).
...
On a related note, are there any open projects trying to do the same thing that simplifymedia does?

---

### Post by Pork Chop on 2010-01-19
i'm still having this problem, albeit on a non-x64 system.

---

