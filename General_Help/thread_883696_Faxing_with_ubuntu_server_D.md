---
title: "Faxing with ubuntu server :D"
date: 2008-08-08
forum: General Help
---

### Post by baggus on 2008-08-08
Hi all,

Spent a while looking for a simple daemon of some sort that will:
[LIST]
[*]recieve faxes on com port modem
[*]print these faxes (on a cups printer)
[*]e-mail recieved faxes to a fixed e-mail adres (or just store em in a folder as long as they are stored)
[/LIST]

Maybe the ever helpfull Ubuntu community has recommendations for this?

It doesn't have to run on Linux at all, i can always virtualize it since i still have a few unused Faildows licenses lying around ;)

Lots of thanks in advance!

---

### Post by brian_p on 2008-08-08
> **baggus said:**
> Hi all,

Spent a while looking for a simple daemon of some sort that will:
[LIST]
[*]recieve faxes on com port modem
[*]print these faxes (on a cups printer)
[*]e-mail recieved faxes to a fixed e-mail adres (or just store em in a folder as long as they are stored)
[/LIST]


Have you looked at whether hylafax is capable of fulfilling some or all of your specs.

```
apt-cache search hylafax
```

---

