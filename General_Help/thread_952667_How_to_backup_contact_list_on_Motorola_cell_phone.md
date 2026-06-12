---
title: "How to backup contact list on Motorola cell phone"
date: 2008-10-19
forum: General Help
---

### Post by pytheas22 on 2008-10-19
I'm using moto4lin to connect to my w385 Motorola cell phone.  The connection works well and I can download files without a problem (thanks to the tips in [this thread]("http://ubuntuforums.org/showthread.php?t=638509")).

My only trouble is that I want to backup my phone's contact list, but I can't figure out which file that is.  I've looked around the file system but nothing looks like it's the file I'm looking for.  I've tried googling around as well but still can't figure it out.  I guess I could figure it out by modifying my contact list and seeing which files change in size, but that would take a long time, so I'm hoping that someone familiar with Motorola's file system can point me in the right direction.

If anyone has any idea which file I need to copy over to backup the list, it would be very helpful.  Thanks in advance.

---

### Post by NilsE on 2008-10-19
If it is a Moto CDMA phone you can use bitpim which does all of this for you and still lets you browse the file system.

The one in the repositories is pretty old so I would get the latest .deb file from [www.bitpim.org](www.bitpim.org) and install it

---

### Post by pytheas22 on 2008-10-19
Thanks for the reply.  I couldn't get bitpim to do any more than list the directories on my phone, but I also was only using the version in the repositories, since they don't have a 64-bit .deb on their website and I don't have time to figure out how to make the 32-bit installer work now.  Maybe I'll try pulling the .deb from the Intrepid repositories, which should be more recent.  Either way, bitpim seems to be smoother and have a nicer interface than moto4lin, so I'm glad to learn about it.

Still if anyone knows exactly which file I need to copy in order to backup my contact list, I'd be grateful.

---

### Post by NilsE on 2008-10-20
> **pytheas22 said:**
> 

Still if anyone knows exactly which file I need to copy in order to backup my contact list, I'd be grateful.
The reason I suggested Bitpim is it does thebackup automatically for you.  Just click on the top left icon and select phonebook in the selection.

---

### Post by pytheas22 on 2008-10-20
> The reason I suggested Bitpim is it does thebackup automatically for you. Just click on the top left icon and select phonebook in the selection.

I know and thanks again for letting me know about bitpim, but unfortunately I don't think my phone is really supported--it just detects it as an 'other' device--and it can't do any more than read the file system.  When I click the button for the phonebook, nothing happens, and it says that my contact list is empty.

---

### Post by NilsE on 2008-10-20
A few people have reported luck with reading the phonebook with bitpim setting the phone to either V3M or V3C.  There is a bunch of stuff in this thread at Howard Forums for the W385.

[http://www.howardforums.com/showthread.php?t=1227948](http://www.howardforums.com/showthread.php?t=1227948)

---

