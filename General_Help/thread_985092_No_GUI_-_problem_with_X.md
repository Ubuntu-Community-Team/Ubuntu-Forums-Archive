---
title: "No GUI - problem with X?"
date: 2008-11-17
forum: General Help
---

### Post by kilps on 2008-11-17
Hi all

Not entirely sure how I should describe the problem - hope I get it right. While not doing anything unusual (think I'd just opened GIMP) my screen suddenly switched to a black command line type interface before presenting me with the login window allowing me to log back in.

Now since I restarted my computer I'm seeing fail messages (all moves too fast to see what is says) and am not getting a graphical login screen - entering recovery mode and choosing xfix gives me an error message along the lines of "Can't locate strict.pm" - but again disappears too fast for me to get the whole thing.

I'm running 8.04 - am a bit behind on updates I think.

Can anyone help? Thanks.

---

### Post by kilps on 2008-11-17
Some updates:

I read somewhere that running 'dpkg-reconfigure xserver-xorg' might help. I tried that and got the same error message as before - which is (well it is very similar at least):

```
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-reconfigure line 8.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8.
```

So after googling that a bit it seemed that I might need to update perl - so I ran 'sudo aptitude reinstall perl' - which amongst others gave a very similar message to the above.

Can anyone help? thanks.

---

