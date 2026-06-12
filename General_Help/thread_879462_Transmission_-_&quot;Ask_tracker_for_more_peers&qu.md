---
title: "Transmission - &quot;Ask tracker for more peers&quot;"
date: 2008-08-04
forum: General Help
---

### Post by chinnaraaju on 2008-08-04
Hi,

i am using transmission torrent client in my ubuntu.
Recently , i found an option 'Ask tracker for more peers'..i wondered what might be exact use of this option..

pls clarify me the use of this option..whether its safe...explain me in download & upload context..

Regards,
Chinna.

---

### Post by jasex on 2008-08-04
From my understanding it requests to open more connections with peers for the torrent, from the tracker's listing of peers.

My experience, is that if you're downloading from 12 peers and 32 seeders, but you know that the file has 300 peers and 700 seeders (example numbers)
then it sends a refresh, to connect to more peers  that may have just become active

I also believe the client performs this at an automatic interval (modifiable by source?)

---

### Post by estyles on 2008-08-08
yeah, it doesn't seem to do much.  If there are more peers, then Transmission will use them, and if it doesn't have any peers, clicking the button won't find any.  I'm sure it will refresh the list of peers, but I feel like it's more of a "click...hum..." button.  Kinda like jamming the elevator button to make it come faster.

---

