---
title: "firefox address bar issue"
date: 2008-07-25
forum: General Help
---

### Post by terrordrone on 2008-07-25
I have FF 3 installed

there is a strange error

the address bar does not display any url unless i punch it in. 

but, if i run it as sudo firefox, it runs normally as it should

if i just run it as firefox, the address bar doesnt display any url

any idea why? :confused:

---

### Post by ajmorris on 2008-07-25
hi there,
This is probably because of your specific user's config settings. You can either create a new firefox profile, or just navigate to ~/.mozilla/firefox then move the profile directory in there (or just delete it if you dont want it) then restart firefox with the new profile that will automagically be created when you move/delete your current profile, then see if it works. if it works, you can then procede to transfer over bookmarks etc from your old profile. A handy firefox plugin for bookmarks is foxmarks ;)

AJ

---

### Post by terrordrone on 2008-07-25
> **ajmorris said:**
> hi there,
This is probably because of your specific user's config settings. You can either create a new firefox profile, or just navigate to ~/.mozilla/firefox then move the profile directory in there (or just delete it if you dont want it) then restart firefox with the new profile that will automagically be created when you move/delete your current profile, then see if it works. if it works, you can then procede to transfer over bookmarks etc from your old profile. A handy firefox plugin for bookmarks is foxmarks ;)

AJ
thanks a lot m8

it worked :D

---

