---
title: "Localhost 631?"
date: 2008-09-11
forum: General Help
---

### Post by 2CV67 on 2008-09-11
Hi guys!

Somewhere along the way, I found a reference to [http://localhost:631/](http://localhost:631/) & tried it.

Followed an uneasy feeling of not knowing where I was...
I thought localhost was my computer somehow (sorry to be so dumb).
But here I seem to be out in the internet somewhere...
But somewhere where they have a list of all my printers & where I (they?) can add/remove/change all my printer settings!

It all seems to be compatible with what I find under Ubuntu > System > Administration > Printers.
Changes made in one show up in the other OK, so no obvious conflict.

I now notice that the window for Administration > Printers is headed "Printer configuration - localhost"...

Can somebody please explain what is going on here (in simple language if possible)?

Should I be using localhost:631 or not?
Is it better or worse than Administration > Printers ?
Advantages & disadvantages?

Thanks!

---

### Post by amo-ej1 on 2008-09-11
Your cups installation is listening on localhost on port 631, so if you enter it in a browser you get redirected to the webbased cups configuration frontend, which will let you do similar things as the GUI. You could use that if you like it more or you could use the GUI if you like that one. Using both will not result in any conflict.

---

### Post by tgilber1 on 2008-09-11
The URL localhost:631 is the CUPS interface to view, add, or modify printers.  The "Printing" sub-menu choice under Administration is a python script that provide a Gnome front-end to CUPS.

The Gnome Printing interface simplifies set up of printers for a CUPS printing environment.  If you want more granular control over your printers, then CUPS interface may be provide the answer.


> **2CV67 said:**
> Hi guys!

Somewhere along the way, I found a reference to [http://localhost:631/](http://localhost:631/) & tried it.

Followed an uneasy feeling of not knowing where I was...
I thought localhost was my computer somehow (sorry to be so dumb).
But here I seem to be out in the internet somewhere...
But somewhere where they have a list of all my printers & where I (they?) can add/remove/change all my printer settings!

It all seems to be compatible with what I find under Ubuntu > System > Administration > Printers.
Changes made in one show up in the other OK, so no obvious conflict.

I now notice that the window for Administration > Printers is headed "Printer configuration - localhost"...

Can somebody please explain what is going on here (in simple language if possible)?

Should I be using localhost:631 or not?
Is it better or worse than Administration > Printers ?
Advantages & disadvantages?

Thanks!

---

