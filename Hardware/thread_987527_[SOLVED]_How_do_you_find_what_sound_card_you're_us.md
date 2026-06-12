---
title: "[SOLVED] How do you find what sound card you're using?"
date: 2008-11-19
forum: Hardware
---

### Post by Shardsofmetal on 2008-11-19
I know there's a command to find the module name of the sound card you're using. The OSS HOWTO used to have that command, and linked to a compatibility list, which told what sound cards OSS supported. However, now that the documentation has been moved to community docs, the post has been edited to point users to the new documentation, which does not include that command. Thanks

---

### Post by NoWayBill on 2008-11-19
lspci

That will tell you the manufacturer and chipset.

---

### Post by Shardsofmetal on 2008-11-19
Thank you. Now how do u have it return just the sound part. I remember that the command the tutorial had you run was "lspci | grep ???", only the question marks were replaced with something else. Does anybody know what that was? Thanks

---

### Post by Stompzi on 2008-11-19
`lspci | grep audio` will work.

---

### Post by Shardsofmetal on 2008-11-19
Thank you. The command, as I now remember, and it seems to work, is ```
lspci | grep -i audio
```
I needed the -i because otherwise it needed to Audio, but this way seems like it would be more compatible, in case some systems say "audio" instead.

---

