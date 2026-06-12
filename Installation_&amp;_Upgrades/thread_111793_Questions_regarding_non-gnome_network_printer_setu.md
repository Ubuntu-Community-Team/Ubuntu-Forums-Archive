---
title: "Questions regarding non-gnome network printer setup"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by kenfar on 2006-01-02
_First a little backstory:_

On my desktop I've managed to get wireless, dual video cards, an intel 810E video chipset, iptables, and samba going fine - with seemingly little more documentation than collected snippets of advise & wisdom from these forums.  But - that just isn't cutting it for network printing.

I'm running a very vanilla ubuntu server configuration - no gnome (crashed continually) along with a couple of ubuntu clients.   Everything is 5.10.  None of the gnome printer set up stuff works on the server, and of course neither does the cups admin page for configuration.

I've installed hpoj & hplip.  Followed directions from this page and my cupsd.conf is directly copied from it:
   [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)
Also ran this command from the cups documentation:
   kenfar@badger:~$ sudo lpadmin -p printer -E -v parallel:/dev/lp1 -m laserjet.ppd

Now I can actually see the printer (queue? class?) via the cups admin site (overrode RunAsUser).
[U]
Now the questions:[/U]

1.   I can print a test page, tho nothing actually prints.  CUPS admin page says "Printer not connected; will retry in 30 seconds".  What would be the recommended next step in diagnosis?  Note: iptables not yet configured.

2.  Am I missing something here?  Need hp firmware?  Need to somehow map that printer to a device driver (besides laserjet.ppd)?  Need to turn something else on?

3.  any pointers to recommended documentation for network printing, cups & samba?  I know there is separate documentation for both samba & cups, but something that pulled it all into a ubuntu solution would be extremely helpful.  And ideally something that steps back and describes all the pieces rather than just a few specific commands that generally don't seem to work...


Thanks from a worn out new user that is honestly trying to remove his windows boxes!

Ken

---

