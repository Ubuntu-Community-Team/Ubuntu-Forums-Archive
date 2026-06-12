---
title: "[SOLVED] Error message when I check for updates"
date: 2008-11-19
forum: General Help
---

### Post by gilloz on 2008-11-19
When I check for updates with the Update Manager, I always get the message below.  How do I corect this error?


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Elfy on 2008-11-19
Try running this```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by prshah on 2008-11-19
> **forestpixie said:**
> Try running this```
[color=red]sudo apt-get update &&[/color] sudo apt-get install medibuntu-keyring && sudo apt-get update
```

I believe you need to drop the first "..apt-get update.." because it will fail, and then the rest of the commands will never be executed (because of '&&').

---

### Post by Elfy on 2008-11-19
That's what I've thought as well tbh - but it's from the site and always works for me when I first get the sources - it does throw an error - and of course I forgot to take it off here :)

---

### Post by gilloz on 2008-11-19
Thanks guys.  That did the trick. Oh, and I did remove that 1st part before trying it out.  Thanks again.

---

