---
title: "Evolution-exchange Question"
date: 2008-07-11
forum: General Help
---

### Post by ZelmoB on 2008-07-11
I am trying to configure the evolution-exchange connector to work with my companies Exchange 2003 server.

I am running Release 8.04 with Evolution and evolution-exchange version 2.22.3.1-0Ubuntu1.

I've successfully connected to the OWA server with Firefox and Explorer.

When I attempt to configure an exchange account in Evolution, I get as far as the "Receiving Email" dialog.  I select "Microsoft Exchange" as the server type, Enter the same username I use with a browser, enter the URL I use with a browser and click authenticate.

As soon as I click on authenticate, the debug log displays:

e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have key 'exchange:__mbeatty;auth_Basic@webmail.freedommortgage.com_'

I enter my password and get a popup saying: Could not authenticate to server.

At this point the debug log also displays:

(evolution:17019): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)

Am I having a problem with the Keyring manager?  The "Could Not Authenticate" dialog comes up so quickly that it's hard to believe the connector is actually trying to connect to the server.

Any ideas what I could try?

---

