---
title: "[SOLVED] Openoffice.org wants to save a file after printing"
date: 2008-10-02
forum: General Help
---

### Post by JoeG on 2008-10-02
Hi. Running Ubuntu 8.04 here with Openoffice.org 2.4.1 and have a slight issue. I open an existing file with Writer and print it, having made no changes to the file. Close Openoffice Writer and am asked if I wish to save the changes. I'm printing to an HP Laserjet 4100 on the network using a jetdirect card and have no issues printing. 

Anyone else having this problem, or has had this issue and knows of a fix? It's not a show-stopper, but kind of annoying. I'll be happy to provide any other information needed to narrow this down.

---

### Post by Patb on 2008-10-02
Joe, in OO Writer, go to Tools > Options and under the heading "OpenOffice.org" click the tag "General".  Unmark the box "Printing sets 'document modified' status".  

Extract from Writer's help menu:  > This setting specifies whether the printing of the document counts as a modification. When this option is marked, the very next time the document is closed you are asked if the changes should be saved. The print date is then entered in the document properties as a change.

Hope this helps. Cheers, Pat.

---

### Post by ProgramErgoSum on 2008-10-02
To add onto Pat's comments, I think, this exists for MS Office docs too. It is probably because, there is a feature in footer of a document where you can have an automatic field to hold the 'date printed' value.

---

### Post by JoeG on 2008-10-02
> **Patb said:**
> Joe, in OO Writer, go to Tools > Options and under the heading "OpenOffice.org" click the tag "General".  Unmark the box "Printing sets 'document modified' status".  

Extract from Writer's help menu:  

Hope this helps. Cheers, Pat.

That did the trick! Thanks so much, Pat. I figured it was a setting for the application that I simply hadn't found yet.  Thread marked as "Solved".

---

