---
title: "fetchyahoo and gmail smtp server."
date: 2008-08-15
forum: General Help
---

### Post by c0rrupt on 2008-08-15
I want to use fetchyahoo to forward some mail messages from my old Yahoo account to my Gmail account.  Fetchyahoo supports forwarding messages with an SMTP server, but the only problem is that Gmail uses SSL on their servers. Does anyone know a way around this, or if fetchyahoo supports ssl SMTP servers?

Here is the code from my fetchyahoorc config file.

```

###### mail forwarding configuration ######
# set use-forward to 1 to enable mail forwarding
use-forward = 1

# set mail-host to your smtp outgoing mail server
mail-host = smtp.gmail.com:587

# the e-mail addresses you want mail forwarded to
send-to = MYEMAIL@gmail.com

# the e-mail address used as the from address, this should probably be at the
# same ISP as the outgoing smtp mailhost specified above
send-from = MYEMAIL@gmail.com

```

---

### Post by blissfulpenguin on 2009-06-16
i'm not really sure of the details, but something tells me that you could probably set up a sendmail server of some kind on your local machine.  i think all you would have to do is have fetchyahoo put it in a mailbox setup specifically for this purpose, from which your sendmail server with smtp and ssl support could then forward to gmail.

if anyone would like to elaborate on how this works, please do so. :)

---

