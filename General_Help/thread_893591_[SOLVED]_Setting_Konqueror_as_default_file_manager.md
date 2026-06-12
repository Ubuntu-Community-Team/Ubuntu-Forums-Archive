---
title: "[SOLVED] Setting Konqueror as default file manager instead of dolphin"
date: 2008-08-18
forum: General Help
---

### Post by peterjakey on 2008-08-18
Can I set Konqueror as default file manager instead of dolphin?

---

### Post by mc4man on 2008-08-18
you could try this way
In konsole run ```
kcontrol
``` expand KDE Components -> File Associations -> expand Inode -> Directory
Then move Konqueror above Dolphin in the Application preference order, apply

---

### Post by peterjakey on 2008-08-18
> **mc4man said:**
> you could try this way
In konsole run ```
kcontrol
``` expand KDE Components -> File Associations -> expand Inode -> Directory
Then move Konqueror above Dolphin in the Application preference order, apply

that worked thanks!

---

### Post by tikey on 2008-09-02
I accidentaly deleted the konqueror entry for inode/directory. Could someone give me the exact command that I have to put here?
And which services have to be in the Service Preference Order?

Thanks

---

### Post by sirHC88 on 2008-11-10
> **mc4man said:**
> you could try this way
In konsole run ```
kcontrol
``` expand KDE Components -> File Associations -> expand Inode -> Directory
Then move Konqueror above Dolphin in the Application preference order, apply

Thank you, also worked for me in Intrepid. I already searched quite long for that.

---

### Post by DMerriman on 2008-12-08
Feh. This doesn't work in 8.10 -- kcontrol isn't even in the repositories any more, according to both Adept and Synaptic.

Me, I don't *like* Dolphin, and want my fast, simple, easy-to-use Konqueror file management back!

I really wish the folks at Ubuntu could/would get their act together: when I updated from 8.04>>8.1, I lost networking (finally had to remove the fscking KNetworkManager and **manually** set DNS!), and have had a host of other problems -- never mind the little details that they let slip through.

With 8.04 installations wanting to immediately upgrade to 8.10 (and the attendant problems it has), I've quit giving people Kubuntu live CDs to try Linux with, and gone to Fedora and SuSe -- and I'm on the ragged edge of switching over myself: this "we're gonna change stuff 'cause we know better than you" business is getting REAL old!

---

