---
title: "Help! Microtek ScanMaker3840"
date: 2008-05-07
forum: Hardware
---

### Post by shirokurokun on 2008-05-07
Hello

I'm a newbie to Ubuntu. I just migrated to Xubuntu hardy a few days ago. I'm experiencing some problems regarding software and hardware, but thanks to this forums I found some workarounds just by peeking on some threads.

This is the only(probably) problem that I have right now. I can't get my scanmaker to work. I did a few things and I think I screwed sane. Before, I can find my scanner by using the sane-find-scanner command, [COLOR="Red"]cannot open scanner access to resource is denied[/COLOR] is my only problem, But now I can't even find my scanner using this command.

I think what I did is just follow the instructions [_[COLOR="Blue"]here[/COLOR]_]("http://www.ziplabel.com/sm3840/")
I just downloaded sane-backends-1.0.15, extract and follow the instructions there. I think it installed sane-backends-1.0.15 and ruined the sane-back-ends that is bundled with my Xubuntu.

Is there anyway to undo these changes? I think I saw the solution to this problem somewhere in this forums regarding the access denied error, but it won't work if sane can't detect my scanner. Please help me! I don't want to reformat the pc just because of this.

Thanks!
(Pls excuse my English, it's not my native language.)

---

### Post by alienexplorers on 2008-05-11
All you needed was the libsane-sm3840.so.1.0.15 backend driver and not the entire sane 1.0.15 package.  Querry Google and search for libsane-sm3840.so.1.0.15.....

---

### Post by shirokurokun on 2008-05-23
Where should I put libsane-sm3840.so.1.0.15?

---

