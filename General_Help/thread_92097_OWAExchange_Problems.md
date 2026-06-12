---
title: "OWA/Exchange Problems"
date: 2005-11-18
forum: General Help
---

### Post by Saxis on 2005-11-18
Having problems getting anything to work with OWA and Exchange 2003.  I cannot log into OWA via Firefox, and also Evolution will not Authenticate.  I set up and manage the OWA/Exchange myself, and it has always worked fine in IE and Windows.    I get different error messages in Evolution depending on the username I enter. With just "username", it says that it may need me to supply the domain also, so I enter "DOMAIN\username" and it just says "Make sure username and password are correct...."

Firefox just keeps asking for my username and password in a continuous loop. Even after hitting "Cancel", it asks again.  After the second "Cancel", the OWA windows come up with "Access denied".

On the OWA server I have Anonymous Access disabled, and it is set to use plain text passwords over SSL.

Any ideas?

---

### Post by Saxis on 2005-11-18
Figured it out, of course only after I posted...

---

### Post by N6546R on 2005-11-19
What was the problem?

Perry

---

### Post by Saxis on 2005-11-21
Turns out I really didn't have Plain Text passwords over SSL enabled.  SSL was enabled, but it was using Digest for AD accounts.  Works fine with any Windows/IE client, but Evolution and Firefox didn't like it.

---

