---
title: "&quot;Could not load default font 'fixed'&quot; - Thinkpad X31"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by be_placid on 2006-06-20
Hello,

I recently obtained an IBM Thinkpad X31 with the following specs:
[LIST]
[*]1.4GHz Intel Proc.
[*]1GB RAM
[*]16MB ATI Radeon Mobility
[*]60GB HDD
[/LIST]

I had an old breezy disc that I installed onto the laptop (complete HDD format) and once it was working, I decided to upgrade to Dapper. I did so by replacing 'breezy' with 'dapper' in /etc/apt/sources.list and ran a `sudo apt-get dist-ugprade`. After various restarts due to the laptop overheating (another issue) I managed to get it installed. However, X would not start and the errors returned were:
[LIST]
[*]Could not map font path 'unix/:7100' (from memory, might be wrong text/values)
[*]Could not load default font 'fixed' (100% right)
[/LIST]
Googling the second error returned plenty of results, of which I have tried isntalling XFS and making sure its running before starting GDM (manually stoping GDM and by moving the GDM init script /etc/rc5.d/S10GDM after the XFM script). I have also tried symlinking /usr/X11R6/lib/X11/fonts in /usr/share/X11/fonts but this hasn't worked either.
I am beginning to believe its a pathing problem (similar to issues with the NVIDIA module needing a symlink due to Xorg path changes), but at the moment i'm rather stuck.

Can anyone assist me?

Thanks in advance,


Alex

---

### Post by be_placid on 2006-08-30
FYI, anyone who has this problem should make sure they have the 'apm' .deb installed. This fixed it for me.

Hope that helps,
Placid

---

