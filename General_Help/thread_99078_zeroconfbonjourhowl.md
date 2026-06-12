---
title: "zeroconf/bonjour/howl"
date: 2005-12-04
forum: General Help
---

### Post by burnhamd on 2005-12-04
Hey all is there anyway to network my windows and ubuntu computer together.  After 16 grueling hours with samba I dont really want that.  Is there a way to set up zeroconf on all my computers and sharing printers and files.  Or is there another way to do this.  I really want someone to walk into my house with a laptop and be able to print without being added to the workgroup.

Thanks in advance

---

### Post by ltmon on 2005-12-04
Zeroconf, Bonjour, Howl etc. are not network protocols, they are network service discovery programs/protocols.  They add nothing except an easier way to find services when you don't know the IP or hostname.  Both the host and the client need to support the right protocol.

In general terms they aren't going to add a whole lot to Samba, and they are in an experimental state on Linux anyway.

L.

---

### Post by burnhamd on 2005-12-05
I dont want to use these services as a replacement to samba just as a way of automatically finding printers and music and other computers.  Just a way to see them.
Does anyone know of an easy way to accomplish this.
Printing is what I really want.

---

