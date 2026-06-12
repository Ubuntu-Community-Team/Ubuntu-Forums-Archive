---
title: "Intrepid: Evolution is slow with IMAP"
date: 2008-10-31
forum: General Help
---

### Post by Kurgan_it on 2008-10-31
I have updated to 8.10 yesterday, and immeditely after updating, Evolution became painfully slow. 

I run an IMAP setup with a local (GB LAN) dovecot server. I have 4 accounts and about 80 folders, with a total of more than 150.000 emails. The older version of Evolution was really fast, it could handle this load flawlessly. 

Right after updating to Intrepid (32 bit), Evolution uses about 1 GB RAM and one CPU core at 100% about all the time. Disk is constantly in use, too.  Evolution's "tasks" (that are shown in the bottom status bar) seem to hang forever at 100% when "scanning for changed messages in folder XXX", with no network activity (so IMAP is actually doing nothing at that time) and a lot of cpu and disk use.

I suppose that the new indexing system based on sqlite (if I have understood correctly from the pop-up that was shown at the first run) is really flawed, or at least really slow compared to the old one.

If I don't find a solution quickly, I'll have to abandon Evolution. This is sad because up to 8.04 it was faster at IMAP tasks than every other mail client I have used, including  Thunderbird for windows and Linux.

---

### Post by PizzAp on 2008-11-13
After upgrading the first run takes ages, I guess that's the migration tool running.

---

### Post by Kurgan_it on 2008-11-13
It's not simply a conversion problem. The new database backend is terribly slow. 

Here is the link to the bug:

[http://bugzilla.gnome.org/show_bug.cgi?id=558883](http://bugzilla.gnome.org/show_bug.cgi?id=558883)

---

### Post by PizzAp on 2008-11-14
Yes, after using evo some more I'd have to agree, startup is very slow.
One of my folders.db is 990mb and even with ext3 datawriteback and software raid 1 evolution needs like 90 seconds until it's ready.

I'm going to apply the patches mentioned in the bug report. I need to rebuild anyways, because of the junk folder patch from [http://bugzilla.gnome.org/show_bug.cgi?id=272027](http://bugzilla.gnome.org/show_bug.cgi?id=272027).

---

### Post by Kurgan_it on 2008-11-14
If you patch Evo as suggested in the bug report, please test it and report back.

Thanks.

---

### Post by PizzAp on 2008-11-15
The proposed Patch ([http://bugzilla.gnome.org/attachment.cgi?id=121851](http://bugzilla.gnome.org/attachment.cgi?id=121851)) really speeds things up. Imho there are still some performance issues though.

Do you know if anyone filed an ubuntu bug report yet?

---

### Post by Kurgan_it on 2008-11-16
I suggest that you try also the other patch, at 

[http://bugzilla.gnome.org/attachment.cgi?id=122308&action=view](http://bugzilla.gnome.org/attachment.cgi?id=122308&action=view)

Also, could you please send me somehow the binary packages (if you have compiled them) with the patches?

You should also report yout results in the bugzilla thread at [http://bugzilla.gnome.org/show_bug.cgi?id=558883](http://bugzilla.gnome.org/show_bug.cgi?id=558883).

I have reported the bug in Ubuntu, here is the link:
[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/292739](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/292739)

---

### Post by PizzAp on 2008-11-17
Done.

---

### Post by PizzAp on 2008-11-19
Does anyone have these problems without ext3? I guess it's all because of the sqlite ext3 bug.

---

