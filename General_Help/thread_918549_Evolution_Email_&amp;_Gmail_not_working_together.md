---
title: "Evolution Email &amp; Gmail not working together"
date: 2008-09-13
forum: General Help
---

### Post by Pharohs on 2008-09-13
I have done everything except Voodoo, in trying to get Evolution email to send/receive my Gmail.  there are many "step-by-step" articles, and I have tried several, but no luck.  I'm convinced that the Evolution team's Welcome message is a fake.

Any assistance is welcomed.

---

### Post by eentonig on 2008-09-13
- Launch Evolution
- Edit\Preferences
- Add or Edit an account
- Tab Receiving mail: 
--> Server Type: Imap
--> server : imap.gmail.com:993
--> <username>@<google domain>
--> <SSL Encryption>
--> Authentication <Password>

- Tab Sending mail;
--> Server Type: <Smtp>
--> smtp.gmail.com:587
--> TLS Encryption
--> Auth. Type <login>

Gmail site:
- follow the Link 'Preferences' (I guess, I get a dutch translated page).
- Open tab 'forwarding and POP/IMAP' (Again, translation might be a bit off)
- enable IMAP access.
- Save change

Try to download your mail, type your gmail password when asked and click save (or not).

---

### Post by jualin on 2008-09-13
> **eentonig said:**
> -

Gmail site:
- follow the Link 'Preferences' (I guess, I get a dutch translated page).
- Open tab 'forwarding and POP/IMAP' (Again, translation might be a bit off)
- enable IMAP access.
- Save change

Try to download your mail, type your gmail password when asked and click save (or not).

The first step is actually "Settings" but is pretty much the same as preferences. If IMAP doesn't work you can try using POP by performing the same steps. Good luck!

---

### Post by jualin on 2008-09-13
I found [this website which shows you pictures of what you should do.]("https://mail.google.com/support/bin/answer.py?hl=en&answer=13273")

---

### Post by Pharohs on 2008-09-13
I downloaded Mozilla's Thunderbird and found the simple command line instructions for a picture perfect installation.  It went, smooth as silk.  Thunderbird is set up to automatically set up Gmail, if you select it.

Thanks for the responses!

---

### Post by airtonix on 2008-09-28
Still does not work.

edit : silly me i missed a full stop within my username.

---

### Post by Cool Surfer on 2008-09-28
Its good it worked, but I think it was a port problem or some pwd thingy.
Gmail is working fine in both thunderbird and evolution.:guitar:

---

