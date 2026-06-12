---
title: "[SOLVED] win xp cannot access linux box"
date: 2008-11-25
forum: General Help
---

### Post by hubiedo on 2008-11-25
i can see the linux box with my xp or win2k. i get access denied. it asks for a user and password. when entered it gives me the access denied. linux and win are on same group. is there a network password. 

any help is appreciated

---

### Post by HermanAB on 2008-11-25
This may help:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by andrew.mckevitt on 2008-11-25
Samba uses different usernames and passwords from ubuntu and are set up seperately. If you want simple access to your ubuntu files without password control, try modifying the share, right-click on the file/folder, tick 'sharing option' and  select 'allow other people to write to this folder' and tick 'Guest access (for people without a user account)'.

This is ok for simple sharing across a private home network, but not if you visit places with free wifi. You'd have to remember to disable sharing when in these places.

---

### Post by hubiedo on 2008-11-28
thanks u guys and gals. i have resolved the issue using a linux samba tutorial at linux planet and following the setup procedures there. i will use the debug info to help set up samba with firestarter etc. which is my next project.

i went thru the entire step by step to set up my samba w/ dns assignment etc. and it worked. 

the firestarter does not play well with samba but that is a separate issue i will post if any problems.

---

