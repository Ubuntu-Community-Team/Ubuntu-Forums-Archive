---
title: "Problems w/ ssh"
date: 2008-08-19
forum: General Help
---

### Post by sr_guy on 2008-08-19
I have a asterisk box setup to run all my voip. I can ssh into that box from every PC in my house but my ubuntu box. Is there anything I can check that may cause this?

---

### Post by HalPomeranz on 2008-08-19
The first step would be to try logging into the Asterisk server from the Ubuntu box using "ssh -v ..." to get some debugging output.

---

### Post by elmoosecapitan on 2008-08-19
This has been a solution for people before:

If the user name on your computer is different from the user name on the server than ```
ssh -l username node.host.domain
```


cheers



Does scp work?

---

